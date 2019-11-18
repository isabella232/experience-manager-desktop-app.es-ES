---
title: Instalación y configuración de la aplicación de escritorio de AEM
description: Instale y configure la aplicación de escritorio de AEM para que funcione con los servidores de AEM Assets y descargue los recursos en el sistema de archivos local.
uuid: 79bc9de9-5708-41f9-ac43-68c1fd2a2129
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f6365302-1690-4719-9b8c-035719422740
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 850d2c21a796599ed40164e7d6f892967563c16b

---


# Instalación de la aplicación de escritorio AEM {#install-app-v2}

## Requisitos del sistema {#tech-specs-v2}

Para obtener información detallada, consulte las notas de la versión de la aplicación de escritorio de [AEM](release-notes.md).

## Actualización de la aplicación v1.x a la aplicación v2 {#upgrade-from-previous-version}

Si ya es usuario de la aplicación, comprenda las diferencias y similitudes entre la versión anterior y la última de la aplicación. Además, siga las directrices que se describen a continuación para realizar la transición de v1.x a la versión más reciente.

>[!NOTE]
>
>Las aplicaciones de escritorio v1.x y v2 no pueden coexistir en un equipo. Antes de instalar una versión, desinstale la otra versión.

Para actualizar de v1.x a la versión más reciente de la aplicación, siga estas instrucciones:

1. Antes de actualizar, sincronice todos los recursos. Cargue todos los cambios con la aplicación v1.x. Esto sirve para evitar perder los cambios al desinstalar la aplicación v1.x.
1. Desinstalar la aplicación v1.x. Al desinstalar v1.x, borre la caché.
1. Reinicie el equipo.
1. Descargue e instale la aplicación más reciente. Siga las instrucciones a continuación.

## Instalar {#install-v2}

Para instalar la aplicación de escritorio, siga estos pasos. Desinstale cualquier aplicación de escritorio de Adobe Experience Manager v1.x existente antes de instalar la aplicación más reciente. Para obtener más información, consulte arriba.

