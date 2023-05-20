---
title: Instalación y configuración de la aplicación de escritorio v1.10
description: Instalación y configuración [!DNL Experience Manager] versión 1.10 de la aplicación de escritorio para trabajar con [!DNL Assets] y asigne los recursos que desea montar como una unidad en el escritorio.
exl-id: 7f3bdfb1-d345-4e48-b020-6e06531f46f2
source-git-commit: 78f18e68178f711d925d7e308822c657087d009a
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 0%

---

# Instalación y configuración [!DNL Experience Manager] aplicación de escritorio v1.10 {#install-and-configure-aem-desktop-app}

Uso del [!DNL Experience Manager] aplicación de escritorio, los recursos dentro de [!DNL Experience Manager] son fácilmente accesibles desde el escritorio local y se pueden utilizar en cualquier aplicación de escritorio. Los recursos se pueden mostrar fácilmente en el Finder de Mac o en el Explorador de Windows, abrirse en aplicaciones de escritorio y cambiarse localmente; los cambios se guardan de nuevo en [!DNL Experience Manager] al cargar y se crea una nueva versión en el repositorio.

Esta integración permite que diversas funciones de la organización administren los recursos de forma centralizada en Assets y accedan a ellos en el Creative Cloud y otras aplicaciones, al tiempo que facilita el cumplimiento de los distintos estándares, incluida la marca.

Para usar [!DNL Experience Manager] aplicación de escritorio,

