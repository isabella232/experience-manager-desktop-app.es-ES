---
title: Solución de problemas de AEM versión 1.x de la aplicación de escritorio
description: Solucione los problemas de AEM aplicación de escritorio versión 1.x para resolver los problemas ocasionales relacionados con la instalación, actualización, configuración, etc.
uuid: ce98a3e7-5454-41be-aaaa-4252b3e0f8dd
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.5/ASSETS, SG_EXPERIENCEMANAGER/6.4/ASSETS, SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f5eb222a-6cdf-4ae3-9cf2-755c873f397c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1702ef74ad0497b25c2fc349a2950e4e2b19a90b
workflow-type: tm+mt
source-wordcount: '3379'
ht-degree: 1%

---


# Solución de problemas de AEM aplicación de escritorio v1.x {#troubleshoot-aem-desktop-app}

Solucione problemas de AEM aplicación de escritorio para resolver los problemas ocasionales relacionados con la instalación, actualización, configuración, etc.

La aplicación de escritorio de Adobe Experience Manager (AEM) incluye utilidades que le ayudan a asignar el repositorio de AEM Assets como recurso compartido de red en el escritorio (recurso compartido SMB en Mac OS). El uso compartido de redes es una tecnología de sistema operativo que permite que las fuentes remotas sean tratadas como si formaran parte del sistema de archivos local de un equipo. En el caso de la aplicación de escritorio, la estructura de repositorio de la administración de recursos digitales (DAM) de una instancia de AEM remota se define como el origen de archivos remoto. El diagrama siguiente describe la topología de la aplicación de escritorio:

![diagrama de aplicaciones de escritorio](assets/aem-desktopapp-architecture.png)

Con esta arquitectura, la aplicación de escritorio intercepta las llamadas al sistema de archivos (abrir, cerrar, leer, escribir, etc.) al recurso compartido de red montado y las convierte en llamadas HTTP nativas AEM al servidor AEM. Los archivos se almacenan en caché localmente. Para obtener más información, consulte [Uso de AEM aplicación de escritorio v1.x](use-app-v1.md).

## Descripción general del componente de la aplicación de escritorio de AEM {#desktop-app-component-overview}

la aplicación de escritorio incluye los siguientes componentes:

* **La aplicación** de escritorio: La aplicación monta o desmonta DAM como un sistema de archivos remoto y traduce las llamadas del sistema de archivos entre el recurso compartido de red montado localmente y la instancia de AEM remota a la que se conecta.
* **Sistema operativo cliente** WebDAV/SMB: Gestiona la comunicación entre el Explorador/Finder de Windows y la aplicación de escritorio. Si se recupera, crea, modifica, elimina, mueve o copia un archivo, el cliente WebDAV/SMB del sistema operativo (SO) comunica esta operación a la aplicación de escritorio. Tras recibir la comunicación, la aplicación de escritorio la convierte en llamadas de API nativas AEM remotas. Por ejemplo, si un usuario crea un archivo en el directorio montado, el cliente WebDAV/SMB inicia una solicitud, que la aplicación de escritorio convierte en una solicitud HTTP que crea el archivo en DAM. El cliente WebDAV/SMB es un componente integrado del sistema operativo. No está afiliado de ninguna manera con la aplicación de escritorio, AEM o Adobe.
* **Instancia** de Adobe Experience Manager: Proporciona acceso a los recursos almacenados en el repositorio de AEM Assets DAM. Además, realiza las acciones solicitadas por la aplicación de escritorio en nombre de las aplicaciones de escritorio locales que interactúan con el recurso compartido de red montado. La instancia de destinatario AEM debe ejecutar AEM versión 6.1 o superior. AEM instancias que ejecutan versiones anteriores de AEM podrían requerir paquetes de funciones adicionales y correcciones rápidas instalados para ser totalmente funcionales.

## Casos de uso previstos para AEM aplicación de escritorio {#intended-use-cases-for-aem-desktop-app}

