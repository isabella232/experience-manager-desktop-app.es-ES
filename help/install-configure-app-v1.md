---
title: Instalar y configurar [!DNL Experience Manager] versión 1.x de la aplicación de escritorio
description: Instale y configure [!DNL Experience Manager] desktop app version 1.x to work with [!DNL Assets] servidores y asigne los recursos que desea montar como unidad en el escritorio.
uuid: 79bc9de9-5708-41f9-ac43-68c1fd2a2129
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.5/ASSETS, SG_EXPERIENCEMANAGER/6.4/ASSETS,SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f6365302-1690-4719-9b8c-035719422740
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2893fc1f8aad02e1436a1a281a320e6837487220
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 0%

---


# Instalar y configurar [!DNL Experience Manager] aplicación de escritorio v1.x {#install-and-configure-aem-desktop-app}

Al utilizar la aplicación de escritorio [!DNL Experience Manager], los recursos dentro de [!DNL Experience Manager] son fácilmente accesibles en el escritorio local y se pueden utilizar en cualquier aplicación de escritorio. Los recursos se pueden revelar fácilmente en Mac Finder o el Explorador de Windows, abrirse en aplicaciones de escritorio y cambiarse localmente; los cambios se guardan de nuevo en [!DNL Experience Manager] cuando se carga y se crea una nueva versión en el repositorio.

Esta integración permite que diversas funciones de la organización gestionen los activos de forma centralizada en Assets y accedan a ellos en el Creative Cloud y en otras aplicaciones, al tiempo que facilita el cumplimiento de las diversas normas, incluida la marca.

Para utilizar la aplicación de escritorio [!DNL Experience Manager],

