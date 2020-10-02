---
title: Instalar y configurar AEM versión 1.x de la aplicación de escritorio
description: Instale y configure AEM aplicación de escritorio versión 1.x para que funcione con los servidores de AEM Assets y asigne los recursos que desea montar como unidad en el escritorio.
uuid: 79bc9de9-5708-41f9-ac43-68c1fd2a2129
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.5/ASSETS, SG_EXPERIENCEMANAGER/6.4/ASSETS,SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f6365302-1690-4719-9b8c-035719422740
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ef87dc011297fda181a9a7643a261e8a42e35a8b
workflow-type: tm+mt
source-wordcount: '984'
ht-degree: 0%

---


# Instalar y configurar AEM aplicación de escritorio v1.x {#install-and-configure-aem-desktop-app}

Con la aplicación de escritorio AEM, los recursos de AEM son fácilmente accesibles en el escritorio local y se pueden utilizar en cualquier aplicación de escritorio. Los recursos se pueden mostrar fácilmente en Mac Finder o en el Explorador de Windows, abrirse en aplicaciones de escritorio y cambiarse localmente; los cambios se guardan en AEM al cargar y se crea una nueva versión en el repositorio.

Esta integración permite que diversas funciones de la organización gestionen los activos de forma centralizada en AEM Assets y accedan a ellos en el Creative Cloud y en otras aplicaciones, al tiempo que facilita el cumplimiento de los distintos estándares, incluida la marca.

Para utilizar AEM aplicación de escritorio,