1. Tenga a mano la dirección URL y las credenciales de la implementación de AEM.
1. Omita este paso si utiliza AEM 6.4.4 y posterior o AEM 6.5.0 o posterior. Asegúrese de que la configuración de AEM cumple los requisitos de compatibilidad mencionados en las notas de la versión. Si es necesario, descargue el paquete [de](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) compatibilidad aplicable e instálelo con el administrador de paquetes de AEM como administrador de AEM. Para instalar un paquete, consulte [Cómo trabajar con paquetes](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/package-manager.html).
1. Ejecute el archivo binario del programa de instalación y siga las instrucciones que aparecen en pantalla para instalarlo.
1. En Windows, el programa de instalación puede solicitar la instalación `Visual Studio C++ Redistributable 2015`. Siga las instrucciones que aparecen en pantalla para instalarlo. Si la instalación falla, instálela manualmente. Descargue el instalador desde [aquí](https://www.microsoft.com/en-us/download/details.aspx?id=52685) e instale tanto `vc_redist.x64.exe` como `vc_redist.x86.exe` archivos. Vuelva a ejecutar el instalador de la aplicación de escritorio de AEM.
1. Reinicie el equipo como se le solicite. Inicie la aplicación de escritorio para configurarla.
1. Para conectar la aplicación con un repositorio de AEM, haga clic en el icono de la aplicación en la bandeja para iniciar la aplicación. Proporcione la dirección de la instancia de AEM. Haga clic en **[!UICONTROL Connect]** y proporcione las credenciales.

   ![Pantalla de conexión de la aplicación de escritorio a la](assets/connect_da2.png "dirección del servidor de entradaPantalla de conexión a la dirección del servidor de entrada")

   >[!Csubasta]
   >
   >Asegúrese de que no hay espacios al inicio o al final antes o después de la dirección del servidor AEM. De lo contrario, la aplicación no se puede conectar al servidor AEM.

1. Una vez realizada la conexión, puede ver la lista de carpetas y recursos disponibles en la carpeta raíz de AEM DAM. Puede examinar las carpetas desde la aplicación.

   ![Al iniciar sesión, la aplicación muestra el](assets/firstview_da2.png "contenido de DAM. Al iniciar sesión, la aplicación muestra el contenido de DAM")

1. (AEM 6.5.1 o posterior) Si utiliza una aplicación de escritorio con AEM 6.5.1 o posterior, actualice el conector S3 o Azure a la versión 1.10.4 o posterior. Consulte Conector [](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/data-store-config.html#AzureDataStore) de Azure o conector [S3](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/data-store-config.html#AmazonS3DataStore).

   Si es cliente de Adobe Managed Services (AMS), póngase en contacto con el Servicio de atención al cliente de Adobe.

## Configuración de preferencias {#set-preferences}

Para cambiar las preferencias, haga clic en el icono ![](assets/do-not-localize/more_options_da2.png) Más opciones y en el icono **[!UICONTROL Preference]**![Preferencias](assets/do-not-localize/preferences_icon_da2.png). En la **[!UICONTROL Preferences]** ventana, ajuste los valores de lo siguiente:

* [!UICONTROL Launch application on login].
* [!UICONTROL Show window when application starts].
* **[!UICONTROL Cache Directory]**:: Ubicación de la caché local de la aplicación (contiene los recursos descargados localmente).
* **[!UICONTROL Network Drive Letter]**:: Letra de unidad utilizada para asignar a AEM DAM. No lo cambie si no está seguro. La aplicación puede asignarse a cualquier letra de unidad en Windows. Si dos usuarios colocan recursos de distintas letras de unidad, no podrán ver los recursos colocados entre ellos. La ruta de los recursos cambia. Los recursos permanecen colocados en el archivo binario (digamos INDD) y no se eliminan. La aplicación muestra todas las letras de unidad disponibles y, de forma predeterminada, utiliza la última letra disponible que suele ser `Z`.
* **[!UICONTROL Maximum Cache Size]**:: Caché permitida en el disco duro en GB que se utiliza para almacenar recursos descargados localmente.
* **[!UICONTROL Current cache size]**:: Tamaño de almacenamiento de los recursos descargados localmente. La información solo se muestra después de descargar los recursos con la aplicación.
* **[!UICONTROL Automatically download linked assets]**:: Los recursos que se colocan en las aplicaciones nativas de Creative Cloud admitidas se recuperan automáticamente si descarga el archivo original.
* **[!UICONTROL Maximum number of downloads]**:: Al descargar recursos por primera vez (mediante la opción Mostrar, Abrir, Editar, Descargar o similar), los recursos se descargan únicamente si el lote contiene menos de este número. El valor predeterminado es 50. No cambie si no está seguro. Aumentar el valor puede llevar a tiempos de espera más largos y reducir el valor puede no permitirle descargar los recursos o carpetas necesarios de una sola vez.

Para actualizar las preferencias no disponibles, cierre la sesión del servidor AEM. Después de actualizar las preferencias, haga clic en ![Guardar preferencias](assets/do-not-localize/save_preferences_da2.png) para guardar los cambios.

![Preferencias y](assets/preferences_da2.png "configuración de la aplicación de escritorio de AEMespreferencias de la aplicación de escritorio")

## Desinstalar la aplicación {#uninstall-the-app}

Para desinstalar la aplicación en Windows, siga estos pasos:

1. Cargue todos los cambios en AEM para evitar que se pierda ninguna edición. Consulte [Edición de recursos y carga de recursos actualizados en AEM](using.md#edit-assets-upload-updated-assets). Cierre la sesión y [!UICONTROL Exit] la aplicación.
1. Elimine la aplicación como si eliminara cualquier otra aplicación del sistema operativo. Desinstálela de Agregar y quitar programas en Windows.
1. Para eliminar la caché y los registros, seleccione la casilla de verificación necesaria.
   ![Cuadro de diálogo de desinstalación para quitar registros y](assets/uninstall_da2.png "cachéCuadro de diálogo de desinstalación para quitar registros y caché")
1. Siga las instrucciones que aparecen en pantalla. Una vez finalizado, reinicie el equipo.

Para desinstalar la aplicación en Mac, siga estos pasos:

1. Cargue todos los cambios en AEM para evitar que se pierda ninguna edición. Consulte [Edición de recursos y carga de recursos actualizados en AEM](using.md#edit-assets-upload-updated-assets). Cierre la sesión y [!UICONTROL Exit] la aplicación.
1. Retire el `Adobe Experience Manager Desktop.app` de `/Applications`.

Como alternativa, para limpiar las cachés de aplicaciones internas en Mac y desinstalar la aplicación, puede ejecutar el siguiente comando en la terminal:
`/Applications/Adobe Experience Manager Desktop/Contents/Resources/uninstall-osx/uninstall.sh`