* Asegúrese de que su [!DNL Experience Manager] La versión del servidor es compatible con [!DNL Experience Manager] aplicación de escritorio. Consulte la [matriz de compatibilidad](release-notes-of-v1.md#compatibilitymatrix).

* Descargue e instale la aplicación.

* Pruebe la conexión con algunos recursos. Consulte [Acceso y apertura de recursos en el escritorio](use-app-v1.md#openondesktop).

## Requisitos del sistema, requisitos previos y vínculos de descarga {#system-requirements-prerequisites-and-download-links}

Para obtener información detallada, consulte la [[!DNL Experience Manager] notas de la versión de aplicación de escritorio](release-notes-of-v1.md).

## Instale y conecte la aplicación a [!DNL Experience Manager] server {#install-and-connect-aem-desktop-app-to-aem-server}

Para obtener más información, consulte [Instalar y conectar [!DNL Experience Manager] aplicación de escritorio para [!DNL Experience Manager] server](use-app-v1.md#installandconnect).

>[!NOTE]
>
>Solo una instancia de [!DNL Experience Manager] La aplicación de escritorio de se puede instalar y activar a la vez.

## Administración de archivos {#file-handling}

Al cambiar un archivo desde una ubicación de recurso compartido de red montada por la aplicación de escritorio, los archivos se guardan en esa ubicación en dos fases. En la primera fase, se guarda un archivo localmente. Un usuario puede guardar el archivo y continuar trabajando en él, sin esperar a que se complete la transferencia.

En la segunda fase, la aplicación de escritorio carga el archivo actualizado en [!DNL Experience Manager] servidor después de un retraso predefinido (por ejemplo, 30 segundos). Esta operación se produce en segundo plano. Utilice la opción Ver estado del recurso para ver el estado de la operación de carga.

1. Cargue un recurso en Assets.

1. Haga clic en [!DNL Experience Manager] icono de aplicación de escritorio de la barra de herramientas.

1. En el menú, seleccione la opción Ver estado del recurso.

1. En el cuadro de diálogo, revise el estado de la operación de carga.

>[!NOTE]
>
>[!DNL Experience Manager] La aplicación de escritorio de puede gestionar recursos de hasta 40 GB de tamaño.

## Conexión a un [!DNL Experience Manager] instancia detrás de Dispatcher {#connect-to-an-aem-instance-behind-a-dispatcher}

Los métodos copy y move de la API de Assets requieren que se pasen los siguientes encabezados adicionales a [!DNL Experience Manager]:

* Destino X
* Profundidad X
* Sobrescribir X

[!DNL Experience Manager] desktop se conecta a [!DNL Experience Manager] mediante una dirección URL que incluya el puerto predeterminado. Por lo tanto, el `virtualhosts` la configuración de dispatcher debe incluir el número de puerto predeterminado. Para obtener más información sobre `virtualhosts` configuración, consulte [identificar hosts virtuales](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#identifying-virtual-hosts-virtualhosts).

Para obtener información adicional sobre cómo configurar Dispatcher para que pase por estos encabezados adicionales, consulte [Especificar los encabezados HTTP](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#specifying-the-http-headers-to-pass-through-clientheaders).

### Compatibilidad con proxy {#proxy-support}

[!DNL Experience Manager] La aplicación de escritorio de utiliza el proxy predefinido del sistema para conectarse a Internet a través de HTTPS. La aplicación solo se puede conectar con un proxy de red que no requiera autenticación adicional.

Si establece o modifica la configuración del servidor proxy para Windows (Opciones de Internet > Configuración de LAN), reinicie [!DNL Experience Manager] aplicación de escritorio para que los cambios surtan efecto.

>[!NOTE]
>
>La configuración proxy solo se aplica al iniciar la aplicación de escritorio. Cierre y vuelva a iniciar la aplicación para que los cambios surtan efecto.

Si el proxy requiere autenticación, el equipo de TI puede permitir que la URL de Experience Manager Assets en la configuración del servidor proxy permita el paso del tráfico de la aplicación.

## Personalización del cuadro de diálogo Información del recurso {#customize-the-asset-info-dialog}

Puede personalizar el cuadro de diálogo Información del recurso superponiendo uno o ambos de estos componentes:

* La página de interfaz de usuario de Granite en `/libs/dam/gui/content/assets/moreinfo`.

* El HTL `/css/javascript` componente en `/libs/dam/gui/components/admin/moreinfo`.

El componente que se superponga dependerá de la naturaleza de la personalización. Para cambiar qué componentes se muestran como parte del cuadro de diálogo Información del recurso, superponga la página de interfaz de usuario de Granite. Para cambiar el contenido del HTML, CSS o JavaScript del cuadro de diálogo, superponga el componente HTL.

## Administrar caché {#manage-cache}

En Windows, la caché se encuentra en `%LOCALAPPDATA%\Adobe\AssetsCompanion\Cache\`, donde es una versión codificada del [!DNL Experience Manager] host configurado en la aplicación de escritorio. Por ejemplo, `http://localhost:4502` aparece como `http%3A%2F%2Flocalhost%3A4502%2F`.

En Mac OS X, hay un directorio similar en `~/Library/Group Containers/group.com.adobe.aem.desktop/cache`.

### Opción en la aplicación para administrar la caché {#in-app-option-to-manage-cache}

Puede controlar la cantidad de espacio en disco disponible para el almacenamiento en caché local. Los artefactos del servidor de Assets se almacenan en caché localmente para lograr una experiencia más fluida. Puede cambiar los valores predeterminados para adaptarlos a sus necesidades. Además, puede borrar la caché para recuperar todos los recursos de nuevo. Para definir las opciones deseadas, haga clic en el icono de la aplicación y luego en **[!UICONTROL Advanced]** > **[!UICONTROL Manage Cache]**. ****

>[!NOTE]
>
>Cuando borra la caché, conserva los cambios no guardados. Cualquier recurso no registrado [!DNL Experience Manager] se conservan y no se eliminan.

### Cambiar la ubicación de la caché en Windows {#change-location-of-cache-on-windows}

La ubicación predeterminada de la caché para [!DNL Experience Manager] La aplicación de escritorio es la siguiente:

* En Windows, `%LocalAppData%\Adobe\AssetsCompanion\Cache\EncodedAEMEndpoint`.

* En Mac, `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/EncodedAEMEndpoint`.

`EncodedAEMEndpoint` está configurado para la aplicación [!DNL Experience Manager] URL de extremo. El valor es una versión codificada de la dirección URL de destino de [!DNL Experience Manager] servidor. Por ejemplo, si la aplicación tiene como objetivo `http://localhost:4502`, el nombre del directorio es `http%3A%2F%2Flocalhost%3A4502`. La ruta de Windows al directorio de caché en este ejemplo es `%LocalAppData%\Adobe\AssetsCompanion\Cache\http%3A%2F%2Flocalhost%3A4502`.

Para dirigir la aplicación a una carpeta o unidad diferente, edite el archivo de configuración de la aplicación.

1. Vaya al directorio de instalación de la aplicación. La ubicación predeterminada en Windows es `C:\Program Files (x86)\Adobe\Adobe Experience Manager Desktop`.

1. Edite el archivo Adobe Experience Manager Desktop.exe.config con un editor de texto.

   Se requieren privilegios de administrador para guardar los cambios en este archivo.

1. Busque la cadena &quot;ProxyCacheRoot&quot;. Verá que su valor se establece en la ubicación de caché `%LocalAppData%\Adobe\AssetsCompanion\Cache`. Simplemente cambie este valor a cualquier ruta válida.

   >[!NOTE]
   >
   >La aplicación crea automáticamente un *&lt;encoded aem=&quot;&quot; endpoint=&quot;&quot;>* subdirectorio. Este comportamiento no se puede configurar.

>[!MORELIKETHIS]
* [Introducción a [!DNL Experience Manager] aplicación de escritorio](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/creative-workflows/aem-desktop-app.html).
* [Uso [!DNL Experience Manager] aplicación de escritorio](use-app-v1.md).
* [Solución de problemas [!DNL Experience Manager] aplicación de escritorio](troubleshoot-app-v1.md).