* Asegúrese de que la versión del servidor [!DNL Experience Manager] sea compatible con la aplicación de escritorio [!DNL Experience Manager]. Consulte la [matriz de compatibilidad](release-notes-of-v1.md#compatibilitymatrix).

* Descargue e instale la aplicación.

* Pruebe la conexión con algunos recursos. Consulte [Acceso y apertura de recursos en el escritorio](use-app-v1.md#openondesktop).

## Requisitos del sistema, requisitos previos y vínculos de descarga {#system-requirements-prerequisites-and-download-links}

Para obtener información detallada, consulte las [[!DNL Experience Manager] notas de la versión de la aplicación de escritorio](release-notes-of-v1.md).

## Instale y conecte la aplicación al servidor [!DNL Experience Manager] {#install-and-connect-aem-desktop-app-to-aem-server}

Para obtener más información, consulte [Instalación y conexión [!DNL Experience Manager] desktop app to [!DNL Experience Manager] servidor](use-app-v1.md#installandconnect).

>[!NOTE]
>
>Solo se puede instalar una instancia de la aplicación de escritorio [!DNL Experience Manager] y estar activa a la vez.

## Administración de archivos {#file-handling}

Al cambiar un archivo desde una ubicación de recurso compartido de red montada por la aplicación de escritorio, los archivos se guardan en esa ubicación en dos fases. En la primera fase, un archivo se guarda localmente. Un usuario puede guardar el archivo y seguir trabajando en él sin esperar a que se complete la transferencia.

En la segunda fase, la aplicación de escritorio carga el archivo actualizado en el servidor [!DNL Experience Manager] tras un retraso predefinido (por ejemplo, 30 segundos). Esta operación se produce en segundo plano. Utilice la opción Estado del recurso de Vista para vista del estado de la operación de carga.

1. Cargue un recurso en Recursos.

1. Haga clic en el icono de la aplicación de escritorio [!DNL Experience Manager] de la barra de herramientas.

1. En el menú, seleccione la opción Estado del recurso de Vista.

1. En el cuadro de diálogo, revise el estado de la operación de carga.

>[!NOTE]
>
>[!DNL Experience Manager] la aplicación de escritorio puede gestionar recursos de hasta 40 GB de tamaño.

## Conectar con una instancia [!DNL Experience Manager] detrás de un despachante {#connect-to-an-aem-instance-behind-a-dispatcher}

Los métodos de copiar y mover de la API de recursos requieren que los siguientes encabezados adicionales se pasen a [!DNL Experience Manager]:

* X-Destination
* Profundidad X
* X-Overwrite

[!DNL Experience Manager] el escritorio se conecta  [!DNL Experience Manager] mediante una URL que incluye el puerto predeterminado. Por lo tanto, la configuración `virtualhosts` de la configuración del despachante debe incluir el número de puerto predeterminado. Para obtener más información sobre la configuración `virtualhosts`, consulte [identificación de hosts virtuales](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#identifying-virtual-hosts-virtualhosts).

Para obtener información adicional sobre cómo configurar el despachante para que pase por estos encabezados adicionales, consulte [Especificación de encabezados HTTP](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#specifying-the-http-headers-to-pass-through-clientheaders).

### Compatibilidad con proxy {#proxy-support}

[!DNL Experience Manager] la aplicación de escritorio utiliza el proxy predefinido del sistema para conectarse a Internet a través de HTTPS. La aplicación solo se puede conectar mediante un proxy de red que no requiera autenticación adicional.

Si configura o modifica la configuración del servidor proxy para Windows (Opciones de Internet > Configuración de LAN), reinicie la aplicación de escritorio [!DNL Experience Manager] para que los cambios surtan efecto.

>[!NOTE]
>
>La configuración de proxy solo se aplica cuando se inicio la aplicación de escritorio. Cierre y vuelva a iniciar la aplicación para que se apliquen los cambios.

Si el proxy requiere autenticación, el equipo de TI puede permitir que la URL de recursos de Experience Manager en la configuración del servidor proxy permita el paso del tráfico de la aplicación.

## Personalización del cuadro de diálogo Información de recurso {#customize-the-asset-info-dialog}

Puede personalizar el cuadro de diálogo Información de recurso superponiendo uno o ambos de estos componentes:

* Página de interfaz de usuario Granite en `/libs/dam/gui/content/assets/moreinfo`.

* El componente HTL `/css/javascript` en `/libs/dam/gui/components/admin/moreinfo`.

El componente que se superponga dependerá de la naturaleza de la personalización. Para cambiar qué componentes se muestran como parte del cuadro de diálogo Información de recurso, superponga la página de interfaz de usuario Granite. Para cambiar el contenido HTML, CSS o JavaScript del cuadro de diálogo, superponga el componente HTL.

## Administrar caché {#manage-cache}

En Windows, la caché se encuentra en `%LOCALAPPDATA%\Adobe\AssetsCompanion\Cache\`, donde es una versión codificada del host [!DNL Experience Manager] configurado en la aplicación de escritorio. Por ejemplo, `http://localhost:4502` aparece como `http%3A%2F%2Flocalhost%3A4502%2F`.

En Mac OS X, un directorio similar se encuentra en `~/Library/Group Containers/group.com.adobe.aem.desktop/cache`.

### Opción en la aplicación para administrar la caché {#in-app-option-to-manage-cache}

Puede controlar la cantidad de espacio en disco disponible para su almacenamiento en caché local. Los artefactos del servidor de Assets se almacenan en caché localmente para una experiencia más fluida. Puede cambiar los valores predeterminados para adaptarlos a sus necesidades. Además, puede borrar la caché para recuperar todos los recursos de nuevo. Para establecer las opciones deseadas, haga clic en el icono de la aplicación y haga clic en **[!UICONTROL Advanced]** > **[!UICONTROL Manage Cache]**. ****

>[!NOTE]
>
>Cuando borra la caché, conserva los cambios no guardados. Los recursos que no estén protegidos en el servidor [!DNL Experience Manager] se conservan y no se eliminan.

### Cambiar la ubicación de la caché en Windows {#change-location-of-cache-on-windows}

La ubicación predeterminada de la caché para la aplicación de escritorio [!DNL Experience Manager] es la siguiente:

* En Windows, `%LocalAppData%\Adobe\AssetsCompanion\Cache\EncodedAEMEndpoint`.

* En Mac, `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/EncodedAEMEndpoint`.

`EncodedAEMEndpoint` es la URL del  [!DNL Experience Manager] extremo configurada de la aplicación. El valor es una versión codificada de la dirección URL de destino del servidor [!DNL Experience Manager]. Por ejemplo, si la aplicación está dirigiendo `http://localhost:4502`, el nombre del directorio es `http%3A%2F%2Flocalhost%3A4502`. La ruta de Windows al directorio de la memoria caché en este ejemplo es `%LocalAppData%\Adobe\AssetsCompanion\Cache\http%3A%2F%2Flocalhost%3A4502`.

Para dirigir la aplicación a una carpeta o unidad diferente, edite el archivo de configuración de la aplicación.

1. Vaya al directorio de instalación de la aplicación. La ubicación predeterminada en Windows es `C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop`.

1. Edite el archivo Adobe Experience Manager Desktop.exe.config con un editor de texto.

   Se requieren privilegios de administrador para guardar los cambios en este archivo.

1. Busque la cadena &quot;ProxyCacheRoot&quot;. Verá que su valor se establece en la ubicación de caché `%LocalAppData%\Adobe\AssetsCompanion\Cache`. Simplemente cambie este valor a cualquier ruta válida.

   >[!NOTE]
   >
   >La aplicación crea automáticamente un subdirectorio *&lt;Extremo de AEM codificado>*. Este comportamiento no se puede configurar.

>[!MORELIKETHIS]
* [Introducción  [!DNL Experience Manager] a la aplicación](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/aem-desktop-app.html) de escritorio.
* [ [!DNL Experience Manager] Usar aplicación](use-app-v1.md) de escritorio.
* [ [!DNL Experience Manager] Solución de problemas de la aplicación](troubleshoot-app-v1.md) de escritorio.