* Asegúrese de que AEM aplicación de escritorio admite la versión AEM del servidor. Consulte la matriz [de](release-notes-of-v1.md#compatibilitymatrix)compatibilidad.

* Descargue e instale la aplicación.

* Pruebe la conexión con algunos recursos. Consulte [Acceso y apertura de recursos en el escritorio](use-app-v1.md#openondesktop).

## Requisitos del sistema, requisitos previos y vínculos de descarga {#system-requirements-prerequisites-and-download-links}

Para obtener información detallada, consulte las notas de la versión de la aplicación de escritorio de [AEM](release-notes-of-v1.md).

## Instalación y conexión de AEM aplicación de escritorio a AEM servidor {#install-and-connect-aem-desktop-app-to-aem-server}

Para obtener más información, consulte [Instalación y conexión de AEM aplicación de escritorio a AEM servidor](use-app-v1.md#installandconnect).

>[!NOTE]
>
>Solo se puede instalar una instancia de la aplicación de escritorio AEM y estar activa a la vez.

## Gestión de archivos {#file-handling}

Al cambiar un archivo desde una ubicación de recurso compartido de red montada por la aplicación de escritorio, los archivos se guardan en esa ubicación en dos fases. En la primera fase, un archivo se guarda localmente. Un usuario puede guardar el archivo y seguir trabajando en él sin esperar a que se complete la transferencia.

En la segunda fase, la aplicación de escritorio carga el archivo actualizado en AEM servidor tras un retraso predefinido (por ejemplo, 30 segundos). Esta operación se produce en segundo plano. Utilice la opción Estado del recurso de Vista para vista del estado de la operación de carga.

1. Cargue un recurso en AEM Assets.

1. Toque o haga clic en el icono de la aplicación de escritorio AEM de la barra de herramientas.

1. En el menú, seleccione la opción Estado del recurso de Vista.

1. En el cuadro de diálogo, revise el estado de la operación de carga.

>[!NOTE]
>
>AEM aplicación de escritorio puede gestionar recursos de hasta 40 GB.

## Conectar con una instancia de AEM detrás de un despachante {#connect-to-an-aem-instance-behind-a-dispatcher}

Los métodos de copiar y mover de la API de recursos requieren que se pasen a AEM los siguientes encabezados adicionales:

* X-Destination
* Profundidad X
* X-Overwrite

AEM escritorio se conecta a AEM con una dirección URL que incluye el puerto predeterminado. Por lo tanto, la `virtualhosts` configuración de la configuración del despachante debe incluir el número de puerto predeterminado. Para obtener más información sobre `virtualhosts` la configuración, consulte [Identificación de hosts](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#identifying-virtual-hosts-virtualhosts)virtuales.

Para obtener información adicional sobre cómo configurar el despachante para que pase por estos encabezados adicionales, consulte [Especificación de encabezados](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#specifying-the-http-headers-to-pass-through-clientheaders)HTTP.

### Compatibilidad con proxy {#proxy-support}

AEM aplicación de escritorio utiliza el proxy predefinido del sistema para conectarse a Internet a través de HTTPS. La aplicación solo se puede conectar mediante un proxy de red que no requiera autenticación adicional.

Si configura o modifica la configuración del servidor proxy para Windows (Opciones de Internet > Configuración de LAN), reinicie la aplicación de escritorio AEM para que los cambios surtan efecto.

>[!NOTE]
>
>La configuración de proxy solo se aplica cuando se inicio la aplicación de escritorio. Cierre y vuelva a iniciar la aplicación para que se apliquen los cambios.

Si el proxy requiere autenticación, el equipo de TI puede permitir que la URL de recursos de Experience Manager en la configuración del servidor proxy permita el paso del tráfico de la aplicación.

## Personalización del cuadro de diálogo Información del recurso {#customize-the-asset-info-dialog}

Puede personalizar el cuadro de diálogo Información de recurso superponiendo uno o ambos de estos componentes:

* La página de la interfaz de usuario Granite en `/libs/dam/gui/content/assets/moreinfo`.

* Componente HTL `/css/javascript` en `/libs/dam/gui/components/admin/moreinfo`.

El componente que se superponga dependerá de la naturaleza de la personalización. Para cambiar qué componentes se muestran como parte del cuadro de diálogo Información de recurso, superponga la página de interfaz de usuario Granite. Para cambiar el contenido HTML, CSS o JavaScript del cuadro de diálogo, superponga el componente HTL.

## Administrar caché {#manage-cache}

En Windows, la caché está en `%LOCALAPPDATA%\Adobe\AssetsCompanion\Cache\`, donde es una versión codificada del host de AEM configurado en la aplicación de escritorio. Por ejemplo, `http://localhost:4502` aparece como `http%3A%2F%2Flocalhost%3A4502%2F`.

En Mac OS X, hay un directorio similar en `~/Library/Group Containers/group.com.adobe.aem.desktop/cache`.

### Opción en la aplicación para administrar la caché {#in-app-option-to-manage-cache}

Puede controlar la cantidad de espacio en disco disponible para su almacenamiento en caché local. Los artefactos del servidor de AEM Assets se almacenan en caché localmente para una experiencia más fluida. Puede cambiar los valores predeterminados para adaptarlos a sus necesidades. Además, puede borrar la caché para recuperar todos los recursos de nuevo. Para establecer las opciones deseadas, haga clic en el icono de la aplicación y haga clic en **[!UICONTROL Advanced]** > **[!UICONTROL Manage Cache]**. ****

>[!NOTE]
>
>Cuando borra la caché, conserva los cambios no guardados. Los recursos que no estén protegidos en AEM servidor se conservan y no se eliminan.

### Cambiar la ubicación de la caché en Windows {#change-location-of-cache-on-windows}

La ubicación predeterminada de la caché para la aplicación de escritorio AEM es la siguiente:

* En Windows, `%LocalAppData%\Adobe\AssetsCompanion\Cache\EncodedAEMEndpoint`.

* En Mac, `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/EncodedAEMEndpoint`.

`EncodedAEMEndpoint` es AEM URL del extremo de AEM configurado de la aplicación de escritorio. El valor es una versión codificada de la dirección URL de destino del servidor de AEM. Por ejemplo, si la aplicación está segmentada `http://localhost:4502`, el nombre del directorio es `http%3A%2F%2Flocalhost%3A4502`. La ruta de Windows al directorio de la memoria caché en este ejemplo es `%LocalAppData%\Adobe\AssetsCompanion\Cache\http%3A%2F%2Flocalhost%3A4502`.

Para dirigir la aplicación a una carpeta o unidad diferente, edite el archivo de configuración de la aplicación.

1. Vaya al directorio de instalación de la aplicación. La ubicación predeterminada en Windows es `C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop`.

1. Edite el archivo Adobe Experience Manager Desktop.exe.config con un editor de texto.

   Se requieren privilegios de administrador para guardar los cambios en este archivo.

1. Busque la cadena &quot;ProxyCacheRoot&quot;. Verá que su valor se establece en la ubicación de la caché `%LocalAppData%\Adobe\AssetsCompanion\Cache`. Simplemente cambie este valor a cualquier ruta válida.

   >[!NOTE]
   >
   >La aplicación crea automáticamente un subdirectorio *&lt;Encoded AEM Endpoint>* . Este comportamiento no se puede configurar.

>[!MORELIKETHIS]
* [Introducción a la aplicación de escritorio de AEM](https://helpx.adobe.com/customer-care-office-hours/aem/desktop-app.html)
* [Uso de la aplicación de escritorio de AEM](use-app-v1.md)
* [Comprender el registro y la salida con AEM aplicación de escritorio](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/collaboration/checkin-checkout-technical-video-understand.html)
* [Uso de la aplicación de escritorio con AEM Assets](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/collaboration/checkin-checkout-technical-video-understand.html)
* [Solución de problemas de AEM aplicación de escritorio](troubleshoot-app-v1.md)

