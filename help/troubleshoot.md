---
title: Prácticas recomendadas para y solución de problemas [!DNL Adobe Experience Manager] aplicación de escritorio
description: Siga las prácticas recomendadas y solucione problemas para resolver los problemas ocasionales relacionados con la instalación, actualización, configuración, etc.
exl-id: f388e4ac-907d-4093-ba6f-86ecdafeb015
source-git-commit: 2c846fb9cd82691f6439e93429dffcca8127ba68
workflow-type: tm+mt
source-wordcount: '2260'
ht-degree: 0%

---

# Solucionar problemas [!DNL Adobe Experience Manager] aplicación de escritorio {#troubleshoot-v2}

[!DNL Adobe Experience Manager] la aplicación de escritorio se conecta a un [!DNL Experience Manager] repositorio de administración de activos digitales (DAM) de la implementación. La aplicación recupera información del repositorio y resultados de búsqueda en el equipo, descarga y carga archivos y carpetas, e incluye funciones para administrar conflictos con la interfaz de usuario de Assets.

Siga leyendo para solucionar los problemas de la aplicación, conocer las prácticas recomendadas y averiguar las limitaciones.

## Prácticas recomendadas {#best-practices-to-prevent-troubles}

Siga las siguientes prácticas recomendadas para evitar algunos problemas comunes y solucionar problemas.