AEM aplicación de escritorio utiliza la tecnología de uso compartido de la red para asignar un repositorio AEM remoto a un escritorio local. Sin embargo, no se pretende sustituir a un recurso compartido de red que tenga activos, donde los usuarios realizan operaciones de gestión de activos digitales directamente desde su escritorio local. Estos incluyen mover o copiar varios archivos, o arrastrar estructuras de carpetas grandes al recurso compartido de red de AEM Assets directamente en Finder/Explorer.

AEM aplicación de escritorio proporciona una forma práctica de acceder (abrir) y editar (guardar) recursos DAM entre la IU AEM Assets Touch y el escritorio local. Vincula los recursos del servidor de AEM Assets con los flujos de trabajo basados en escritorio.

El siguiente ejemplo de caso de uso ilustra cómo se debe utilizar AEM Desktop:

* Un usuario inicia sesión en AEM y utiliza la interfaz de usuario web para localizar un recurso.
* Con las funciones de acción de escritorio de la interfaz de usuario web AEM, el usuario abre, muestra o edita el recurso en el escritorio según sea necesario.
* AEM Desktop abre el recurso en el editor predeterminado para el tipo de archivo del recurso.
* El usuario realiza los cambios deseados en el recurso.
* Una vez modificado un archivo, el usuario puede realizar la vista del estado de sincronización del archivo mediante la ventana de estado de sincronización en segundo plano de AEM Desktop.
* Con el menú contextual de AEM escritorio, el usuario inicia o cierra la compra del recurso o regresa a la interfaz de usuario de DAM.
* Tras completar los cambios realizados en el archivo, el usuario vuelve a la interfaz de usuario web AEM

Este no es el único caso de uso. Sin embargo, ilustra cómo AEM Desktop es un mecanismo práctico para acceder a los recursos y editarlos localmente. Se le recomienda utilizar la interfaz de usuario web DAM tanto como sea posible, ya que ofrece una mejor experiencia. Proporciona al Adobe más flexibilidad para cumplir con los requerimientos del cliente.

## Restricciones     {#limitations}

El recurso compartido de red WebDAV/SMB1 proporciona la comodidad de trabajar con archivos en una ventana del Explorador/Finder. Sin embargo, Explorer/Finder y AEM se comunican a través de una conexión de red que tiene ciertas limitaciones. Por ejemplo, el tiempo que se tarda en copiar un archivo de 1 GB en el directorio WebDAV/SMB montado es aproximadamente el mismo que el tiempo necesario para cargar un archivo de 1 GB en un sitio Web mediante un explorador Web. De hecho, en el primer caso, la duración puede ser mayor debido a las ineficiencias del protocolo WebDAV/SMB y de los clientes WebDAV/SMB del sistema operativo (particularmente Mac OS X).

Existen limitaciones a los tipos de tareas que se pueden realizar desde un directorio montado. En general, trabajar con archivos de gran tamaño, especialmente con una conexión de red de baja latencia, alta o baja anchura de banda, puede resultar complicado, especialmente al editar archivos de gran tamaño.

Adobe recomienda que realice algunas pruebas de casos de uso antes de confirmar a un cliente que ciertos tipos de archivos se pueden editar de forma eficaz desde el directorio montado.

AEM Desktop no es adecuado para realizar una manipulación intensiva del sistema de archivos, que incluye, entre otras cosas:

* Mover o copiar archivos y directorios
* Añadir muchos recursos para AEM
* Búsqueda y apertura de archivos a través del sistema de archivos, excepto para explorar carpetas
* Compresión o descompresión de archivos

Debido a las limitaciones del sistema operativo, Windows tiene una limitación de tamaño de archivo de 4.294.967.295 bytes (aproximadamente 4,29 GB). Se debe a una configuración del Registro que define el tamaño que puede tener un archivo en un recurso compartido de red. El valor de la configuración del Registro es un DWORD con un tamaño máximo igual al número al que se hace referencia.

