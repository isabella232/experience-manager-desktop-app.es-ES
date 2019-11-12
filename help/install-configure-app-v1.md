---
title: Instalación y configuración de la versión 1.x de la aplicación de escritorio de AEM
seo-title: Instalación y configuración de la versión 1.x de la aplicación de escritorio de AEM
description: Instale y configure la versión 1.x de la aplicación de escritorio de AEM para que funcione con los servidores de AEM Assets y asigne los recursos que desea montar como unidad en el escritorio.
seo-description: Instale y configure la versión 1.x de la aplicación de escritorio de AEM para que funcione con los servidores de AEM Assets y asigne los recursos que desea montar como unidad en el escritorio.
uuid: 79bc9de9-5708-41f9-ac43-68c1fd2a2129
contentOwner: asgupta
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f6365302-1690-4719-9b8c-035719422740
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7ce29042aff6d4caea0e7b8a56673d4bfed03a45

---


# Instalación y configuración de la aplicación de escritorio de AEM v1.x {#install-and-configure-aem-desktop-app}

Instale y configure la aplicación de escritorio de AEM para que funcione con los servidores de AEM Assets y descargue los recursos en el sistema de archivos local. Para utilizar la aplicación de escritorio de AEM,

* Asegúrese de que la versión del servidor AEM sea compatible con la aplicación de escritorio AEM. Consulte la matriz [de](release-notes-of-v1.md#compatibilitymatrix)compatibilidad.
* Descargue e instale la aplicación.
* Pruebe la conexión con algunos recursos. Consulte [Acceso y apertura de recursos en el escritorio](use-app-v1.md#openondesktop).

## Requisitos del sistema, requisitos previos y vínculos de descarga {#system-requirements-prerequisites-and-download-links}

Para obtener información detallada, consulte las notas de la versión de la aplicación de escritorio de [AEM](release-notes-of-v1.md).

## Instalación y conexión de la aplicación de escritorio de AEM al servidor de AEM {#install-and-connect-aem-desktop-app-to-aem-server}

Para obtener más información, consulte [Instalación y conexión de la aplicación de escritorio de AEM al servidor](use-app-v1.md#installandconnect)AEM.

>[!NOTE]
>
>Solo se puede instalar y activar una instancia de la aplicación de escritorio de AEM a la vez.

## Compatibilidad con proxy {#proxy-support}

La aplicación de escritorio de AEM utiliza el proxy predefinido del sistema para conectarse a Internet a través de HTTPS. La aplicación solo se puede conectar mediante un proxy de red que no requiera autenticación adicional.

Si configura o modifica la configuración del servidor proxy para Windows (Opciones de Internet &gt; Configuración de LAN), reinicie la aplicación de escritorio de AEM para que los cambios surtan efecto.

Si el proxy requiere autenticación, el equipo de TI puede incluir la URL de AEM Assets en la lista de direcciones permitidas en la configuración del servidor proxy para permitir el paso del tráfico de la aplicación.

## Gestión de archivos {#file-handling}

Al cambiar un archivo desde una ubicación de recurso compartido de red montada por la aplicación de escritorio, los archivos se guardan en esa ubicación en dos fases. En la primera fase, un archivo se guarda localmente. Un usuario puede guardar el archivo y seguir trabajando en él sin esperar a que se complete la transferencia.

En la segunda fase, la aplicación de escritorio carga el archivo actualizado en el servidor AEM tras un retraso predefinido (por ejemplo, 30 segundos). Esta operación se produce en segundo plano. Utilice la opción Ver estado del recurso para ver el estado de la operación de carga.

1. Cargue un recurso en Recursos AEM.
1. Toque o haga clic en el icono de la aplicación de escritorio de AEM en la barra de herramientas.
1. En el menú, seleccione la opción Ver estado del recurso.
1. En el cuadro de diálogo, revise el estado de la operación de carga.

>[!NOTE]
>
>La aplicación de escritorio AEM puede gestionar recursos de hasta 40 GB.

## Conectar con una instancia de AEM detrás de un despachante {#connect-to-an-aem-instance-behind-a-dispatcher}

Los métodos Copy and Move de la API de recursos requieren que se pasen a AEM los siguientes encabezados adicionales:

* X-Destination
* Profundidad X
* X-Overwrite

AEM Desktop se conecta a AEM mediante una URL que incluye el puerto predeterminado. Por lo tanto, la configuración *virtualhosts* de la configuración del despachante debe incluir el número de puerto predeterminado. Para obtener más información sobre la configuración de hosts virtuales, consulte [Identificación de hosts](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#identifying-virtual-hosts-virtualhosts)virtuales.

Para obtener información adicional sobre cómo configurar el despachante para que pase por estos encabezados adicionales, consulte [Especificación de encabezados](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#specifying-the-http-headers-to-pass-through-clientheaders)HTTP.

## Personalización del cuadro de diálogo Información del recurso {#customize-the-asset-info-dialog}

Puede personalizar el cuadro de diálogo Información de recurso superponiendo uno o ambos de estos componentes:

* La página de interfaz de usuario Granite en `/libs/dam/gui/content/assets/moreinfo`
* El componente HTL `/css/javascript` en `/libs/dam/gui/components/admin/moreinfo`

El componente que se superponga dependerá de la naturaleza de la personalización. Para cambiar qué componentes se muestran como parte del cuadro de diálogo Información de recurso, superponga la página de interfaz de usuario Granite. Para cambiar el contenido HTML/CSS/Javascript del cuadro de diálogo, superponga el componente HTL.

## Administrar caché {#manage-cache}

En Windows, la caché se encuentra en `%LOCALAPPDATA%\Adobe\AssetsCompanion\Cache\`, donde es una versión codificada del host de AEM configurada en la aplicación de escritorio. Por ejemplo, `http://localhost:4502` aparece como `http%3A%2F%2Flocalhost%3A4502%2F`.

En Mac OS X, hay un directorio similar en `~/Library/Group Containers/group.com.adobe.aem.desktop/cache`.

### Opción en la aplicación para administrar la caché {#in-app-option-to-manage-cache}

Puede controlar la cantidad de espacio en disco disponible para su almacenamiento en caché local. Los artefactos del servidor de AEM Assets se almacenan en caché localmente para una experiencia más fluida. Puede cambiar los valores predeterminados para adaptarlos a sus necesidades. Además, puede borrar la caché para recuperar todos los recursos de nuevo. Para establecer las opciones deseadas, haga clic en el icono de la aplicación y haga clic en **[!UICONTROL Advanced]** &gt; **[!UICONTROL Manage Cache]**. ****

>[!NOTE]
>
>Cuando borra la caché, conserva los cambios no guardados. Los recursos que no estén protegidos en el servidor AEM se conservan y no se eliminan.

### Cambiar la ubicación de la caché en Windows {#change-location-of-cache-on-windows}

La ubicación predeterminada de la caché para la aplicación de escritorio de AEM es:

* Windows: `%LocalAppData%\Adobe\AssetsCompanion\Cache\EncodedAEMEndpoint`
* Mac: `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/EncodedAEMEndpoint`

`EncodedAEMEndpoint` es la URL del extremo de AEM configurado de la aplicación de escritorio de AEM. El valor es una versión codificada de la dirección URL de destino del servidor AEM. Por ejemplo, si la aplicación está segmentada `http://localhost:4502`, el nombre del directorio es `http%3A%2F%2Flocalhost%3A4502`. La ruta de Windows al directorio de caché en este ejemplo es %LocalAppData%\Adobe\AssetsCompanion\Cache\http%3A%2F%2Flocalhost%3A4502.

Para dirigir la aplicación a una carpeta o unidad diferente, edite el archivo de configuración de la aplicación.

1. Vaya al directorio de instalación de la aplicación. La ubicación predeterminada en Windows es `C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop`.
1. Edite el archivo Adobe Experience Manager Desktop.exe.config con un editor de texto.

   Se requieren privilegios de administrador para guardar los cambios en este archivo.

1. Busque la cadena "ProxyCacheRoot". Verá que su valor está establecido en la ubicación de caché "%LocalAppData%\Adobe\AssetsCompanion\Cache". Simplemente cambie este valor a cualquier ruta válida.

   >[!NOTE]
   >
   >La aplicación crea automáticamente un subdirectorio *&lt;Encoded AEM Endpoint&gt;* ; este comportamiento no se puede configurar.

## Recursos adicionales {#additional-resources}

* [Introducción a la aplicación de escritorio de AEM](https://helpx.adobe.com/experience-manager/kt/eseminars/ccoo-aem-desktop-app.html)
* [Uso de la aplicación de escritorio de AEM](use-app-v1.md)

* [Obtenga información sobre la llegada y la salida con la aplicación de escritorio de AEM](https://helpx.adobe.com/experience-manager/kt/assets/using/checkin-checkout-technical-video-understand.html)
* [Uso de la aplicación de escritorio con AEM Assets](https://helpx.adobe.com/experience-manager/kt/assets/using/checkin-checkout-technical-video-understand.html)
* [Solución de problemas de la aplicación de escritorio AEM](troubleshoot-app-v1.md)