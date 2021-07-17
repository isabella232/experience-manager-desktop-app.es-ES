---
title: Solución de problemas de la aplicación de escritorio versión 1.10.
description: Solucionar problemas [!DNL Adobe Experience Manager] de la aplicación de escritorio versión 1.10 para resolver los problemas ocasionales relacionados con la instalación, actualización y configuración.
exl-id: 1e1409c2-bf5e-4e2d-a5aa-3dd74166862c
source-git-commit: 32aff5d66f2cb67ab4bb440d7ace747a5cf1dd26
workflow-type: tm+mt
source-wordcount: '3350'
ht-degree: 1%

---

# Solución de problemas de la aplicación de escritorio v1.x de [!DNL Adobe Experience Manager] {#troubleshoot-aem-desktop-app}

Solucionar problemas AEM aplicación de escritorio para resolver los problemas ocasionales relacionados con la instalación, actualización, configuración, etc.

[!DNL Adobe Experience Manager] la aplicación de escritorio incluye utilidades que le ayudan a asignar el repositorio de AEM Assets como recurso compartido de red en el escritorio (recurso compartido SMB en Mac OS). El uso compartido de red es una tecnología de sistema operativo que permite que las fuentes remotas sean tratadas como si fueran parte del sistema de archivos local de un equipo. En el caso de la aplicación de escritorio, la estructura de repositorio de la administración de recursos digitales (DAM) de una instancia de AEM remota se segmenta como el origen de archivos remoto. El diagrama siguiente describe la topología de la aplicación de escritorio:

![diagrama de aplicaciones de escritorio](assets/aem-desktopapp-architecture.png)

Con esta arquitectura, la aplicación de escritorio intercepta las llamadas del sistema de archivos (abrir, cerrar, leer, escribir, etc.) al recurso compartido de red montado y las traduce a llamadas HTTP nativas AEM al servidor de AEM. Los archivos se almacenan en caché localmente. Para obtener más información, consulte [Uso de AEM aplicación de escritorio v1.x](use-app-v1.md).

## Descripción general del componente de la aplicación de escritorio AEM {#desktop-app-component-overview}

la aplicación de escritorio incluye los siguientes componentes:

* **La aplicación** de escritorio: La aplicación monta o desmonta DAM como un sistema de archivos remoto y traduce las llamadas del sistema de archivos entre el recurso compartido de red montado localmente y la instancia de AEM remota a la que se conecta.
* **Sistema operativo cliente** WebDAV/SMB: Gestiona la comunicación entre el Explorador/Buscador de Windows y la aplicación de escritorio. Si se recupera, crea, modifica, elimina, mueve o copia un archivo, el cliente de sistema operativo (OS) WebDAV/SMB comunica esta operación a la aplicación de escritorio. Después de recibir la comunicación, la aplicación de escritorio la traduce en llamadas API nativas AEM remotas. Por ejemplo, si un usuario crea un archivo en el directorio montado, el cliente WebDAV/SMB inicia una solicitud, que la aplicación de escritorio traduce en una solicitud HTTP que crea el archivo en DAM. El cliente WebDAV/SMB es un componente integrado del sistema operativo. No está afiliado a la aplicación de escritorio, AEM ni Adobe de ninguna manera.
* **Instancia** de Adobe Experience Manager: Proporciona acceso a los recursos almacenados en el repositorio de AEM Assets DAM. Además, realiza las acciones solicitadas por la aplicación de escritorio en nombre de las aplicaciones de escritorio locales que interactúan con el recurso compartido de red montado. La instancia de AEM de destino debe ejecutar AEM versión 6.1 o superior. AEM instancias que ejecutan versiones de AEM anteriores pueden requerir paquetes de funciones y correcciones adicionales instalados para ser completamente funcionales.

## Casos de uso previstos para AEM aplicación de escritorio {#intended-use-cases-for-aem-desktop-app}

AEM aplicación de escritorio utiliza la tecnología de red compartida para asignar un repositorio de AEM remoto a un escritorio local. Sin embargo, no se pretende reemplazar a un recurso compartido de red que contenga recursos, donde los usuarios realizan operaciones de administración de recursos digitales directamente desde su escritorio local. Estas incluyen mover o copiar varios archivos, o arrastrar estructuras de carpetas grandes al recurso compartido de red de AEM Assets directamente en Finder/Explorer.