La aplicación de escritorio Experience Manager no tiene un valor de tiempo de espera configurable que desconecte la conexión entre el servidor Experience Manager y la aplicación de escritorio después de un intervalo de tiempo fijo. Cuando se cargan recursos de gran tamaño, si la conexión se agota después de un tiempo, la aplicación tiene el reintentos de cargar el recurso varias veces aumentando el tiempo de espera de carga. No se recomienda cambiar la configuración de tiempo de espera predeterminada.

## Almacenamiento en caché y comunicación con AEM {#caching-and-communication-with-aem}

AEM aplicación de escritorio ofrece funciones internas de almacenamiento en caché y carga en segundo plano para mejorar la experiencia del usuario final. Cuando guarda un archivo grande, se guarda primero localmente para que pueda continuar trabajando. Después de un tiempo (actualmente de 30 segundos), el archivo se envía al servidor de AEM en segundo plano.

A diferencia de Creative Cloud Desktop u otras soluciones de sincronización de archivos, como Microsoft One Drive, AEM aplicación de escritorio no es un cliente de sincronización de escritorio completo. El motivo de esto es que proporciona acceso a todo el repositorio de AEM Assets, que puede ser extremadamente grande (cientos de gigabytes o terabytes) para una sincronización completa.

El almacenamiento en caché permite limitar la sobrecarga de red/almacenamiento a sólo un subconjunto de recursos relevantes para el usuario.

>[!CAUTION]
>
>Adobe recomienda desactivar la generación de miniaturas para acelerar la navegación. Si activa las previsualizaciones de iconos, la aplicación almacenará en caché los recursos digitales al navegar por la carpeta montada. La aplicación también descarga recursos que al usuario no le importan, lo que agrega carga al servidor, consume el ancho de banda del usuario y utiliza más espacio en disco del usuario.

A continuación se muestra cómo AEM aplicación de escritorio realiza el almacenamiento en caché:

* Al abrir una carpeta en Finder y mostrar miniaturas/previsualizaciones de archivos, o al abrir un archivo en una aplicación, la aplicación de escritorio almacena en caché el archivo binario.
* Cuando almacena archivos mediante Finder u otras aplicaciones de escritorio, el archivo se almacena primero localmente (en caché) y se notifica al sistema operativo. A continuación, el archivo se pone en cola para su carga en el servidor en segundo plano y, finalmente, se carga a través de la red. En caso de error de red, la aplicación de escritorio reintentos la carga de todo el archivo durante un máximo de tres veces. Si el archivo no se carga después de tres reintentos, se marca como un archivo en conflicto y el estado se muestra mediante la ventana Estado de la cola de carga en segundo plano. la aplicación de escritorio ya no intenta actualizar el archivo. El usuario debe actualizar el archivo y volver a cargarlo una vez restaurada la conectividad

Todas las operaciones no se almacenan en caché localmente. Los siguientes datos se transmiten al servidor AEM inmediatamente sin almacenamiento en caché local:

* Cualquier operación en carpetas, por ejemplo, crear, eliminar, etc.
* La funcionalidad Carga de carpetas introducida en la versión 1.4 carga una jerarquía de carpetas local sin almacenar en caché los archivos localmente

## Operaciones individuales {#individual-operations}

