---
title: Instalar y configurar [!DNL Adobe Experience Manager] aplicación de escritorio
description: Instale y configure [!DNL Adobe Experience Manager] desktop app to work with [!DNL Adobe Experience Manager Assets] servidores y descargue los recursos en el sistema de archivos local.
translation-type: tm+mt
source-git-commit: a25c1fa13895ae9eb7268e3e01c83a5f0b9d7d1d
workflow-type: tm+mt
source-wordcount: '1162'
ht-degree: 1%

---


# Instalar [!DNL Adobe Experience Manager] aplicación de escritorio {#install-app-v2}

Al utilizar la aplicación de escritorio [!DNL Adobe Experience Manager], los recursos dentro de [!DNL Experience Manager] están fácilmente disponibles en el escritorio local y se pueden utilizar en cualquier aplicación de escritorio nativa. Los recursos se pueden previsualizar, abrir en aplicaciones de escritorio nativas, mostrar en Mac Finder o el Explorador de Windows para colocarlos en otros documentos y cambiar localmente. Los cambios se guardan en [!DNL Experience Manager] al cargar y se crea una nueva versión en el repositorio.

Esta integración permite que diversas funciones de la organización,

* Administre los recursos centralmente en [!DNL Experience Manager Assets].

* Acceda a los recursos en cualquier aplicación de escritorio nativa, incluidas las aplicaciones de terceros y en Adobe Creative Cloud. Al hacerlo, los usuarios pueden cumplir fácilmente los distintos estándares, incluida la marca.

Para utilizar la aplicación de escritorio [!DNL Experience Manager],