AEM aplicación de escritorio proporciona una forma cómoda de acceder (abrir) y editar (guardar) recursos DAM entre la interfaz de usuario de AEM Assets Touch y el escritorio local. Vincula recursos del servidor de AEM Assets con los flujos de trabajo basados en escritorio.

El siguiente ejemplo de uso ilustra cómo se debe utilizar AEM Desktop:

* Un usuario inicia sesión en AEM y utiliza la interfaz de usuario web para localizar un recurso.
* Con las funciones de acción de escritorio de la interfaz de usuario web AEM, el usuario abre, muestra o edita el recurso en el escritorio según sea necesario.
* AEM Desktop abre el recurso en el editor predeterminado para el tipo de archivo del recurso.
* El usuario realiza los cambios que desee en el recurso.
* Una vez modificado un archivo, el usuario puede ver el estado de sincronización del archivo mediante AEM ventana de estado de sincronización en segundo plano de Desktop.
* Con el menú contextual de AEM Escritorio, el usuario inicia o cierra la compra del recurso o regresa a la interfaz de usuario de DAM.
* Después de completar los cambios en el archivo, el usuario vuelve a la interfaz de usuario web AEM

Este no es el único caso de uso. Sin embargo, ilustra cómo AEM Escritorio es un mecanismo cómodo para acceder o editar recursos localmente. Se le recomienda utilizar la interfaz de usuario web de DAM tanto como sea posible, ya que ofrece una mejor experiencia. Proporciona a los Adobes más flexibilidad para satisfacer los requerimientos de los clientes.

## Restricciones     {#limitations}

El recurso compartido de red WebDAV/SMB1 proporciona la comodidad de trabajar con archivos en una ventana del Explorador/Buscador. Sin embargo, Explorer/Finder y AEM se comunican a través de una conexión de red que tiene ciertas limitaciones. Por ejemplo, el tiempo que se tarda en copiar un archivo de 1 GB en el directorio WebDAV/SMB montado es aproximadamente el mismo que el tiempo necesario para cargar un archivo de 1 GB a un sitio web mediante un explorador web. De hecho, en el primer caso, la duración puede ser mayor debido a las ineficiencias del protocolo WebDAV/SMB y de los clientes WebDAV/SMB del sistema operativo (particularmente Mac OS X).

Existen limitaciones a los tipos de tareas que se pueden realizar desde un directorio montado. En general, trabajar con archivos de gran tamaño, especialmente con una conexión de red de baja latencia, alta latencia y bajo ancho de banda, puede ser complicado, especialmente cuando se editan archivos de gran tamaño.

Adobe recomienda realizar algunas pruebas de casos de uso antes de comprometerse con un cliente para que ciertos tipos de archivos se puedan editar de forma eficiente en el lugar desde el directorio montado.

AEM Desktop no es adecuado para realizar manipulaciones intensivas del sistema de archivos, incluidas, entre otras:

* Mover o copiar archivos y directorios
* Adición de muchos recursos a AEM
* Búsqueda y apertura de archivos a través del sistema de archivos, excepto para explorar carpetas
* Compresión o descompresión de archivos

Debido a las limitaciones del sistema operativo, Windows tiene un límite de tamaño de archivo de 4.294.967.295 bytes (aproximadamente 4,29 GB). Se debe a una configuración de registro que define el tamaño que puede tener un archivo en un recurso compartido de red. El valor de la configuración del Registro es un DWORD con un tamaño máximo igual al número al que se hace referencia.

[!DNL Experience Manager] la aplicación de escritorio no tiene un valor de tiempo de espera que se pueda configurar y que desconecte la conexión entre el  [!DNL Experience Manager] servidor y la aplicación de escritorio después de un intervalo de tiempo fijo. Al cargar recursos de gran tamaño, si la conexión supera el tiempo de espera después de un tiempo, la aplicación vuelve a intentar cargar el recurso varias veces aumentando el tiempo de espera de carga. No se recomienda cambiar la configuración de tiempo de espera predeterminada.

## Almacenamiento en caché y comunicación con AEM {#caching-and-communication-with-aem}

AEM aplicación de escritorio proporciona funciones internas de almacenamiento en caché y carga en segundo plano para mejorar la experiencia del usuario final. Cuando se guarda un archivo grande, primero se guarda localmente para permitirle seguir trabajando. Después de un tiempo (actualmente de 30 segundos), el archivo se envía al servidor de AEM en segundo plano.

A diferencia de Creative Cloud Desktop u otras soluciones de sincronización de archivos, como Microsoft One Drive, AEM aplicación de escritorio no es un cliente de sincronización de escritorio completo. El motivo es que proporciona acceso a todo el repositorio de AEM Assets, que puede ser extremadamente grande (cientos de gigabytes o terabytes) para una sincronización completa.

