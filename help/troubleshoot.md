---
title: Prácticas recomendadas para la aplicación de escritorio de Adobe Experience Manager y resolución de problemas
description: Siga las prácticas recomendadas y resuelva los problemas ocasionales relacionados con la instalación, actualización, configuración, etc.
uuid: ce98a3e7-5454-41be-aaaa-4252b3e0f8dd
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.5/ASSETS, SG_EXPERIENCEMANAGER/6.4/ASSETS, SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f5eb222a-6cdf-4ae3-9cf2-755c873f397c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2893fc1f8aad02e1436a1a281a320e6837487220
workflow-type: tm+mt
source-wordcount: '2171'
ht-degree: 0%

---


# Solución de problemas de la aplicación de escritorio de Adobe Experience Manager {#troubleshoot-v2}

La aplicación de escritorio de Adobe Experience Manager se conecta al repositorio de Digital Asset Management (DAM) de la implementación de un Experience Manager remoto. La aplicación obtiene información del repositorio y resultados de búsqueda en el equipo, descarga y carga archivos y carpetas, e incluye funciones para gestionar conflictos con la interfaz de usuario de Recursos.

Siga leyendo para solucionar problemas de la aplicación, conozca las prácticas recomendadas y descubra las limitaciones.

## Prácticas recomendadas {#best-practices-to-prevent-troubles}

Siga las siguientes optimizaciones para evitar problemas comunes y solucionar problemas.