* Asegúrese de que su versión [!DNL Experience Manager] sea compatible con la aplicación de escritorio [!DNL Experience Manager]. Consulte los [requisitos del sistema](release-notes.md#system-requirements-and-prerequisites-v2) a continuación.

* Descargue e instale la aplicación. Consulte [instalación de la aplicación de escritorio](#install-v2) a continuación.

* Pruebe la conexión con algunos recursos. Consulte [cómo examinar y buscar recursos](using.md#browse-search-preview-assets).

## Requisitos del sistema, requisitos previos y vínculos de descarga {#tech-specs-v2}

Para obtener información detallada, consulte las [[!DNL Experience Manager] notas de la versión de la aplicación de escritorio](release-notes.md).

## Actualizar desde una versión anterior {#upgrade-from-previous-version}

Si es un usuario de la versión 1.x de la aplicación de escritorio, comprenda las diferencias y similitudes entre la versión anterior y la última de la aplicación. Consulte [novedades en la aplicación de escritorio](introduction.md#whats-new-v2) y [cómo funciona la aplicación](release-notes.md#how-app-works)

>[!NOTE]
>
>Dos versiones de la aplicación de escritorio no pueden coexistir en un equipo. Antes de instalar una versión, desinstale la otra versión.

Para actualizar desde una versión anterior de la aplicación, siga estas instrucciones:

1. Antes de actualizar, sincronice todos los recursos y cargue los cambios en [!DNL Experience Manager]. Esto sirve para evitar perder las ediciones al desinstalar la aplicación.

1. Desinstale la versión anterior de la aplicación. Al desinstalar, seleccione la opción para borrar la caché.

1. Reinicie el equipo.

1. [](release-notes.md) Descargue e  [](#install-v2) instale la aplicación más reciente. Siga las instrucciones a continuación.

## Instalar {#install-v2}

Para instalar la aplicación de escritorio, siga estos pasos. Desinstale cualquier aplicación de escritorio v1.x de Adobe [!DNL Experience Manager] existente antes de instalar la aplicación más reciente. Para obtener más información, consulte arriba.

1. Descargue el instalador más reciente de la página [notas de la versión](release-notes.md).

1. Tenga a mano la dirección URL y las credenciales de su implementación [!DNL Experience Manager].

1. Si está actualizando desde otra versión de la aplicación, consulte [actualización de la aplicación de escritorio](#upgrade-from-previous-version).

1. Omita este paso si utiliza [!DNL Experience Manager] como [!DNL Cloud Service], [!DNL Experience Manager] 6.4.4 o posterior, o [!DNL Experience Manager] 6.5.0 o posterior. Asegúrese de que su configuración [!DNL Experience Manager] cumple los requisitos de compatibilidad mencionados en las [notas de la versión](release-notes.md). Si es necesario, descargue el [paquete de compatibilidad](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) aplicable e instálelo mediante el Administrador de paquetes [!DNL Experience Manager] como administrador [!DNL Experience Manager]. Para instalar un paquete, consulte [Cómo trabajar con paquetes](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html).

1. Ejecute el archivo binario del programa de instalación y siga las instrucciones que aparecen en pantalla para instalarlo.

1. En Windows, el instalador puede solicitar la instalación de `Visual Studio C++ Redistributable 2015`. Siga las instrucciones que aparecen en pantalla para instalarlo. Si la instalación falla, instálela manualmente. Descargue el instalador de [aquí](https://www.microsoft.com/en-us/download/details.aspx?id=52685) e instale los archivos `vc_redist.x64.exe` y `vc_redist.x86.exe`. Vuelva a ejecutar el instalador de la aplicación de escritorio [!DNL Experience Manager].

1. Reinicie el equipo como se le solicite. Inicie y configure la aplicación de escritorio.

1. Para conectar la aplicación con un repositorio [!DNL Experience Manager], haga clic en el icono de la aplicación en la bandeja e inicie la aplicación. Proporcione la dirección del servidor [!DNL Experience Manager] con el formato `https://[aem_server]:[port]/`.

   Haga clic en **[!UICONTROL Connect]** y proporcione las credenciales.

   ![Pantalla de conexión de la aplicación de escritorio a la dirección del servidor de entrada](assets/connect_da2.png)

   *Figura: Pantalla de conexión a la dirección del servidor de entrada.*

   >[!CAUTION]
   >
   >Asegúrese de que no haya espacios al inicio o al final antes o después de la dirección del servidor [!DNL Experience Manager]. De lo contrario, la aplicación no se puede conectar al servidor [!DNL Experience Manager].

1. Tras una conexión correcta, puede realizar la vista de la lista de las carpetas y los recursos disponibles en la carpeta raíz del [!DNL Experience Manager] DAM. Puede examinar las carpetas desde la aplicación.

   ![Al iniciar sesión, la aplicación muestra el contenido de DAM](assets/firstview_da2.png)

   *Figura: La aplicación muestra el contenido de DAM después del inicio de sesión*

1. ([!DNL Experience Manager] 6.5.1 o posterior) Si utiliza una aplicación de escritorio con [!DNL Experience Manager] 6.5.1 o posterior, actualice el conector S3 o Azure a la versión 1.10.4 o posterior. Consulte [Conector de Azure](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html#azure-data-store) o conector [S3](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html#amazon-s-data-store).

   Si es cliente de Adobe Managed Services (AMS), póngase en contacto con el servicio de atención al cliente de Adobe.

## Definir preferencias {#set-preferences}

Para cambiar las preferencias, haga clic en ![Más iconos de opciones](assets/do-not-localize/more_options_da2.png) y **[!UICONTROL Preference]** ![Icono de preferencias](assets/do-not-localize/preferences_icon_da2.png). En la ventana **[!UICONTROL Preferences]**, ajuste los valores de lo siguiente:

* [!UICONTROL Launch application on login].

* [!UICONTROL Show window when application starts].

* **[!UICONTROL Cache Directory]**:: Ubicación de la caché local de la aplicación (contiene los recursos descargados localmente).

* **[!UICONTROL Network Drive Letter]**:: La letra de unidad utilizada para asignar al  [!DNL Experience Manager] DAM. No lo cambie si no está seguro. La aplicación puede asignarse a cualquier letra de unidad en Windows. Si dos usuarios colocan recursos de distintas letras de unidad, no podrán ver los recursos colocados entre ellos. La ruta de los recursos cambia. Los recursos permanecen colocados en el archivo binario (digamos INDD) y no se eliminan. La aplicación lista todas las letras de unidad disponibles y, de forma predeterminada, utiliza la última letra disponible que suele ser `Z`.

* **[!UICONTROL Maximum Cache Size]**:: Caché permitida en el disco duro en GB que se utiliza para almacenar recursos descargados localmente.

* **[!UICONTROL Current cache size]**:: Tamaño del almacenamiento de los recursos descargados localmente. La información solo se muestra después de descargar los recursos con la aplicación.

* **[!UICONTROL Automatically download linked assets]**:: Los recursos que se colocan en las aplicaciones de Creative Cloud nativas admitidas se recuperan automáticamente si descarga el archivo original.

* **[!UICONTROL Maximum number of downloads]**:: Al descargar recursos por primera vez (mediante la opción Mostrar, Abrir, Editar, Descargar o similar), los recursos se descargan únicamente si el lote contiene menos de este número. El valor predeterminado es 50. No cambie si no está seguro. Aumentar el valor puede llevar a tiempos de espera más largos y reducir el valor puede no permitirle descargar los recursos o carpetas necesarios de una sola vez.

* **[!UICONTROL Upload Acceleration]**:: Al cargar recursos, la aplicación puede utilizar cargas simultáneas para mejorar la velocidad de carga. Puede aumentar la concurrencia de la carga moviendo el control deslizante hacia la derecha. El control deslizante en el extremo izquierdo significa que no hay concurrencia (carga de un solo subproceso), la posición media corresponde a 10 subprocesos simultáneos y el límite máximo en el extremo derecho corresponde a 20 subprocesos simultáneos. Un límite de concurrencia mayor requiere un mayor consumo de recursos del procesador del equipo local.

Para actualizar las preferencias no disponibles, cierre la sesión del servidor [!DNL Experience Manager]. Después de actualizar las preferencias, haga clic en ![Guardar preferencias](assets/do-not-localize/save_preferences_da2.png) para guardar los cambios.

![Preferencias y configuración de la aplicación de escritorio](assets/preferences_da2.png)

*Figura: Preferencias de la aplicación de escritorio.*

## Desinstalar la aplicación {#uninstall-the-app}

Para desinstalar la aplicación en Windows, siga estos pasos:

1. Cargue todos los cambios en [!DNL Experience Manager] para evitar perder cualquier edición. Consulte [Editar recursos y cargar recursos actualizados a [!DNL Experience Manager]](using.md#edit-assets-upload-updated-assets). Cierre la sesión y [!UICONTROL Exit] la aplicación.

1. Elimine la aplicación como si eliminara cualquier otra aplicación del sistema operativo. Desinstálela de Añadir y elimine programas en Windows.

1. Para eliminar la caché y los registros, seleccione la casilla de verificación necesaria.

   ![Cuadro de diálogo de desinstalación para eliminar registros y caché](assets/uninstall_da2.png)

1. Siga las instrucciones que aparecen en pantalla. Una vez finalizado, reinicie el equipo.

Para desinstalar la aplicación en Mac, siga estos pasos:

1. Cargue todos los cambios en [!DNL Experience Manager] para evitar perder cualquier edición. Consulte [Editar recursos y cargar recursos actualizados a [!DNL Experience Manager]](using.md#edit-assets-upload-updated-assets). Cierre la sesión y [!UICONTROL Exit] la aplicación.

1. Elimine el `Adobe Experience Manager Desktop.app` de `/Applications`.

Como alternativa, para limpiar las cachés de aplicaciones internas en Mac y desinstalar la aplicación, puede ejecutar el siguiente comando en la terminal:

```shell
/Applications/Adobe Experience Manager Desktop/Contents/Resources/uninstall-osx/uninstall.sh
```