El almacenamiento en caché permite limitar la sobrecarga de red/almacenamiento a solo un subconjunto de recursos que sean relevantes para el usuario.

>[!CAUTION]
>
>Adobe recomienda desactivar la generación de miniaturas para acelerar la navegación. Si activa las vistas previas de iconos, la aplicación almacenará en caché los recursos digitales al desplazarse por la carpeta montada. La aplicación también descarga recursos que puede no interesar al usuario, lo que añade carga al servidor, consume el ancho de banda del usuario y utiliza más espacio en disco del usuario.

A continuación se muestra AEM aplicación de escritorio realiza el almacenamiento en caché:

* Cuando abre una carpeta en Finder y se muestran miniaturas/previsualizaciones de archivos, o cuando abre un archivo en una aplicación, la aplicación de escritorio almacena en caché el binario del archivo.
* Cuando almacena archivos a través de Finder u otras aplicaciones de escritorio, el archivo se almacena localmente primero (en caché) y se notifica al sistema operativo. A continuación, el archivo se coloca en cola para su carga en el servidor en segundo plano y, finalmente, se carga a través de la red. En caso de error de red, la aplicación de escritorio reintenta la carga de todo el archivo durante un máximo de tres veces. Si el archivo no se carga después de tres reintentos, se marca como un archivo en conflicto y el estado se muestra a través de la ventana Estado de cola de carga en segundo plano. la aplicación de escritorio ya no intenta actualizar el archivo. El usuario debe actualizar el archivo y volver a cargarlo después de restaurar la conectividad

Todas las operaciones no se almacenan en caché localmente. Los siguientes mensajes se transmiten al servidor de AEM inmediatamente sin el almacenamiento en caché local:

* Cualquier operación en carpetas, como crear, eliminar, etc.
* La funcionalidad Carga de carpetas introducida en la versión 1.4 carga una jerarquía de carpetas local sin almacenar en caché los archivos localmente

## Operaciones individuales {#individual-operations}