* **Comprenda cómo funciona** la aplicación de escritorio: Antes de empezar a usar la aplicación, dedique unos minutos a saber cómo funciona. Obtenga información sobre la vinculación entre la interfaz web Experience Manager y el escritorio, la asignación de repositorios, el almacenamiento en caché de recursos, el almacenamiento local y la carga en segundo plano. Consulte [cómo funciona](release-notes.md#how-app-works).

* **Evite los caracteres no admitidos en los nombres** de carpetas: No utilice espacios en blanco ni caracteres no válidos al crear o cargar carpetas. Consulte una lista de caracteres en [Crear carpetas en Recursos Experience Manager](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html#creating-folders). Algunos casos de uso de Adobe Experience Manager pueden verse afectados por caracteres no admitidos en el nombre de la carpeta.

* **Prácticas recomendadas para evitar conflictos**: Para evitar conflictos potenciales al colaborar en varios recursos, consulte  [Evitar conflictos](using.md#adv-workflow-collaborate-avoid-conflicts) de edición.

* **Utilice la carga de carpetas para carpetas** grandes y jerárquicas: En lugar de utilizar la interfaz web de Recursos u otros métodos, utilice la aplicación de escritorio de Experience Manager para cargar carpetas grandes. La aplicación carga los recursos en segundo plano con el registro y la supervisión. Consulte [carga masiva de recursos](using.md#bulk-upload-assets).

* **Utilice la versión** más reciente: Utilice la versión más reciente de la aplicación y compruebe siempre la compatibilidad antes de instalar una nueva versión de la aplicación o antes de actualizar a una versión más reciente de Adobe Experience Manager. Consulte [notas de la versión](release-notes.md).

* **Utilice la misma letra** de unidad: Utilice la misma letra de unidad en una organización para asignarla a Adobe Experience Manager DAM. Para ver los recursos colocados por otros usuarios, las rutas deben ser las mismas. El uso de la misma letra de unidad garantiza una ruta constante a los recursos DAM. Los recursos permanecen colocados y no se eliminan incluso si distintos usuarios utilizan distintas letras de unidad.

* **Tenga en cuenta la red**: El rendimiento de la red es fundamental para el rendimiento de la aplicación de escritorio Experience Manager. Si se enfrenta a una respuesta lenta a las transferencias de archivos o a las operaciones masivas, desactive las funciones o aplicaciones que pueden causar mucho tráfico en la red.

* **Casos de uso no admitidos para la aplicación** de escritorio: No utilice la aplicación para la migración de recursos (necesita planificación y otras herramientas); para operaciones DAM de gran capacidad (como mover carpetas grandes, cargas grandes, buscar archivos mediante búsquedas avanzadas de metadatos); y como cliente de sincronización (los principios de diseño y los patrones de uso son diferentes de los clientes en sincronización como la sincronización de escritorio de Microsoft OneDrive o Adobe Creative Cloud).

* **Tiempo de espera**: Actualmente, la aplicación de escritorio no tiene un valor de tiempo de espera configurable que desconecte la conexión entre el servidor Experience Manager y la aplicación de escritorio después de un intervalo de tiempo fijo. Cuando se cargan recursos de gran tamaño, si la conexión se agota después de un tiempo, la aplicación tiene el reintentos de cargar el recurso varias veces aumentando el tiempo de espera de carga. No se recomienda cambiar la configuración de tiempo de espera predeterminada.

## Cómo solucionar problemas {#troubleshooting-prep}

Para solucionar problemas de aplicaciones de escritorio, tenga en cuenta la siguiente información. Además, le prepara para transmitir mejor los problemas al Servicio de atención al cliente de Adobe si decide solicitar asistencia.

### Ubicación de los archivos de registro {#check-log-files-v2}

[!DNL Experience Manager] la aplicación de escritorio almacena sus archivos de registro en las siguientes ubicaciones según el sistema operativo:

En Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`

En Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

Al cargar muchos recursos, si algunos archivos no se pueden cargar, consulte `backend.log` archivo para identificar las cargas fallidas.

>[!NOTE]
>
>Cuando trabaje con el Servicio de atención al cliente de Adobe en una solicitud de asistencia o un ticket, se le puede pedir que comparta los archivos de registro para ayudar al equipo de atención al cliente a comprender el problema. Archive toda la carpeta `Logs` y compártala con el contacto del Servicio de atención al cliente.

### Cambiar el nivel de detalles en los archivos de registro {#level-of-details-in-log}

Para cambiar el nivel de detalles en los archivos de registro:

1. Asegúrese de que la aplicación no se esté ejecutando.

1. En el sistema Windows:

   1. Abra una ventana de comandos.

   1. Inicie la aplicación de escritorio [!DNL Adobe Experience Manager] ejecutando el comando:

   ```shell
   set AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe
   ```

   En el sistema Mac:

   1. Abra una ventana de terminal.

   1. Inicie la aplicación de escritorio [!DNL Adobe Experience Manager] ejecutando el comando:

   ```shell
   AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app
   ```

Los niveles de registro válidos son DEBUG, INFO, WARN o ERROR. La gran cantidad de registros es mayor en DEBUG y menor en ERROR.

### Habilitar modo de depuración {#enable-debug-mode}

Para solucionar problemas, puede habilitar el modo de depuración y obtener más información en los registros.

>[!NOTE]
>
>Los niveles de registro válidos son DEBUG, INFO, WARN o ERROR. La gran cantidad de registros es mayor en DEBUG y menor en ERROR.

Para utilizar la aplicación en modo de depuración en Mac:

1. Abra una ventana de terminal o un símbolo del sistema.

1. Inicie la aplicación de escritorio [!DNL Experience Manager] ejecutando el siguiente comando:

   `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`.

Para habilitar el modo de depuración en Windows:

1. Abra una ventana de comandos.

1. Inicie la aplicación de escritorio [!DNL Experience Manager] ejecutando el siguiente comando:

`AEM_DESKTOP_LOG_LEVEL=DEBUG&"C:\Program Files\Adobe\Adobe Experience Manager Desktop.exe`.

### Borrar caché {#clear-cache-v2}

Siga estos pasos:

1. Inicio la aplicación y conecte una instancia de Experience Manager.

1. Para abrir las preferencias de la aplicación, haga clic en las elipses en la esquina superior derecha y seleccione [!UICONTROL Preferences].

1. Busque la entrada que muestra [!UICONTROL Current Cache Size]. Haga clic en el icono de papelera situado junto a este elemento.

Para borrar manualmente la caché, siga los pasos a continuación.

>[!CAUTION]
>
>Se trata de una operación potencialmente destructiva. Si hay cambios en los archivos locales que no se cargan en [!DNL Adobe Experience Manager], esos cambios se perderán si continúa.

La caché se borra eliminando el directorio de caché de la aplicación, que se encuentra en las preferencias de la aplicación.

1. Inicio la aplicación.

1. Para abrir las preferencias de la aplicación, seleccione las elipses en la esquina superior derecha y seleccione [!UICONTROL Preferences].

1. Observe el valor [!UICONTROL Cache Directory].

   En este directorio hay subdirectorios con el nombre de los extremos [!DNL Adobe Experience Manager] codificados. Los nombres son una versión codificada de la dirección URL de destino [!DNL Adobe Experience Manager]. Por ejemplo, si la aplicación está dirigiendo `localhost:4502`, el nombre del directorio será `localhost_4502`.

Para borrar la caché, elimine el directorio de extremo [!DNL Adobe Experience Manager] codificado que desee. Como alternativa, si se elimina el directorio completo especificado en las preferencias, se borrará la caché de todas las instancias que haya utilizado la aplicación.

La eliminación de la caché de la aplicación de escritorio [!DNL Adobe Experience Manager] es una tarea preliminar para la resolución de problemas que puede resolver varios problemas. Borre la caché de las preferencias de la aplicación. Consulte [establecer preferencias](install-upgrade.md#set-preferences). La ubicación predeterminada de la carpeta de caché es:

### Conozca la versión [!DNL Adobe Experience Manager] de la aplicación de escritorio {#know-app-version-v2}

Para ver el número de versión:

1. Inicio la aplicación.

1. Haga clic en las elipses en la esquina superior derecha, pase el ratón sobre [!UICONTROL Help] y haga clic en [!UICONTROL About].

   El número de versión aparece en esta pantalla.

### No se pueden ver los recursos colocados {#placed-assets-missing}

Si no puede ver los recursos que usted u otros profesionales creativos colocaron en los archivos de soporte (por ejemplo, archivos INDD), compruebe lo siguiente:

* Conexión al servidor. La conectividad de red deficiente puede detener las descargas de recursos.

* Tamaño de archivo. Los recursos grandes tardan más en descargarse y mostrarse.

* Consistencia de la letra de unidad. Si usted u otro colaborador colocó los recursos mientras asignaba el DAM Experience Manager a una letra de unidad diferente, no se muestran los recursos colocados.

* Permisos. Para comprobar si tiene permisos para recuperar los recursos colocados, póngase en contacto con el administrador del Experience Manager.

### Las ediciones realizadas en archivos de la interfaz de usuario de la aplicación de escritorio no se reflejan en [!DNL Adobe Experience Manager] inmediatamente {#changes-on-da-not-visible-on-aem}

[!DNL Adobe Experience Manager] la aplicación de escritorio deja al usuario la decisión de cuándo se completan todas las ediciones de un archivo. Según el tamaño y la complejidad de un archivo, lleva una cantidad considerable de tiempo transferir la nueva versión de un archivo a [!DNL Adobe Experience Manager]. El diseño de la aplicación requiere minimizar el número de veces que se transfiere un archivo de forma sucesiva, en lugar de adivinar cuándo se completan las ediciones del archivo y se cargan automáticamente. Se recomienda que el usuario inicie la transferencia del archivo nuevamente a [!DNL Adobe Experience Manager] mediante la opción de cargar los cambios de un archivo.

### Problemas al actualizar en macOS {#issues-when-upgrading-on-macos}

En ocasiones pueden producirse problemas al actualizar la aplicación de escritorio Experience Manager en macOS. Esto se debe a que la carpeta de sistema heredada de la aplicación de escritorio Experience Manager impide que las nuevas versiones de la aplicación de escritorio Experience Manager se carguen correctamente. Para solucionar este problema, se pueden quitar manualmente las siguientes carpetas y archivos.

Antes de ejecutar los siguientes pasos, arrastre la aplicación `Adobe Experience Manager Desktop` de la carpeta Aplicaciones macOS a la papelera. A continuación, abra terminal, ejecute el siguiente comando y proporcione su contraseña cuando se le solicite.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

### No se pueden cargar archivos {#upload-fails}

Si utiliza una aplicación de escritorio con Experience Manager 6.5.1 o posterior, actualice el conector S3 o Azure a la versión 1.10.4 o posterior. Resuelve el problema de error de carga de archivos relacionado con [OAK-8599](https://issues.apache.org/jira/browse/OAK-8599). Consulte [instrucciones de instalación](install-upgrade.md#install-v2).

### [!DNL Experience Manager] problemas de conexión de la aplicación de escritorio  {#connection-issues}

Si tiene problemas generales de conectividad, puede obtener más información sobre la [!DNL Experience Manager] aplicación de escritorio.

**Compruebe el registro de solicitudes**

[!DNL Experience Manager] la aplicación de escritorio registra todas las solicitudes que envía, junto con el código de respuesta de cada solicitud, en un archivo de registro dedicado.

1. Abra `request.log` en el directorio de registro de la aplicación para ver estas solicitudes.

1. Cada línea del registro representa una solicitud o una respuesta. Las solicitudes tendrán un carácter `>` seguido de la dirección URL solicitada. Las respuestas tendrán un carácter `<` seguido del código de respuesta y la dirección URL solicitada. Las solicitudes y la respuesta se pueden hacer coincidir utilizando el GUID de cada línea.

**Verificar solicitudes cargadas por el explorador incrustado de la aplicación**

La mayoría de las solicitudes de la aplicación se encuentran en el registro de solicitudes. Sin embargo, si no hay información útil allí, puede resultar útil examinar las solicitudes enviadas por el explorador integrado de la aplicación.
Consulte la [sección SAML](#da-connection-issue-with-saml-aem) para obtener instrucciones sobre cómo vista de dichas solicitudes.

#### La autenticación de inicio de sesión SAML no funciona {#da-connection-issue-with-saml-aem}

Si la aplicación de escritorio [!DNL Experience Manager] no se conecta a la instancia de [!DNL Adobe Experience Manager] habilitada para SSO (SAML), lea esta sección para solucionar problemas. Los procesos de SSO son variados, a veces complejos, y el diseño de la aplicación hace todo lo posible para dar cabida a estos tipos de conexiones. Sin embargo, algunas configuraciones requieren resolución de problemas adicional.

A veces, el proceso SAML no redirige a la ruta solicitada originalmente o la redirección final es a un host distinto al configurado en la aplicación de escritorio [!DNL Adobe Experience Manager]. Para verificar que no sea así:

1. Abra un navegador web. Acceda a la dirección URL `https://[aem_server]:[port]/content/dam.json`.

1. Inicie sesión en la implementación [!DNL Adobe Experience Manager].

1. Cuando el inicio de sesión se haya completado, observe la dirección actual del explorador en la barra de direcciones. Debe coincidir exactamente con la dirección URL introducida inicialmente.

1. Compruebe también que todo lo anterior a `/content/dam.json` coincide con el valor de destinatario [!DNL Adobe Experience Manager] configurado en la configuración de la aplicación de escritorio [!DNL Adobe Experience Manager].

**El proceso SAML de inicio de sesión funciona correctamente según los pasos anteriores, pero los usuarios siguen sin poder iniciar sesión**

La ventana dentro de la aplicación de escritorio [!DNL Adobe Experience Manager] que muestra el proceso de inicio de sesión es simplemente un navegador web que muestra la interfaz de usuario web de la instancia de destinatario [!DNL Adobe Experience Manager]:

* La versión de Mac utiliza [WebView](https://developer.apple.com/documentation/webkit/webview).

* La versión de Windows utiliza Chrome basado en [CefSharp](https://cefsharp.github.io/).

Asegúrese de que el proceso SAML sea compatible con esos exploradores.

Para solucionar problemas adicionales, es posible realizar la vista de las direcciones URL exactas que el explorador intenta cargar. Para ver esta información:

1. Siga las instrucciones para iniciar la aplicación en [modo de depuración](#enable-debug-mode).

1. Vuelva a producir el intento de inicio de sesión.

1. Vaya al [directorio de registro](#check-log-files-v2) de la aplicación

1. Para Windows:

   1. Abra &quot;aemcompanionlog.txt&quot;.

   1. Busque mensajes que comiencen con &quot;La dirección del navegador de inicio de sesión ha cambiado a&quot;. Estas entradas también contienen la dirección URL que cargó la aplicación.

   Para Mac:

   1. `com.adobe.aem.desktop-nnnnnnnn-nnnnnn.log`, donde el  **** número se reemplaza por los números que se encuentren en el nombre de archivo más reciente.

   1. Busque mensajes que comiencen con &quot;marco cargado&quot;. Estas entradas también contienen la dirección URL que cargó la aplicación.


El observar la secuencia de URL que se está cargando puede ayudar a solucionar problemas al final de SAML para determinar qué es lo que está mal.

#### Problema de configuración SSL {#ssl-config-v2}

Las bibliotecas que utiliza la aplicación de escritorio de Experience Manager para la comunicación HTTP utilizan una estricta aplicación SSL. A veces, una conexión puede funcionar correctamente con un navegador, pero falla al usar la aplicación de escritorio Experience Manager. Para configurar SSL correctamente, instale el certificado intermedio que falta en Apache. Consulte [Cómo instalar un certificado de CA intermedio en Apache](https://access.redhat.com/solutions/43575).

Las bibliotecas que Experience Manager Desktop utiliza para la comunicación HTTP utilizan una estricta aplicación SSL. Por lo tanto, puede haber casos en los que las conexiones SSL que se ejecutan con éxito a través de un explorador fallan con la aplicación de escritorio [!DNL Adobe Experience Manager]. Esto es bueno porque fomenta la configuración correcta de SSL y aumenta la seguridad, pero puede resultar frustrante cuando la aplicación no puede conectarse.

El método recomendado en este caso es utilizar una herramienta para analizar el certificado SSL de un servidor e identificar problemas para que se puedan corregir. Hay sitios web que inspeccionan el certificado de un servidor al proporcionar su dirección URL.

Como medida temporal, es posible deshabilitar la estricta aplicación SSL en la aplicación de escritorio [!DNL Adobe Experience Manager]. Esta no es una solución recomendada a largo plazo, ya que reduce la seguridad al ocultar la causa raíz de una SSL configurada incorrectamente. Para deshabilitar la aplicación estricta:

1. Utilice el editor de su elección para editar el archivo de configuración JavaScript de la aplicación, que se encuentra (de forma predeterminada) en las siguientes ubicaciones (según el sistema operativo):

   En Mac: `/Applications/Adobe Experience Manager Desktop.app/Contents/Resources/javascript/lib-smb/config.json`

   En Windows: `C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop\javascript\config.json`

1. Busque la siguiente sección en el archivo:

   ```shell
   ...
   "assetRepository": {
       "options": {
   ...
   ```

1. Modifique la sección agregando `"strictSSL": false` como se indica a continuación:

   ```shell
   ...
   "assetRepository": {
       "options": {
           "strictSSL": false,
   ...
   ```

1. Guarde el archivo y reinicie la aplicación de escritorio [!DNL Adobe Experience Manager].

### La aplicación no responde {#unresponsive}

Raramente la aplicación puede no responder, mostrar solo una pantalla en blanco o mostrar un error en la parte inferior de la interfaz sin ninguna opción en la interfaz. Pruebe lo siguiente en el orden:

* Haga clic con el botón derecho en la interfaz de la aplicación y haga clic en **[!UICONTROL Refresh]**.
* Salga de la aplicación y ábrala de nuevo.

En ambos métodos, la aplicación inicio en la carpeta DAM raíz.

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

