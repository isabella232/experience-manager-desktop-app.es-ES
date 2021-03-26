---
title: 'Prácticas recomendadas para la solución de problemas y la aplicación de escritorio [!DNL Adobe Experience Manager] '
description: Siga las prácticas recomendadas y resuelva los problemas ocasionales relacionados con la instalación, actualización, configuración, etc.
translation-type: tm+mt
source-git-commit: 9d90bdcab79604e03d1ad3f30ed2aca2eb03e1c5
workflow-type: tm+mt
source-wordcount: '2110'
ht-degree: 0%

---


# Solución de problemas de la aplicación de escritorio [!DNL Adobe Experience Manager] {#troubleshoot-v2}

[!DNL Adobe Experience Manager] la aplicación de escritorio se conecta al repositorio de Digital Asset Management (DAM) de una  [!DNL Experience Manager] implementación. La aplicación obtiene información del repositorio y resultados de búsqueda en el equipo, descarga y carga archivos y carpetas, e incluye funciones para administrar conflictos con la interfaz de usuario de Assets.

Siga leyendo para solucionar problemas de la aplicación, conocer las prácticas recomendadas y averiguar las limitaciones.

## Prácticas recomendadas {#best-practices-to-prevent-troubles}

Siga las siguientes prácticas recomendadas para evitar algunos problemas comunes y solucionar problemas.