Al solucionar problemas de rendimiento suboptimizado para usuarios individuales, revise primero [las limitaciones de la aplicación](#limitations). Las secciones siguientes incluyen sugerencias para mejorar el rendimiento para los usuarios individuales.

## Recomendaciones de ancho de banda {#bandwidth-recommendations}

El ancho de banda disponible para un usuario individual juega un papel crítico en el rendimiento del cliente WebDAV/SMB.

Adobe recomienda que la velocidad de carga de un usuario individual sea cercana a 10 Mbps. Para las conexiones inalámbricas, el ancho de banda se comparte a menudo entre varios usuarios. Si varios usuarios realizan simultáneamente tareas que consumen ancho de banda de red, el rendimiento puede degradarse aún más. Para evitar estos problemas, utilice una conexión por cable.

## Configuraciones específicas de Windows {#windows-specific-configurations}

Si utiliza Experience Manager en Windows, puede configurar Windows para mejorar el rendimiento del cliente WebDAV. Para obtener más información, vaya a [https://support.microsoft.com/en-us/kb/2445570](https://support.microsoft.com/es-es/kb/2445570).

En Windows 7, modificar la configuración de IE puede mejorar el rendimiento de WebDAV. Para obtener más información, consulte cómo [corregir el rendimiento lento de WebDAV en Windows 7](https://oddballupdate.com/2009/12/fix-slow-webdav-performance-in-windows-7/).

<!-- TBD: The above performance tip is for Windows 7 which is not supported by the app anymore. Remove it later.
-->

## Operaciones simultáneas {#concurrent-operations}

Cuando interactúa con un archivo localmente, AEM Desktop comprueba si hay una versión más reciente del archivo disponible en AEM. Si hay una versión nueva disponible, la aplicación descarga una copia nueva del archivo en la caché local. Sin embargo, AEM Desktop no sobrescribe un archivo almacenado en caché local si se ha modificado. Esta función evita que el trabajo se sobrescriba de forma involuntaria.

Cuando se modifica el mismo archivo tanto localmente como en AEM, la versión modificada localmente sobrescribe la versión en AEM. En este caso, la versión anterior está disponible en la línea de tiempo del recurso. Puede verificar ambas versiones y resolver cualquier conflicto.

Si un archivo local no es coherente con la versión disponible en el servidor, el cuadro de diálogo de estado de carga en segundo plano le notifica sobre el conflicto. Para resolver el problema, abra el archivo conflictivo y guárdelo. Al guardar el archivo, AEM Desktop sincroniza los cambios locales más recientes con AEM. Puede ver las versiones anteriores del recurso en la cronología y resolver cualquier conflicto.

Debe tener en cuenta los factores adicionales cuando varios usuarios intentan trabajar en directorios montados separados dirigidos a la misma instancia de AEM. En particular, son importantes los siguientes factores:

* Cantidad de ancho de banda disponible en la red de origen de los usuarios
* Configuración de red, como firewalls o proxies, de la red de origen
* Cantidad de ancho de banda disponible en la red de la instancia de AEM de destino
* Indica si Dispatcher está presente antes de la instancia de AEM de destino
* Carga actual en la instancia de AEM de destino

## Configuraciones de AEM adicionales {#additional-aem-configurations}

Si el rendimiento de WebDAV/SMB se degrada drásticamente cuando varios usuarios trabajan simultáneamente, puede configurar algunas cosas en AEM, lo que puede ayudar a mejorar el rendimiento.

## Actualizar flujos de trabajo transitorios de recursos {#update-asset-transient-workflows}

Puede mejorar el rendimiento en el lado AEM habilitando flujos de trabajo transitorios para el flujo de trabajo de recursos de actualización de DAM. La activación de flujos de trabajo transitorios reduce la potencia de procesamiento necesaria para actualizar recursos cuando se crean o modifican en AEM.

1. Vaya a `/miscadmin` en la instancia de Experience Manager (`https://[aem_server]:[port]/miscadmin`).
1. En el árbol de navegación, expanda **Herramientas** > **Flujo de trabajo** > **Modelos** > **Dam**.
1. Haga doble clic en **Recurso de actualización de DAM**.
1. En el panel de herramientas flotantes, cambie a la pestaña **Página** y haga clic en **Propiedades de página**.
1. Seleccione la casilla **Transient Workflow** y haga clic en **OK**.

### Ajustar cola de flujo de trabajo transitorio de granito {#adjust-granite-transient-workflow-queue}

Otro método para mejorar AEM rendimiento es configurar el valor de los trabajos paralelos máximos para el trabajo de cola de flujo de trabajo transitorio de Granite. El valor recomendado es aproximadamente la mitad del número de CPU disponible con el servidor. Para ajustar el valor, siga estos pasos:

1. Vaya a `/system/console/configMgr` en la instancia de AEM que se va a configurar (por ejemplo, `https://[aem_server]:[port]/system/console/configMgr`).
1. Busque `QueueConfiguration` y haga clic en para abrir cada trabajo hasta que localice el trabajo **Granite Transient Workflow Queue** y haga clic en **Edit**.
1. Cambie el valor `Maximum Parallel Jobs` y haga clic en **Guardar**.

## Configuración de AWS {#aws-configuration}

Debido a las limitaciones de ancho de banda de la red, el rendimiento de WebDAV/SMB puede degradarse cuando varios usuarios trabajan simultáneamente. Adobe recomienda aumentar el tamaño de la instancia de AWS para una instancia de AEM de destino que se ejecute en AWS para mejorar el rendimiento de WebDAV/SMB.

Esta medida aumenta específicamente la cantidad de ancho de banda de red disponible para el servidor. A continuación, algunos detalles:

* La cantidad de ancho de banda de red dedicado a una instancia de AWS aumenta a medida que aumenta el tamaño de la instancia. Para obtener información sobre la cantidad de ancho de banda disponible para cada tamaño de instancia, consulte la [documentación de AWS](https://aws.amazon.com/ec2/instance-types/).
* Al solucionar problemas para un cliente grande, el Adobe configuró el tamaño de su instancia de AEM a c4.8xlarge, principalmente para los 4000 Mbps de ancho de banda dedicado que proporciona.
* Si hay un despachante por delante de la instancia de AEM, asegúrese de que tenga el tamaño adecuado. Si la instancia de AEM proporciona 4000 Mbps pero Dispatcher solo proporciona 500 Mbps, el ancho de banda efectivo es de sólo 500 Mbps. Esto se debe a que Dispatcher crea un cuello de botella de red.

## Limitaciones de archivos extraídos {#checked-out-file-limitations}

Existen algunas limitaciones conocidas en la forma en que puede interactuar con archivos extraídos a través del Explorador/Buscador. Si un archivo está desprotegido, debe ser de solo lectura para cualquiera que no sea el usuario que tenga el archivo desprotegido. La implementación del protocolo WebDAV/SMB1 en AEM aplica esta regla. Sin embargo, los clientes de OS WebDAV/SMB a menudo no interactúan correctamente con los archivos extraídos. A continuación se describen algunas rarezas.

### General {#general}

Al escribir en un archivo extraído, el bloqueo solo se aplica en AEM implementación de WebDAV. Por lo tanto, el bloqueo solo lo aplican los clientes que utilizan WebDAV, como la aplicación de escritorio. El bloqueo no se aplica a través AEM interfaz web. La interfaz de AEM solo muestra un icono de candado en la vista de tarjeta para los recursos que se han extraído. El icono es estético y no tiene ningún efecto en el comportamiento de AEM.

En general, los clientes de WebDAV no siempre se comportan como se espera. Puede haber problemas adicionales. Sin embargo, actualizar o comprobar el recurso en AEM es una forma correcta de comprobar que un recurso no se está modificando. Este comportamiento es típico de los clientes de OS WebDAV, que no están bajo control del Adobe.

### Windows {#windows}

Parece que la eliminación de un archivo es correcta porque el archivo desaparece del explorador de archivos en Windows. Sin embargo, al actualizar el directorio y proteger AEM recursos, se muestra que el archivo sigue presente. Además, parece que la edición de archivos se ha realizado correctamente (no se muestran cuadros de diálogo de advertencia ni mensajes de error). Sin embargo, si se vuelve a abrir el archivo o se comprueba AEM recursos, el archivo no se modifica.

#### Mac OS X {#mac-os-x}

Reemplazar un archivo no muestra una advertencia o un error, pero comprobar el recurso en AEM revela que permanece sin cambios. Actualice o marque el recurso en AEM para comprobar que no se está modificando.

## Solución de problemas con los iconos de las aplicaciones de escritorio (Mac OS X) {#troubleshooting-desktop-app-icon-issues-mac-os-x}

Después de instalar la aplicación de escritorio, el icono del menú de la aplicación de escritorio aparece en la barra de menús. Si no aparece el icono, realice estos pasos para resolver el problema:

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

AEM Escritorio intenta sincronizar cualquier archivo determinado tres veces. Si el archivo no se sincroniza después del tercer intento, AEM Desktop considera que el archivo está en conflicto y le notifica a través de la ventana de estado de carga en segundo plano. Un estado de conflicto indica que los cambios más recientes aún están disponibles para usted de forma local, pero no se sincronizan de nuevo con AEM. AEM aplicación de escritorio ya no intenta sincronizar.

La forma más sencilla de solucionar esta situación es abrir el archivo conflictivo y guardarlo de nuevo. Obliga a AEM Escritorio a intentar la sincronización en otras tres ocasiones. Si el archivo sigue sin sincronizarse, consulte las secciones siguientes para obtener más ayuda.

## Borrado de la caché de AEM Desktop {#clearing-aem-desktop-cache}

Borrar la caché de AEM Desktop es una tarea preliminar de solución de problemas que puede resolver varios problemas de AEM Desktop.

Puede borrar la caché eliminando el directorio de caché de la aplicación en las siguientes ubicaciones.
En Windows, `%LocalAppData%\Adobe\AssetsCompanion\Cache\`

En Mac, `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/`

Sin embargo, la ubicación puede cambiar dependiendo del punto final de AEM configurado AEM Escritorio. El valor es una versión codificada de la dirección URL de destino. Por ejemplo, si la aplicación está dirigiéndose a `http://localhost:4502`, el nombre del directorio es `http%3A%2F%2Flocalhost%3A4502%2F`.

Para borrar la caché, elimine el directorio &lt;Encoded AEM Endpoint>.

>[!NOTE]
>
>Si borra AEM caché de Escritorio, se perderán los cambios en los archivos locales que no se sincronizan con AEM.

>[!NOTE]
>
>A partir de AEM versión 1.5 de la aplicación de escritorio, existe una opción en la interfaz de usuario de la aplicación de escritorio para borrar la caché.

## Búsqueda de la versión de AEM Desktop {#finding-the-aem-desktop-version}

El procedimiento para determinar la versión de AEM Desktop es el mismo para Windows y Mac OS.

Haga clic en el icono AEM Escritorio y, a continuación, elija **Acerca de**. El número de versión se muestra en la pantalla.

## Actualización de AEM aplicación de escritorio en macOS {#upgrading-aem-desktop-app-on-macos}

En ocasiones pueden producirse problemas al actualizar AEM aplicación de escritorio en macOS. Esto se debe a que la carpeta del sistema heredada de AEM aplicación de escritorio impide que las nuevas versiones de AEM Desktop se carguen correctamente. Para solucionar este problema, las siguientes carpetas y archivos se pueden eliminar manualmente.

Antes de ejecutar los pasos siguientes, arrastre la aplicación &quot;Adobe Experience Manager Desktop&quot; de la carpeta Aplicaciones macOS a la Papelera. A continuación, abra terminal y ejecute el siguiente comando, proporcionando su contraseña cuando se le solicite.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## Guardar un archivo extraído por otros usuarios {#saving-a-file-checked-out-by-others}

Las limitaciones técnicas del sistema operativo impiden que los usuarios tengan una experiencia coherente cuando intentan sobrescribir un archivo que otros desprotegen. La experiencia varía según la aplicación utilizada para editar el archivo extraído. A veces, la aplicación muestra un mensaje de error que indica un error de escritura en disco o muestra un error aparentemente no relacionado o genérico. En otras ocasiones, no se muestra ningún mensaje de error y la operación parece realizarse correctamente.

En este caso, cerrar y volver a abrir el archivo puede revelar que el contenido no cambia. Sin embargo, algunas aplicaciones pueden almacenar una copia de seguridad del archivo para que se puedan aplicar los cambios.

Independientemente del comportamiento, el archivo permanece sin cambios cuando lo protege. Aunque se muestre una versión diferente del archivo, los cambios no se sincronizan con AEM.

## Solución de problemas relacionados con el desplazamiento de archivos {#troubleshooting-problems-around-moving-files}

La API del servidor requiere encabezados adicionales, X-Destination, X-Depth y X-Overwrite, que se pasen para que funcionen las operaciones de mover y copiar. Dispatcher no pasa estos encabezados de forma predeterminada, lo que provoca que estas operaciones fallen. Para obtener más información, consulte [Conexión a AEM detrás de un Dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher).

## Solución de problemas AEM conexión de escritorio {#troubleshooting-aem-desktop-connection-issues}

### Problema de redireccionamiento de SAML {#saml-redirect-issue}

El motivo más común de los problemas con AEM Escritorio conectado a la instancia de AEM habilitada para SSO (SAML) es que el proceso SAML no redirige a la ruta solicitada originalmente. Como alternativa, la conexión se puede redirigir a un host que no esté configurado en AEM escritorio. Siga estos pasos para verificar el proceso de inicio de sesión:

1. Abra un explorador web.
1. En la barra de direcciones, especifique la dirección URL `/content/dam.json`.
1. Reemplace la dirección URL con la instancia de AEM de destino, por ejemplo `https://localhost:4502/content/dam.json`.
1. Inicie sesión en AEM.
1. Después de iniciar sesión, compruebe la dirección actual del explorador en la barra de direcciones. Debe coincidir con la dirección URL que introdujo inicialmente.
1. Compruebe que todo lo anterior a `/content/dam.json` coincide con el valor de AEM de destino configurado en AEM Escritorio.

### Problema de configuración de SSL {#ssl-configuration-issue}

Las bibliotecas que utiliza AEM aplicación de escritorio para la comunicación HTTP utilizan una estricta aplicación SSL. A veces, una conexión puede funcionar correctamente con un explorador, pero falla al usar AEM aplicación de escritorio. Para configurar SSL correctamente, instale el certificado intermedio que falta en Apache. Consulte [Cómo instalar un certificado de CA intermedio en Apache](https://access.redhat.com/solutions/43575).

## Uso de AEM Desktop con Dispatcher {#using-aem-desktop-with-dispatcher}

AEM Desktop funciona con AEM implementaciones detrás de un Dispatcher, que es una configuración predeterminada y recomendada para los servidores de AEM. AEM distribuidores delante de AEM entornos de creación suelen configurarse para omitir el almacenamiento en caché de los recursos DAM. Por lo tanto, los distribuidores no proporcionan almacenamiento en caché adicional desde el punto de vista AEM Desktop. Asegúrese de que la configuración de Dispatcher esté ajustada para funcionar para AEM Escritorio. Para obtener más información, consulte [Conexión a AEM detrás de un distribuidor](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher).

## Comprobando archivos de registro {#checking-for-log-files}

Según el sistema operativo, puede encontrar los archivos de registro de AEM Desktop en las siguientes ubicaciones:

* Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`
* Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`