Al solucionar problemas de rendimiento suboptimizado para usuarios individuales, primero revise [Limitaciones](https://helpx.adobe.com/experience-manager/desktop-app/troubleshooting-desktop-app.html#limitations). Las secciones siguientes incluyen sugerencias para mejorar el rendimiento de los usuarios individuales.

## Recomendaciones de ancho de banda {#bandwidth-recommendations}

El ancho de banda disponible para un usuario individual juega un papel fundamental en el rendimiento del cliente WebDAV/SMB.

Adobe recomienda que la velocidad de carga de un usuario individual sea cercana a 10 Mbps. Para las conexiones inalámbricas, el ancho de banda se comparte a menudo entre varios usuarios. Si varios usuarios realizan simultáneamente tareas que consumen ancho de banda de red, el rendimiento puede degradarse aún más. Para evitar estos problemas, utilice una conexión por cable.

## Configuraciones específicas de Windows {#windows-specific-configurations}

Si ejecuta AEM en Windows, puede configurar Windows para mejorar el rendimiento del cliente WebDAV. Para obtener más información, vaya a [https://support.microsoft.com/en-us/kb/2445570](https://support.microsoft.com/en-us/kb/2445570).

En Windows 7, la modificación de la configuración de IE puede mejorar el rendimiento de WebDAV. Para obtener más información, consulte cómo [corregir el rendimiento lento de WebDAV en Windows 7](https://oddballupdate.com/2009/12/fix-slow-webdav-performance-in-windows-7/).

## Operaciones simultáneas {#concurrent-operations}

Cuando interactúa con un archivo localmente, AEM Desktop comprueba si hay una versión más reciente del archivo disponible en AEM. Si hay una nueva versión disponible, la aplicación descarga una copia nueva del archivo en la caché local. Sin embargo, AEM Desktop no sobrescribe un archivo en caché local si se ha modificado. Esta función evita que el trabajo se sobrescriba por error.

Cuando se modifica el mismo archivo tanto localmente como en AEM, la versión modificada localmente sobrescribe la versión en AEM. En este caso, la versión anterior está disponible en la línea de tiempo del recurso. Puede verificar ambas versiones y resolver cualquier conflicto.

Si un archivo local no es coherente con la versión disponible en el servidor, el cuadro de diálogo de estado de carga en segundo plano le notifica sobre el conflicto. Para resolver el problema, abra el archivo en conflicto y guárdelo. Al guardar el archivo, AEM Desktop se ve obligado a sincronizar los últimos cambios locales con AEM. Puede realizar la vista de versiones anteriores del recurso en la línea de tiempo y resolver cualquier conflicto.

Debe tener en cuenta factores adicionales cuando varios usuarios intenten trabajar en directorios montados separados que tengan como objetivo la misma instancia de AEM. En particular, son importantes los siguientes factores:

* Cantidad de ancho de banda disponible en la red de origen de los usuarios
* Configuración de red, como servidores de seguridad o proxies, de la red de origen
* Cantidad de ancho de banda disponible en la red de la instancia de destinatario AEM
* Indica si un distribuidor está presente antes de la instancia de AEM de destinatario
* Carga actual en la instancia de destinatario AEM

## Configuraciones de AEM adicionales {#additional-aem-configurations}

Si el rendimiento de WebDAV/SMB se degrada drásticamente cuando varios usuarios trabajan simultáneamente, puede configurar algunas cosas en AEM, lo que puede ayudar a mejorar el rendimiento.

## Actualizar flujos de trabajo transitorios de recursos {#update-asset-transient-workflows}

Puede mejorar el rendimiento en el lado AEM habilitando flujos de trabajo transitorios para el flujo de trabajo de recursos de actualización de DAM. Al habilitar flujos de trabajo transitorios, se reduce la potencia de procesamiento necesaria para actualizar los recursos cuando se crean o modifican en AEM.

1. Vaya a `/miscadmin` en la instancia de AEM que se va a configurar (por ejemplo, `http://[Server]:[Port]/miscadmin`).
1. En el árbol de navegación, expanda **Herramientas** > **Flujo de trabajo** > **Modelos** > **Dam**.
1. Haga clic con el doble **Recurso de actualización de DAM**.
1. En el panel de herramientas flotantes, cambie a la ficha **Página** y haga clic en **Propiedades de la página**.
1. Seleccione la casilla de verificación **Flujo de trabajo transitorio** y haga clic en **Aceptar**.

### Ajustar cola de flujo de trabajo transitorio de granito {#adjust-granite-transient-workflow-queue}

Otro método para mejorar el rendimiento de AEM es configurar el valor de los trabajos paralelos máximos para el trabajo de cola de flujo de trabajo transitorio de Granite. El valor recomendado es aproximadamente la mitad del número de CPU disponible con el servidor. Para ajustar el valor, siga estos pasos:

1. Vaya a */system/console/configMgr* en la instancia de AEM que se va a configurar (por ejemplo, `http://[aem_server]:[port]/system/console/configMgr`).
1. Busque **QueueConfiguration** y haga clic para abrir cada trabajo hasta que encuentre el trabajo **Granite Transient Workflow Queue**. Haga clic en Editar junto a ella.
1. Cambie el valor **Número máximo de trabajos paralelos** y haga clic en **Guardar**.

## Configuración de AWS {#aws-configuration}

Debido a las limitaciones de ancho de banda de la red, el rendimiento de WebDAV/SMB puede degradarse cuando varios usuarios trabajan simultáneamente. Adobe recomienda aumentar el tamaño de la instancia de AWS para una instancia de AEM de destinatario que se ejecute en AWS para mejorar el rendimiento de WebDAV/SMB.

Esta medida aumenta específicamente la cantidad de ancho de banda de red disponible para el servidor. Aquí algunos detalles:

* La cantidad de ancho de banda de red dedicado a una instancia de AWS aumenta a medida que aumenta el tamaño de la instancia. Para obtener información sobre la cantidad de ancho de banda disponible para cada tamaño de instancia, consulte la [documentación de AWS](https://aws.amazon.com/ec2/instance-types/).
* Al solucionar problemas de un cliente grande, Adobe configuró el tamaño de su instancia de AEM a c4.8xlarge, principalmente para los 4000 Mbps de ancho de banda dedicado que proporciona.
* Si hay un despachante por delante de la instancia de AEM, asegúrese de que tenga el tamaño adecuado. Si la instancia de AEM proporciona 4000 Mbps pero el despachante sólo proporciona 500 Mbps, el ancho de banda efectivo es de sólo 500 Mbps. Es porque el despachante crea un cuello de botella de red.

## Limitaciones de archivos extraídos {#checked-out-file-limitations}

Existen algunas limitaciones conocidas en la manera de interactuar con los archivos extraídos a través del Explorador/Finder. Si un archivo está desprotegido, debe ser de solo lectura para cualquier persona excepto el usuario que tenga el archivo desprotegido. La implementación del protocolo WebDAV/SMB1 en AEM aplica esta regla. Sin embargo, los clientes de OS WebDAV/SMB no interactúan con elegancia con los archivos extraídos. A continuación se describen algunas rarezas.

### General {#general}

Al escribir en un archivo extraído, el bloqueo solo se aplica en AEM implementación WebDAV. En consecuencia, el bloqueo solo lo aplican los clientes que utilizan WebDAV, como la aplicación de escritorio. El bloqueo no se aplica mediante AEM interfaz web. La interfaz de AEM solo muestra un icono de candado en la vista de tarjetas para los recursos que se han extraído. El icono es cosmético y no afecta al comportamiento de AEM.

En general, los clientes de WebDAV no siempre se comportan de la manera esperada. Puede haber problemas adicionales. Sin embargo, actualizar o comprobar el recurso en AEM es una forma sólida de comprobar que no se está modificando un recurso. Este comportamiento es típico de los clientes WebDAV del SO, que no están bajo el control del Adobe.

### Windows {#windows}

Parece que la eliminación de un archivo es correcta porque el archivo desaparece del explorador de archivos en Windows. Sin embargo, la actualización del directorio y la protección de AEM recursos muestran que el archivo aún está presente. Además, la edición de archivos parece tener éxito (no se muestran diálogos de advertencia ni mensajes de error). Sin embargo, si se vuelve a abrir el archivo o se protegen AEM recursos, se comprueba que el archivo no se ha modificado.

#### Mac OS X {#mac-os-x}

Reemplazar un archivo no muestra una advertencia o un error, pero si se comprueba el recurso en AEM, se muestra que permanece sin cambios. Actualice o marque el recurso en AEM para comprobar que no se está modificando.

## Resolución de problemas con el icono de la aplicación de escritorio (Mac OS X) {#troubleshooting-desktop-app-icon-issues-mac-os-x}

Después de instalar la aplicación de escritorio, el icono de menú de la aplicación de escritorio aparece en la barra de menús. Si el icono no aparece, siga estos pasos para resolver el problema:

1. Abra la ventana del terminal del sistema operativo.
1. Escriba el siguiente comando en el símbolo del sistema y, a continuación, pulse Intro:

   ```shell
    cd ../Library/Caches.
   ```

1. Escriba el siguiente comando y pulse Intro:

   ```shell
   rm -r com.adobe.aem.assetscompanion
   ```

1. Escriba el siguiente comando y pulse Intro:

   ```shell
   cd ~/Library/Preferences
   ```

1. Escriba el siguiente comando y pulse Intro:

   ```shell
   rm com.adobe.aem.assetscompanion.plist
   ```

1. Escriba el siguiente comando y pulse Intro:

   ```shell
   rm ~/Library/Group\ Containers/group.com.adobe.aem.desktop/*
   ```

1. Reinicie el sistema.

AEM Desktop intenta sincronizar un archivo determinado tres veces. Si el archivo no se puede sincronizar después del tercer intento, AEM Desktop considera que el archivo está en conflicto y le notifica mediante la ventana de estado de carga en segundo plano. Un estado de conflicto indica que los cambios más recientes aún están disponibles para usted de forma local, pero no se sincronizan con AEM. AEM aplicación de escritorio ya no intenta sincronizar.

La manera más sencilla de solucionar esta situación es abrir el archivo en conflicto y guardarlo de nuevo. Obliga a AEM Escritorio a intentar la sincronización en tres ocasiones adicionales. Si el archivo sigue sin sincronizarse, consulte las secciones siguientes para obtener más ayuda.

## Borrado de la caché de AEM Desktop {#clearing-aem-desktop-cache}

Borrado de la caché de AEM Desktop es una tarea preliminar de resolución de problemas que puede resolver varios problemas AEM Desktop.

Puede borrar la caché eliminando el directorio de caché de la aplicación en las siguientes ubicaciones.
En Windows, `%LocalAppData%\Adobe\AssetsCompanion\Cache\`

En Mac, `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/`

Sin embargo, la ubicación puede cambiar en función del extremo de AEM configurado AEM Desktop. El valor es una versión codificada de la dirección URL de destino. Por ejemplo, si la aplicación está dirigiendo `http://localhost:4502`, el nombre del directorio es `http%3A%2F%2Flocalhost%3A4502%2F`.

Para borrar la caché, elimine el directorio &lt;Encoded AEM Endpoint>.

>[!NOTE]
>
>Si borra AEM caché de escritorio, se perderán los cambios de archivos locales que no se hayan sincronizado con AEM.

>[!NOTE]
>
>A partir de AEM aplicación de escritorio versión 1.5, existe una opción en la interfaz de usuario de la aplicación de escritorio para borrar la caché.

## Búsqueda de la versión de AEM Desktop {#finding-the-aem-desktop-version}

El procedimiento para determinar la versión de AEM Desktop es el mismo para Windows y Mac OS.

Haga clic en el icono AEM Escritorio y, a continuación, elija **Acerca de**. El número de versión se muestra en la pantalla.

## Actualización de AEM aplicación de escritorio en macOS {#upgrading-aem-desktop-app-on-macos}

En ocasiones pueden producirse problemas al actualizar AEM aplicación de escritorio en macOS. Esto se debe a que la carpeta de sistema heredada de AEM aplicación de escritorio impide que las nuevas versiones de AEM Desktop se carguen correctamente. Para solucionar este problema, se pueden quitar manualmente las siguientes carpetas y archivos.

Antes de ejecutar los pasos a continuación, arrastre la aplicación &quot;Adobe Experience Manager Desktop&quot; de la carpeta Aplicaciones macOS a la papelera. A continuación, abra terminal y ejecute el siguiente comando, proporcionando su contraseña cuando se le solicite.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## Guardar un archivo extraído por otros {#saving-a-file-checked-out-by-others}

Las limitaciones técnicas del sistema operativo impiden que los usuarios tengan una experiencia uniforme al intentar sobrescribir un archivo extraído por otros usuarios. La experiencia varía según la aplicación utilizada para editar el archivo extraído. En ocasiones, la aplicación muestra un mensaje de error que indica un error de escritura en el disco o un error genérico o aparentemente no relacionado. En otras ocasiones, no se muestra ningún mensaje de error y la operación parece realizarse correctamente.

En este caso, cerrar y volver a abrir el archivo puede revelar que el contenido no cambia. Sin embargo, algunas aplicaciones pueden almacenar una copia de seguridad del archivo para que se puedan aplicar los cambios.

Independientemente del comportamiento, el archivo permanece sin cambios cuando lo protege. Incluso si se muestra una versión diferente del archivo, los cambios no se sincronizan con AEM.

## Solución de problemas relacionados con el desplazamiento de archivos {#troubleshooting-problems-around-moving-files}

La API de servidor requiere que se pasen encabezados adicionales, X-Destination, X-Depth y X-Overwrite, para que funcionen las operaciones de mover y copiar. El despachante no pasa estos encabezados de forma predeterminada, lo que provoca que se produzcan errores en estas operaciones. Para obtener más información, consulte [Conexión a AEM Detrás de un despachante](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher).

## Solución de problemas de conexión de AEM Desktop {#troubleshooting-aem-desktop-connection-issues}

### Problema de redirección de SAML {#saml-redirect-issue}

El motivo más común de los problemas con AEM Desktop que se conecta a la instancia de AEM habilitada para SSO (SAML) es que el proceso SAML no redirige a la ruta solicitada originalmente. Como alternativa, la conexión puede redirigirse a un host que no esté configurado en AEM escritorio. Siga estos pasos para verificar el proceso de inicio de sesión:

1. Abra un navegador web.
1. En la barra de direcciones, especifique la dirección URL `/content/dam.json`.
1. Reemplace la dirección URL con la instancia de destinatario AEM, por ejemplo `http://localhost:4502/content/dam.json`.
1. Inicie sesión en AEM.
1. Después de iniciar sesión, compruebe la dirección actual del explorador en la barra de direcciones. Debe coincidir con la dirección URL que introdujo inicialmente.
1. Compruebe que todo lo anterior a `/content/dam.json` coincide con el valor de AEM de destinatario configurado en AEM Escritorio.

### Problema de configuración SSL {#ssl-configuration-issue}

Las bibliotecas que AEM aplicación de escritorio utiliza para la comunicación HTTP utilizan una estricta aplicación SSL. A veces, una conexión puede funcionar correctamente con un navegador, pero falla al usar AEM aplicación de escritorio. Para configurar SSL correctamente, instale el certificado intermedio que falta en Apache. Consulte [Cómo instalar un certificado de CA intermedio en Apache](https://access.redhat.com/solutions/43575).

## Uso de AEM Desktop con el despachante {#using-aem-desktop-with-dispatcher}

AEM Desktop funciona con AEM implementaciones detrás de un despachante, que es una configuración predeterminada y recomendada para AEM servidores. AEM despachantes de AEM entornos de creación suelen configurarse para omitir el almacenamiento en caché de recursos DAM. Por lo tanto, los despachantes no proporcionan almacenamiento en caché adicional desde el punto de vista de AEM Desktop. Asegúrese de que la configuración del despachante esté ajustada para funcionar con AEM Desktop. Para obtener más información, consulte [Conexión a AEM detrás de un despachante](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher).

## Buscando archivos de registro {#checking-for-log-files}

Según el sistema operativo, puede encontrar los archivos de registro de AEM Desktop en las siguientes ubicaciones:

* Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`
* Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`