* **Descubra cómo funciona** la aplicación de escritorio: Antes de empezar a usar la aplicación, dedique unos momentos a saber cómo funciona la aplicación. Obtenga información sobre la vinculación entre [!DNL Experience Manager] interfaz web y escritorio, asignación de repositorios, almacenamiento en caché de recursos, guardado localmente y carga en segundo plano. Consulte [cómo funciona](release-notes.md#how-app-works).

* **Evite los caracteres no admitidos en los nombres** de carpeta: No utilice espacios en blanco ni caracteres no válidos al crear o cargar carpetas. Consulte una lista de caracteres en [Crear carpetas en [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#creating-folders). Algunos [!DNL Experience Manager] casos de uso pueden verse afectados por caracteres no compatibles en el nombre de la carpeta.

* **Prácticas recomendadas para evitar conflictos**: Para evitar posibles conflictos al colaborar en varios recursos, consulte  [evitar conflictos](using.md#adv-workflow-collaborate-avoid-conflicts) de edición.

* **Utilice la carga de carpetas para carpetas** grandes y jerárquicas: En lugar de utilizar la interfaz web de Assets u otros métodos, utilice la aplicación de  [!DNL Experience Manager] escritorio para cargar carpetas grandes. La aplicación carga los recursos en segundo plano mediante el registro y la supervisión. Consulte [carga masiva de recursos](using.md#bulk-upload-assets).

* **Utilice la versión** más reciente: Utilice la última versión de la aplicación y compruebe siempre la compatibilidad antes de instalar una nueva versión de la aplicación o antes de actualizar a una  [!DNL Experience Manager] versión más reciente. Consulte [notas de la versión](release-notes.md).

* **Utilice la misma letra** de unidad: Utilice la misma letra de unidad en una organización para asignarla a  [!DNL Experience Manager] DAM. Para ver los recursos colocados por otros usuarios, las rutas deben ser las mismas. El uso de la misma letra de unidad garantiza una ruta constante a los recursos DAM. Los recursos permanecen colocados y no se eliminan incluso si distintos usuarios utilizan distintas letras de unidad.

* **Tenga en cuenta la red**: El rendimiento de la red es fundamental para el rendimiento de la aplicación de  [!DNL Experience Manager] escritorio. Si se enfrenta a una respuesta lenta a transferencias de archivos u operaciones masivas, desactive las funciones o aplicaciones que puedan causar mucho tráfico de red.

* **Casos de uso no compatibles con la aplicación** de escritorio: No utilice la aplicación para la migración de recursos (necesita planificación y otras herramientas); para operaciones DAM de gran capacidad (como mover carpetas grandes, cargas grandes, buscar archivos mediante búsquedas avanzadas de metadatos); y como cliente de sincronización (los principios de diseño y los patrones de uso son diferentes de los clientes en sincronización como Microsoft OneDrive o Adobe Creative Cloud Desktop Sync).

* **Tiempo de espera**: Actualmente, la aplicación de escritorio no tiene un valor de tiempo de espera que se pueda configurar y que desconecte la conexión entre el  [!DNL Experience Manager] servidor y la aplicación de escritorio después de un intervalo de tiempo fijo. Al cargar recursos de gran tamaño, si la conexión supera el tiempo de espera después de un tiempo, la aplicación vuelve a intentar cargar el recurso varias veces aumentando el tiempo de espera de carga. No se recomienda cambiar la configuración de tiempo de espera predeterminada.

## Solución de problemas de {#troubleshooting-prep}

Para solucionar los problemas de las aplicaciones de escritorio, tenga en cuenta la siguiente información. Además, le prepara para transmitir mejor los problemas al Servicio de atención al cliente de Adobe si decide solicitar asistencia técnica.

### Ubicación de los archivos de registro {#check-log-files-v2}

[!DNL Experience Manager] la aplicación de escritorio almacena sus archivos de registro en las siguientes ubicaciones, en función del sistema operativo:

En Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`

En Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

Al cargar muchos recursos, si algunos archivos no se cargan, consulte el archivo `backend.log` para identificar las cargas fallidas.

>[!NOTE]
>
>Al trabajar con el Servicio de atención al cliente de Adobe en una solicitud de asistencia o ticket, se le puede pedir que comparta los archivos de registro para ayudar al equipo del Servicio de atención al cliente a comprender el problema. Archive toda la carpeta `Logs` y compártala con el contacto del Servicio de atención al cliente.

### Cambiar el nivel de detalles en los archivos de registro {#level-of-details-in-log}

Para cambiar el nivel de detalles en los archivos de registro:

1. Asegúrese de que la aplicación no se esté ejecutando.

1. En el sistema Windows:

   1. Abra una ventana de comandos.

   1. Inicie la aplicación de escritorio [!DNL Adobe Experience Manager] ejecutando el comando :

   ```shell
   set AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe
   ```

   En el sistema Mac:

   1. Abra una ventana de terminal.

   1. Inicie la aplicación de escritorio [!DNL Adobe Experience Manager] ejecutando el comando :

   ```shell
   AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app
   ```

Los niveles de registro válidos son DEBUG, INFO, WARN o ERROR. La gran diversidad de los registros es mayor en DEBUG y menor en ERROR.

### Habilitar el modo de depuración {#enable-debug-mode}

Para solucionar problemas, puede habilitar el modo de depuración y obtener más información en los registros.

>[!NOTE]
>
>Los niveles de registro válidos son DEBUG, INFO, WARN o ERROR. La gran diversidad de los registros es mayor en DEBUG y menor en ERROR.

Para usar la aplicación en modo de depuración en Mac:

1. Abra una ventana de terminal o un símbolo del sistema.

1. Inicie la aplicación de escritorio [!DNL Experience Manager] ejecutando el siguiente comando:

   `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`.

Para habilitar el modo de depuración en Windows:

1. Abra una ventana de comandos.

1. Inicie la aplicación de escritorio [!DNL Experience Manager] ejecutando el siguiente comando:

`AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe`.

### Borrar caché {#clear-cache-v2}

Siga estos pasos:

1. Inicie la aplicación y conecte una instancia [!DNL Experience Manager].

1. Abra las preferencias de la aplicación haciendo clic en los puntos suspensivos en la esquina superior derecha y seleccionando [!UICONTROL Preferences].

1. Busque la entrada que muestra [!UICONTROL Current Cache Size]. Haga clic en el icono de papelera situado junto a este elemento.

Para borrar manualmente la caché, siga los pasos a continuación.

>[!CAUTION]
>
>Esta es una operación potencialmente destructiva. Si hay cambios en el archivo local que no se cargan en [!DNL Adobe Experience Manager], esos cambios se perderán al continuar.

La caché se borra eliminando el directorio de caché de la aplicación, que se encuentra en las preferencias de la aplicación.

1. Inicie la aplicación.

1. Abra las preferencias de la aplicación seleccionando los puntos suspensivos en la esquina superior derecha y [!UICONTROL Preferences].

1. Tenga en cuenta el valor [!UICONTROL Cache Directory].

   En este directorio hay subdirectorios con el nombre de los [!DNL Adobe Experience Manager] Extremos codificados. Los nombres son una versión codificada de la dirección URL [!DNL Adobe Experience Manager] de destino. Por ejemplo, si la aplicación está dirigiéndose a `localhost:4502`, el nombre del directorio será `localhost_4502`.

Para borrar la caché, elimine el directorio del extremo [!DNL Adobe Experience Manager] codificado que desee. Como alternativa, si se elimina todo el directorio especificado en las preferencias, se borrará la caché de todas las instancias que haya utilizado la aplicación.

La eliminación de la caché de la aplicación de escritorio [!DNL Adobe Experience Manager] es una tarea preliminar de solución de problemas que puede resolver varios problemas. Borre la caché de las preferencias de la aplicación. Consulte [establecer preferencias](install-upgrade.md#set-preferences). La ubicación predeterminada de la carpeta de caché es:

### Conozca la versión [!DNL Adobe Experience Manager] de la aplicación de escritorio {#know-app-version-v2}

Para ver el número de versión:

1. Inicie la aplicación.

1. Haga clic en los puntos suspensivos en la esquina superior derecha, pase el ratón sobre [!UICONTROL Help] y haga clic en [!UICONTROL About].

   El número de versión aparece en esta pantalla.

### No se pueden ver los activos colocados {#placed-assets-missing}

Si no puede ver los recursos que usted u otros profesionales creativos colocaron en los archivos de soporte (por ejemplo, archivos INDD), compruebe lo siguiente:

* Conexión al servidor. La conectividad de red defectuosa puede detener las descargas de recursos.

* Tamaño de archivo. Los recursos grandes tardan más en descargarse y mostrarse.

* Consistencia de la letra de unidad. Si usted u otro colaborador colocó los recursos mientras asignaba el DAM [!DNL Experience Manager] a una letra de unidad diferente, no se muestran los recursos colocados.

* Permisos. Para comprobar si tiene permisos para recuperar los recursos colocados, póngase en contacto con su administrador de [!DNL Experience Manager].

### Las ediciones a archivos en la interfaz de usuario de la aplicación de escritorio no se reflejan en [!DNL Adobe Experience Manager] inmediatamente {#changes-on-da-not-visible-on-aem}

[!DNL Adobe Experience Manager] la aplicación de escritorio permite al usuario decidir cuándo se completan todas las ediciones de un archivo. Según el tamaño y la complejidad de un archivo, se tarda una cantidad de tiempo considerable en transferir la nueva versión de un archivo a [!DNL Adobe Experience Manager]. El diseño de la aplicación requiere minimizar el número de veces que un archivo se transfiere de un lado a otro, en lugar de adivinar cuándo se completan las ediciones del archivo y se cargan automáticamente. Se recomienda que el usuario inicie de nuevo la transferencia del archivo a [!DNL Adobe Experience Manager] al elegir cargar los cambios de un archivo.

### Problemas al actualizar en macOS {#issues-when-upgrading-on-macos}

Ocasionalmente pueden producirse problemas al actualizar la aplicación de escritorio [!DNL Experience Manager] en macOS. Esto se debe a que la carpeta del sistema heredada de la aplicación de escritorio [!DNL Experience Manager] impide que las nuevas versiones de la aplicación de escritorio [!DNL Experience Manager] se carguen correctamente. Para solucionar este problema, las siguientes carpetas y archivos se pueden eliminar manualmente.

Antes de ejecutar los siguientes pasos, arrastre la aplicación `Adobe Experience Manager Desktop` desde la carpeta Aplicaciones macOS a la Papelera. A continuación, abra terminal, ejecute el siguiente comando y proporcione la contraseña cuando se le solicite.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

### No se pueden cargar archivos {#upload-fails}

Si utiliza la aplicación de escritorio con [!DNL Experience Manager] 6.5.1 o posterior, actualice el conector S3 o Azure a la versión 1.10.4 o posterior. Resuelve el problema de error de carga de archivos relacionado con [OAK-8599](https://issues.apache.org/jira/browse/OAK-8599). Consulte [instrucciones de instalación](install-upgrade.md#install-v2).

### [!DNL Experience Manager] problemas de conexión de la aplicación de escritorio  {#connection-issues}

Si tiene problemas generales de conectividad, puede obtener más información sobre lo que hace la aplicación de escritorio [!DNL Experience Manager].

**Comprobar el registro de solicitudes**

[!DNL Experience Manager] la aplicación de escritorio registra todas las solicitudes que envía, junto con el código de respuesta de cada solicitud, en un archivo de registro dedicado.

1. Abra `request.log` en el directorio de registro de la aplicación para ver estas solicitudes.

1. Cada línea del registro representa una solicitud o una respuesta. Las solicitudes tendrán un carácter `>` seguido de la dirección URL solicitada. Las respuestas tendrán un carácter `<` seguido del código de respuesta y de la dirección URL solicitada. Las solicitudes y la respuesta se pueden hacer coincidir utilizando el GUID de cada línea.

**Compruebe las solicitudes cargadas por el explorador incrustado de la aplicación**

La mayoría de las solicitudes de la aplicación se encuentran en el registro de solicitudes. Sin embargo, si no hay información útil allí, puede resultar útil ver las solicitudes enviadas por el explorador incrustado de la aplicación.
Consulte la [sección SAML](#da-connection-issue-with-saml-aem) para obtener instrucciones sobre cómo ver esas solicitudes.

#### La autenticación de inicio de sesión SAML no funciona {#da-connection-issue-with-saml-aem}

[!DNL Experience Manager] es posible que la aplicación de escritorio no se conecte a la  [!DNL Adobe Experience Manager] implementación con SSO habilitado (SAML). El diseño de la aplicación intenta dar cabida a las variaciones y complejidades de las conexiones y procesos de SSO. Sin embargo, una configuración puede requerir resolución de problemas adicional.

A veces, el proceso SAML no redirige de nuevo a la ruta solicitada originalmente, o el redireccionamiento final es a un host que es diferente al configurado en la aplicación de escritorio [!DNL Adobe Experience Manager]. Para verificar que no sea así:

1. Abra un explorador web. Acceda a la dirección URL `https://[aem_server]:[port]/content/dam.json`.

1. Inicie sesión en la implementación [!DNL Adobe Experience Manager].

1. Cuando se complete el inicio de sesión, observe la dirección actual del explorador en la barra de direcciones. Debe coincidir exactamente con la dirección URL que se introdujo inicialmente.

1. Compruebe también que todo lo anterior a `/content/dam.json` coincide con el valor [!DNL Adobe Experience Manager] de destino configurado en la configuración de la aplicación de escritorio [!DNL Adobe Experience Manager].

**El proceso SAML de inicio de sesión funciona correctamente según los pasos anteriores, pero los usuarios siguen sin poder iniciar sesión**

La ventana dentro de la aplicación de escritorio [!DNL Adobe Experience Manager] que muestra el proceso de inicio de sesión es simplemente un explorador web que muestra la interfaz de usuario web de la instancia [!DNL Adobe Experience Manager] de destino:

* La versión de Mac utiliza [WebView](https://developer.apple.com/documentation/webkit/webview).

* La versión de Windows utiliza [CefSharp](https://cefsharp.github.io/) basado en Chromium.

Asegúrese de que el proceso SAML sea compatible con esos exploradores.

Para solucionar problemas aún más, es posible ver las direcciones URL exactas que el explorador está intentando cargar. Para ver esta información:

1. Siga las instrucciones para iniciar la aplicación en [modo de depuración](#enable-debug-mode).

1. Reproduzca el intento de inicio de sesión.

1. Vaya al [directorio de registro](#check-log-files-v2) de la aplicación.

1. Para Windows:

   1. Abra &quot;aemcompanionlog.txt&quot;.

   1. Busque mensajes que empiecen por &quot;La dirección del navegador de inicio de sesión ha cambiado a&quot;. Estas entradas también contienen la URL que cargó la aplicación.

   Para Mac:

   1. `com.adobe.aem.desktop-nnnnnnnn-nnnnnn.log`, donde el  **** nombre se sustituye por el número que contenga el nombre de archivo más reciente.

   1. Busque mensajes que empiecen por &quot;cuadro cargado&quot;. Estas entradas también contienen la URL que cargó la aplicación.


Ver la secuencia de URL que se está cargando puede ayudar a solucionar problemas en el extremo de SAML para determinar qué es lo que está mal.

#### Problema de configuración de SSL {#ssl-config-v2}

Las bibliotecas que utiliza la aplicación de escritorio [!DNL Experience Manager] para la comunicación HTTP utilizan una estricta aplicación SSL. A veces, una conexión puede funcionar correctamente con un explorador, pero falla al usar la aplicación de escritorio [!DNL Experience Manager]. Para configurar SSL correctamente, instale el certificado intermedio que falta en Apache. Consulte [Cómo instalar un certificado de CA intermedio en Apache](https://access.redhat.com/solutions/43575).

Las bibliotecas que utiliza la aplicación de escritorio [!DNL Experience Manager] para la comunicación HTTP utilizan una estricta aplicación SSL. Por lo tanto, puede haber casos en los que las conexiones SSL que se realizan correctamente mediante un explorador fallan con la aplicación de escritorio [!DNL Adobe Experience Manager]. Esto es bueno porque fomenta la configuración correcta de SSL y aumenta la seguridad, pero puede resultar frustrante cuando la aplicación no puede conectarse.

El enfoque recomendado en este caso es utilizar una herramienta para analizar el certificado SSL de un servidor e identificar los problemas para que se puedan corregir. Hay sitios web que inspeccionan el certificado de un servidor al proporcionar su URL.

Como medida temporal, es posible deshabilitar la aplicación estricta de SSL en la aplicación de escritorio [!DNL Adobe Experience Manager]. Esta no es una solución recomendada a largo plazo, ya que reduce la seguridad al ocultar la causa raíz de SSL configurado incorrectamente. Para desactivar la aplicación estricta:

1. Utilice el editor de su elección para editar el archivo de configuración de JavaScript de la aplicación, que se encuentra (de forma predeterminada) en las siguientes ubicaciones (según el sistema operativo):

   En Mac: `/Applications/Adobe Experience Manager Desktop.app/Contents/Resources/javascript/lib-smb/config.json`

   En Windows: `C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop\javascript\config.json`

1. Busque la siguiente sección en el archivo :

   ```shell
   ...
   "assetRepository": {
       "options": {
   ...
   ```

1. Modifique la sección agregando `"strictSSL": false` de la siguiente manera:

   ```shell
   ...
   "assetRepository": {
       "options": {
           "strictSSL": false,
   ...
   ```

1. Guarde el archivo y reinicie la aplicación de escritorio [!DNL Adobe Experience Manager].

### La aplicación no responde {#unresponsive}

Raramente la aplicación puede no responder, mostrar solo una pantalla en blanco o mostrar un error en la parte inferior de la interfaz sin ninguna opción en la interfaz. Pruebe lo siguiente en el orden siguiente:

* Haga clic con el botón derecho en la interfaz de aplicación y haga clic en **[!UICONTROL Refresh]**.
* Salga de la aplicación y ábrala de nuevo.

En ambos métodos, la aplicación se inicia en la carpeta raíz DAM.

<!--
### Need additional help with [!DNL Experience Manager] desktop app {#additional-help}

Create Jira ticket with the following information:

* Use `DAM - Companion App` as the [!UICONTROL Component].

* Detailed steps to reproduce the issue in [!UICONTROL Description].

* DEBUG level logs that were captured while reproducing the issue.

* Target Experience Manager version.

* Operating system version.

* [!DNL Adobe Experience Manager] desktop app version. To know your app version, see [finding the desktop app version](#know-app-version-v2).
-->

>[!MORELIKETHIS]
>
>* [Problemas conocidos](release-notes.md#known-issues-v2)
>* [Evitar conflictos de edición](using.md#adv-workflow-collaborate-avoid-conflicts)