* **Comprender cómo funciona la aplicación de escritorio**: Antes de empezar a usar la aplicación, dedique unos minutos a conocer su funcionamiento. Obtenga información sobre la vinculación entre [!DNL Experience Manager] interfaz web y escritorio, asignación de repositorios, almacenamiento en caché de recursos, almacenamiento local y carga en segundo plano. Consulte [cómo funciona](release-notes.md#how-app-works).

* **Evite los caracteres no admitidos en los nombres de carpeta**: No utilice espacios en blanco ni caracteres no válidos al crear o cargar carpetas. Consulte una lista de caracteres en [Creación de carpetas en [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#creating-folders). Algunos [!DNL Experience Manager] Los casos de uso de pueden verse afectados por caracteres no admitidos en el nombre de la carpeta.

* **Prácticas recomendadas para evitar conflictos**: Para evitar posibles conflictos al colaborar en varios recursos, consulte [evitar conflictos de edición](using.md#adv-workflow-collaborate-avoid-conflicts).

* **Usar la carga de carpetas para carpetas grandes y jerárquicas**: En lugar de utilizar la interfaz web de Assets u otros métodos, utilice [!DNL Experience Manager] aplicación de escritorio para cargar carpetas grandes. La aplicación carga los recursos en segundo plano mediante el registro y la monitorización. Consulte [carga masiva de recursos](using.md#bulk-upload-assets).

* **Utilizar la versión más reciente**: utilice la versión más reciente de la aplicación y compruebe siempre la compatibilidad antes de instalar una nueva versión de la aplicación o antes de actualizar a una más reciente [!DNL Experience Manager] versión. Consulte [notas de la versión](release-notes.md).

* **Usar la misma letra de unidad**: utilice la misma letra de unidad en toda la organización para asignarla a [!DNL Experience Manager] DAM. Para ver los recursos colocados por otros usuarios, las rutas deben ser las mismas. El uso de la misma letra de unidad garantiza una ruta constante a los recursos DAM. Los recursos permanecen colocados y no se eliminan aunque distintos usuarios utilicen letras de unidad distintas.

* **Cuidado con la red**: el rendimiento de la red es fundamental para [!DNL Experience Manager] rendimiento de la aplicación de escritorio. Si se enfrenta a una respuesta lenta a las transferencias de archivos o a las operaciones masivas, desactive las funciones o aplicaciones que puedan causar mucho tráfico de red.

* **Casos de uso no admitidos para la aplicación de escritorio**: no utilice la aplicación para la migración de recursos (necesita herramientas de planificación y de otro tipo); para operaciones de DAM de gran capacidad (como mover carpetas grandes, cargas grandes, buscar archivos mediante búsquedas avanzadas de metadatos) y como cliente de sincronización (los principios de diseño y los patrones de uso son diferentes de los clientes de sincronización como Microsoft OneDrive o Adobe Creative Cloud Desktop Sync).

* **Tiempo de espera**: Actualmente, la aplicación de escritorio no tiene un valor de tiempo de espera configurable que desconecte la conexión entre [!DNL Experience Manager] servidor y aplicación de escritorio después de un intervalo de tiempo fijo. Al cargar recursos de gran tamaño, si la conexión supera el tiempo de espera después de un tiempo, la aplicación vuelve a intentar cargar el recurso varias veces aumentando el tiempo de espera de carga. No se recomienda ninguna forma de cambiar la configuración de tiempo de espera predeterminada.

## Cómo solucionar problemas {#troubleshooting-prep}

Para solucionar problemas de la aplicación de escritorio, tenga en cuenta la siguiente información. Además, le prepara para transmitir mejor los problemas al Servicio de atención al cliente de Adobe si elige buscar asistencia.

### Ubicación de los archivos de registro {#check-log-files-v2}

[!DNL Experience Manager] La aplicación de escritorio almacena sus archivos de registro en las siguientes ubicaciones, según el sistema operativo:

En Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`

En Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

Al cargar muchos recursos, si algunos archivos no se pueden cargar, consulte `backend.log` para identificar las cargas fallidas.

>[!NOTE]
>
>Al trabajar con Asistencia al cliente de Adobe en una solicitud de soporte o un ticket, se le puede pedir que comparta los archivos de registro para ayudar al equipo de Asistencia al cliente a comprender el problema. Archivar todo el `Logs` y compártala con tu contacto de Atención al cliente.

### Cambiar el nivel de detalles en los archivos de registro {#level-of-details-in-log}

Para cambiar el nivel de detalles en los archivos de registro:

1. Asegúrese de que la aplicación no se esté ejecutando.

1. En el sistema Windows:

   1. Abra una ventana de comandos.

   1. Launch [!DNL Adobe Experience Manager] aplicación de escritorio ejecutando el comando:

   ```shell
   set AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe
   ```

   En el sistema Mac:

   1. Abra una ventana de terminal.

   1. Launch [!DNL Adobe Experience Manager] aplicación de escritorio ejecutando el comando:

   ```shell
   AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app
   ```

Los niveles de registro válidos son DEBUG, INFO, WARN o ERROR. El nivel de detalle de los registros es mayor en DEPURACIÓN y menor en ERROR.

### Habilitar modo de depuración {#enable-debug-mode}

Para solucionar problemas, puede habilitar el modo de depuración y obtener más información en los registros.

>[!NOTE]
>
>Los niveles de registro válidos son DEBUG, INFO, WARN o ERROR. El nivel de detalle de los registros es mayor en DEPURACIÓN y menor en ERROR.

Para usar la aplicación en modo de depuración en Mac:

1. Abra una ventana de terminal o un símbolo del sistema.

1. Inicie el [!DNL Experience Manager] aplicación de escritorio ejecutando el siguiente comando:

   `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`.

Para habilitar el modo de depuración en Windows:

1. Abra una ventana de comandos.

1. Launch [!DNL Experience Manager] aplicación de escritorio ejecutando el siguiente comando:

`AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe`.

### Conozca los [!DNL Adobe Experience Manager] versión de aplicación de escritorio {#know-app-version-v2}

Para ver el número de versión:

1. Inicie la aplicación.

1. Haga clic en los puntos suspensivos en la esquina superior derecha, pase el ratón sobre [!UICONTROL Help], luego haga clic en [!UICONTROL About].

   El número de versión aparece en esta pantalla.

### Borrar caché {#clear-cache-v2}

Siga estos pasos:

1. Inicie la aplicación y conéctese a un [!DNL Experience Manager] ejemplo.

1. Abra las preferencias de la aplicación haciendo clic en los puntos suspensivos de la esquina superior derecha y seleccionando [!UICONTROL Preferences].

1. Busque la entrada que muestra el [!UICONTROL Current Cache Size]. Haga clic en el icono de papelera situado junto a este elemento.

Para borrar manualmente la caché, siga los pasos a continuación.

>[!CAUTION]
>
>Esta es una operación potencialmente destructiva. Si hay cambios en el archivo local que no se cargan en [!DNL Adobe Experience Manager], esos cambios se perderán al continuar.

La caché se borra eliminando el directorio de caché de la aplicación, que se encuentra en las preferencias de la aplicación.

1. Inicie la aplicación.

1. Abra las preferencias de la aplicación seleccionando los puntos suspensivos en la esquina superior derecha y seleccionando [!UICONTROL Preferences].

1. Tenga en cuenta [!UICONTROL Cache Directory] valor.

   En este directorio hay subdirectorios con nombre después de la variable Codificado [!DNL Adobe Experience Manager] Extremos. Los nombres son una versión codificada del objeto [!DNL Adobe Experience Manager] URL. Por ejemplo, si la aplicación tiene como objetivo `localhost:4502` entonces el nombre del directorio será `localhost_4502`.

Para borrar la caché, elimine la codificación deseada [!DNL Adobe Experience Manager] Directorio de extremo. Como alternativa, si se elimina todo el directorio especificado en las preferencias, se borrará la caché de todas las instancias que haya utilizado la aplicación.

Borrado [!DNL Adobe Experience Manager] la caché de la aplicación de escritorio es una tarea preliminar de resolución de problemas que puede resolver varios problemas. Borre la caché de las preferencias de la aplicación. Consulte [establecer preferencias](install-upgrade.md#set-preferences). La ubicación predeterminada de la carpeta de caché es:

## No se pueden ver los recursos colocados {#placed-assets-missing}

Si no puede ver los recursos que usted u otros profesionales creativos han colocado en los archivos de soporte (por ejemplo, archivos INDD), compruebe lo siguiente:

* Conexión al servidor. La conectividad de red débil puede detener las descargas de recursos.

* Tamaño de archivo. Los recursos grandes tardan más en descargarse y mostrarse.

* Impulse la coherencia de letras. Si usted u otro colaborador han colocado los recursos al asignar el [!DNL Experience Manager] DAM a una letra de unidad diferente, los recursos colocados no se muestran.

* Permisos. Para comprobar si tiene permisos para recuperar los recursos colocados, póngase en contacto con su [!DNL Experience Manager] administrador.

### Las ediciones hechas en archivos en la interfaz de usuario de la aplicación de escritorio no se reflejan en [!DNL Adobe Experience Manager] inmediatamente {#changes-on-da-not-visible-on-aem}

[!DNL Adobe Experience Manager] La aplicación de escritorio deja al usuario la decisión de cuándo se completan todas las ediciones de un archivo. En función del tamaño y la complejidad de un archivo, se tarda una cantidad de tiempo considerable en volver a transferir la nueva versión de un archivo a [!DNL Adobe Experience Manager]. El diseño de la aplicación exige minimizar el número de veces que un archivo se transfiere de un lado a otro, en lugar de suponer cuándo se han completado las ediciones del archivo y se cargan automáticamente. Se aconseja que el usuario inicie la transferencia del archivo de nuevo a [!DNL Adobe Experience Manager] al elegir cargar los cambios de un archivo.

### Problemas al actualizar en macOS {#issues-when-upgrading-on-macos}

Ocasionalmente pueden producirse problemas al actualizar [!DNL Experience Manager] aplicación de escritorio en macOS. Esto se debe a la carpeta heredada del sistema para [!DNL Experience Manager] aplicación de escritorio que evita nuevas versiones de [!DNL Experience Manager] aplicación de escritorio para cargarse correctamente. Para solucionar este problema, se pueden eliminar manualmente las siguientes carpetas y archivos.

Antes de ejecutar los pasos siguientes, arrastre el `Adobe Experience Manager Desktop` de la carpeta Aplicaciones macOS a la papelera. A continuación, abra terminal, ejecute el siguiente comando y proporcione la contraseña cuando se le solicite.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## No se pueden cargar archivos {#upload-fails}

Si utiliza la aplicación de escritorio con [!DNL Experience Manager] 6.5.1 o posterior, actualice el conector S3 o Azure a la versión 1.10.4 o posterior. Resuelve el problema de error de carga de archivo relacionado con [OAK-8599](https://issues.apache.org/jira/browse/OAK-8599). Consulte [instrucciones de instalación](install-upgrade.md#install-v2).

## [!DNL Experience Manager] problemas de conexión de aplicación de escritorio {#connection-issues}

Si tiene problemas generales de conectividad, aquí hay algunas formas de obtener más información acerca de lo que [!DNL Experience Manager] la aplicación de escritorio está funcionando.

**Comprobación del registro de solicitudes**

[!DNL Experience Manager] la aplicación de escritorio registra todas las solicitudes que envía, junto con el código de respuesta de cada solicitud, en un archivo de registro dedicado.

1. Abrir `request.log` en el directorio log de la aplicación para ver estas solicitudes.

1. Cada línea del registro representa una solicitud o una respuesta. Las solicitudes tendrán un `>` seguido de la dirección URL solicitada. Las respuestas tendrán un `<` seguido del código de respuesta y de la dirección URL solicitada. Las solicitudes y las respuestas pueden coincidir utilizando el GUID de cada línea.

**Compruebe las solicitudes cargadas por el explorador incrustado de la aplicación**

La mayoría de las solicitudes de la aplicación se encuentran en el registro de solicitudes. Sin embargo, si no hay información útil allí, puede resultar útil examinar las solicitudes enviadas por el explorador incrustado de la aplicación.
Consulte la [Sección SAML](#da-connection-issue-with-saml-aem) para obtener instrucciones sobre cómo ver esas solicitudes.

### La autenticación de inicio de sesión SAML no funciona {#da-connection-issue-with-saml-aem}

[!DNL Experience Manager] Es posible que la aplicación de escritorio no se conecte a su aplicación con SSO habilitado (SAML) [!DNL Adobe Experience Manager] implementación. El diseño de la aplicación intenta adaptarse a las variaciones y complejidades de las conexiones y procesos de SSO. Sin embargo, una configuración puede requerir una solución de problemas adicional.

A veces, el proceso de SAML no redirige de nuevo a la ruta solicitada originalmente, o el redireccionamiento final es a un host diferente de lo configurado en [!DNL Adobe Experience Manager] aplicación de escritorio. Para comprobar que no es así:

1. Abra un navegador web. Acceso `https://[aem_server]:[port]/content/dam.json` URL.

1. Inicie sesión en [!DNL Adobe Experience Manager] implementación.

1. Cuando finalice el inicio de sesión, observe la dirección actual del explorador en la barra de direcciones. Debe coincidir exactamente con la dirección URL introducida inicialmente.

1. Compruebe también que todo lo anterior a `/content/dam.json` coincide con el destino [!DNL Adobe Experience Manager] valor configurado en [!DNL Adobe Experience Manager] configuración de la aplicación de escritorio.

**El proceso de inicio de sesión de SAML funciona correctamente según los pasos anteriores, pero los usuarios siguen sin poder iniciar sesión**

La ventana dentro de [!DNL Adobe Experience Manager] La aplicación de escritorio que muestra el proceso de inicio de sesión es simplemente un explorador web que muestra el destinatario [!DNL Adobe Experience Manager] interfaz de usuario web de la instancia:

* La versión de Mac utiliza un [WebView](https://developer.apple.com/documentation/webkit/webview).

* La versión de Windows utiliza una versión basada en Chromium [CefSharp](https://cefsharp.github.io/).

Asegúrese de que el proceso de SAML sea compatible con esos exploradores.

Para solucionar más problemas, es posible ver las direcciones URL exactas que el explorador está intentando cargar. Para ver esta información:

1. Siga las instrucciones para iniciar la aplicación en [modo de depuración](#enable-debug-mode).

1. Reproduzca el intento de inicio de sesión.

1. Vaya a [directorio de registro](#check-log-files-v2) de la aplicación

1. Para Windows:

   1. Abra &quot;aemcompanionlog.txt&quot;.

   1. Busque mensajes que comiencen por &quot;La dirección del navegador de inicio de sesión cambió a&quot;. Estas entradas también contienen la dirección URL que cargó la aplicación.

   Para Mac:

   1. `com.adobe.aem.desktop-nnnnnnnn-nnnnnn.log`, donde la variable **n** se sustituyen por los números que estén en el nombre de archivo más reciente.

   1. Busque mensajes que comiencen por &quot;marco cargado&quot;. Estas entradas también contienen la dirección URL que cargó la aplicación.


Mirar la secuencia de URL que se está cargando puede ayudar a solucionar el problema al final de SAML para determinar qué está mal.

### Problema de configuración SSL {#ssl-config-v2}

Las bibliotecas que [!DNL Experience Manager] La aplicación de escritorio de utiliza para la comunicación HTTP utiliza una estricta aplicación SSL. A veces, una conexión puede realizarse correctamente mediante un explorador, pero falla al utilizar [!DNL Experience Manager] aplicación de escritorio. Para configurar SSL correctamente, instale el certificado intermedio que falta en Apache. Consulte [Cómo instalar un certificado de CA intermedia en Apache](https://access.redhat.com/solutions/43575).

Las bibliotecas que [!DNL Experience Manager] La aplicación de escritorio de utiliza para la comunicación HTTP la aplicación estricta de SSL. Por lo tanto, puede haber casos en los que las conexiones SSL que se realizan correctamente a través de un explorador fallen con [!DNL Adobe Experience Manager] aplicación de escritorio. Esto es bueno porque fomenta la configuración correcta de SSL y aumenta la seguridad, pero puede ser frustrante cuando la aplicación no se puede conectar.

El método recomendado en este caso es utilizar una herramienta para analizar el certificado SSL de un servidor e identificar problemas para que se puedan corregir. Hay sitios web que inspeccionan el certificado de un servidor al proporcionar su dirección URL.

Como medida temporal, es posible desactivar la aplicación estricta de SSL en [!DNL Adobe Experience Manager] aplicación de escritorio. Esta no es una solución recomendada a largo plazo, ya que reduce la seguridad al ocultar la causa raíz de SSL configurado incorrectamente. Para deshabilitar la aplicación estricta:

1. Utilice el editor que desee para editar el archivo de configuración de JavaScript de la aplicación, que se encuentra (de forma predeterminada) en las siguientes ubicaciones (según el sistema operativo):

   En Mac: `/Applications/Adobe Experience Manager Desktop.app/Contents/Resources/javascript/lib-smb/config.json`

   En Windows: `C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop\javascript\config.json`

1. Busque la siguiente sección en el archivo:

   ```shell
   ...
   "assetRepository": {
       "options": {
   ...
   ```

1. Modifique la sección añadiendo `"strictSSL": false` como sigue:

   ```shell
   ...
   "assetRepository": {
       "options": {
           "strictSSL": false,
   ...
   ```

1. Guarde el archivo y reinicie [!DNL Adobe Experience Manager] aplicación de escritorio.

### Problemas de inicio de sesión al cambiar a un servidor diferente {#cannot-login-cookies-issue}

Después de usar un [!DNL Experience Manager] servidor, cuando intenta cambiar la conexión a un servidor diferente, puede encontrar problemas de inicio de sesión. Se debe a que las cookies antiguas interfieren con la nueva autenticación. Una opción del menú principal para [!UICONTROL Clear Cookies] ayuda. Cierre sesión en la aplicación y seleccione [!UICONTROL Clear Cookies] antes de proceder a la conexión.

![Borrar cookies al cambiar de servidor](assets/main_menu_logout_da2.png)

## La aplicación no responde {#unresponsive}

En raras ocasiones, la aplicación puede dejar de responder, mostrar solo una pantalla en blanco o mostrar un error en la parte inferior de la interfaz sin ninguna opción en la interfaz. Pruebe lo siguiente en el orden:

* Haga clic con el botón derecho en la interfaz de la aplicación y seleccione **[!UICONTROL Refresh]**.
* Salga de la aplicación y ábrala de nuevo.

En ambos métodos, la aplicación se inicia en la carpeta raíz DAM.

## Ocultar recursos caducados {#hide-expired-assets}

Al examinar los recursos desde [!DNL Experience Manager] interfaz de usuario, no se muestran los recursos caducados. Para evitar ver, buscar y recuperar recursos caducados al examinar recursos desde la aplicación de escritorio y Asset Link, los administradores pueden realizar la siguiente configuración. La configuración funciona para todos los usuarios, independientemente del privilegio de administrador.

* [Configuración en Experience Manager 6.5 para ocultar recursos caducados](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#hide-expired-assets-via-acp-api).
* [Configuración en el Experience Manager as a Cloud Service para ocultar recursos caducados](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/manage/manage-digital-assets.html#hide-expired-assets-via-acp-api).

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

