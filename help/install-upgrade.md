---
title: Instalación y configuración de la aplicación de escritorio
description: Instale y configure los servidores [!DNL Adobe Experience Manager] desktop app to work with [!DNL Adobe Experience Manager Assets] y descargue los recursos en su sistema de archivos local.
feature: Aplicación de escritorio, información de versión
exl-id: 422e51c1-c456-4151-bb43-4b3d29a58187
source-git-commit: ea7227110aac38115829c93e7339dcdfbd9394a6
workflow-type: tm+mt
source-wordcount: '1410'
ht-degree: 0%

---

# Instalación de la aplicación de escritorio [!DNL Adobe Experience Manager] {#install-app-v2}

Con la aplicación de escritorio [!DNL Adobe Experience Manager], los recursos de [!DNL Experience Manager] están fácilmente disponibles en el escritorio local y se pueden usar en cualquier aplicación de escritorio nativa. Los recursos se pueden previsualizar, abrir en aplicaciones de escritorio nativas, mostrar en el Buscador de Mac o en el Explorador de Windows para colocarlos en otros documentos y cambiar localmente: los cambios se guardan de nuevo en [!DNL Experience Manager] cuando se carga y se crea una nueva versión en el repositorio.

Esta integración permite que diversas funciones de la organización puedan:

* Administre los recursos de forma centralizada en [!DNL Experience Manager Assets].

* Acceda a los recursos en cualquier aplicación de escritorio nativa, incluidas las aplicaciones de terceros y en Adobe Creative Cloud. Al hacerlo, los usuarios pueden cumplir fácilmente los distintos estándares, incluida la promoción de la marca.

Para usar la aplicación de escritorio [!DNL Experience Manager],

* Asegúrese de que la versión [!DNL Experience Manager] sea compatible con la aplicación de escritorio [!DNL Experience Manager]. Consulte los [requisitos del sistema](release-notes.md).

* Descargue e instale la aplicación. Consulte [instalar aplicación de escritorio](#install-v2) a continuación.

* Pruebe la conexión con algunos recursos. Consulte [cómo examinar y buscar recursos](using.md#browse-search-preview-assets).

## Requisitos, requisitos previos y vínculos de descarga del sistema {#tech-specs-v2}

Para obtener información detallada, consulte las [[!DNL Experience Manager] notas de la versión de la aplicación de escritorio](release-notes.md).

## Actualizar desde una versión anterior {#upgrade-from-previous-version}

Si es usuario de la versión 1.x de la aplicación de escritorio, entonces comprenda las diferencias y similitudes entre la versión anterior y la más reciente de la aplicación. Consulte las [novedades de la aplicación de escritorio](introduction.md#whats-new-v2) y [cómo funciona la aplicación](release-notes.md#how-app-works)

>[!NOTE]
>
>Dos versiones de la aplicación de escritorio no pueden coexistir en un equipo. Antes de instalar una versión, desinstale la otra versión.

Para actualizar desde una versión anterior de la aplicación, siga estas instrucciones:

1. Antes de actualizar, sincronice todos los recursos y cargue los cambios en [!DNL Experience Manager]. Esto sirve para evitar perder las ediciones al desinstalar la aplicación.

1. Desinstale la versión anterior de la aplicación. Al desinstalar, seleccione la opción para borrar la caché.

1. Reinicie su máquina.

1. [](release-notes.md) Descargue e  [](#install-v2) instale la aplicación más reciente. Siga las instrucciones que se indican a continuación.

## Instalar {#install-v2}

Para instalar la aplicación de escritorio, siga estos pasos. Desinstale cualquier aplicación de escritorio v1.x de Adobe [!DNL Experience Manager] existente antes de instalar la aplicación más reciente. Para obtener más información, consulte más arriba.

1. Descargue el instalador más reciente desde la página [notas de la versión](release-notes.md).

1. Mantenga a mano la dirección URL y las credenciales de su implementación [!DNL Experience Manager].

1. Si está actualizando desde otra versión de la aplicación, consulte [actualización de la aplicación de escritorio](#upgrade-from-previous-version).

1. Omita este paso si utiliza [!DNL Experience Manager] como [!DNL Cloud Service], [!DNL Experience Manager] 6.4.4 o posterior, o [!DNL Experience Manager] 6.5.0 o posterior. Asegúrese de que la configuración de [!DNL Experience Manager] cumple los requisitos de compatibilidad mencionados en las [notas de la versión](release-notes.md). Si es necesario, descargue el [paquete de compatibilidad](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) aplicable e instálelo utilizando el [!DNL Experience Manager] Administrador de paquetes como [!DNL Experience Manager] administrador. Para instalar un paquete, consulte [Cómo trabajar con paquetes](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html).

1. Ejecute el archivo binario del instalador y siga las instrucciones que aparecen en la pantalla para instalarlo.

1. En Windows, es posible que el instalador solicite la instalación de `Visual Studio C++ Redistributable 2015`. Siga las instrucciones que aparecen en la pantalla para instalarlo. Si la instalación falla, instálela manualmente. Descargue el instalador desde [here](https://www.microsoft.com/en-us/download/details.aspx?id=52685) e instale los archivos `vc_redist.x64.exe` y `vc_redist.x86.exe`. Vuelva a ejecutar el instalador de la aplicación de escritorio [!DNL Experience Manager].

1. Reinicie el equipo como se le pida. Inicie y configure la aplicación de escritorio.

1. Para conectar la aplicación con un repositorio [!DNL Experience Manager], haga clic en el icono de la aplicación en la bandeja e inicie la aplicación. Proporcione la dirección del servidor [!DNL Experience Manager] con el formato `https://[aem_server]:[port]/`.

   Haga clic en **[!UICONTROL Connect]** y proporcione las credenciales.

   ![Pantalla de conexión de la aplicación de escritorio a la dirección del servidor de entrada](assets/connect_da2.png)

   *Figura: Pantalla de conexión con la dirección del servidor de entrada.*

   >[!CAUTION]
   >
   >Asegúrese de que no haya espacios al principio o al final antes o después de la dirección del servidor [!DNL Experience Manager]. De lo contrario, la aplicación no se puede conectar al servidor [!DNL Experience Manager].

1. Una vez que la conexión se haya realizado correctamente, puede ver la lista de carpetas y recursos disponibles en la carpeta raíz del DAM [!DNL Experience Manager]. Puede examinar las carpetas desde la aplicación.

   ![Al iniciar sesión, la aplicación muestra el contenido de DAM](assets/firstview_da2.png)

   *Figura: La aplicación muestra el contenido de DAM después del inicio de sesión*

1. ([!DNL Experience Manager] 6.5.1 o posterior) Si utiliza una aplicación de escritorio con [!DNL Experience Manager] 6.5.1 o posterior, actualice el conector S3 o Azure a la versión 1.10.4 o posterior. Consulte [Conector de Azure](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html#azure-data-store) o Conector [S3](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/data-store-config.html#amazon-s-data-store).

   Si es cliente de Adobe Managed Services (AMS), póngase en contacto con el Servicio de atención al cliente de Adobe.

## Definir preferencias {#set-preferences}

Para cambiar las preferencias, haga clic en el icono ![Más opciones](assets/do-not-localize/more_options_da2.png) y en el icono **[!UICONTROL Preference]** ![Preferencias](assets/do-not-localize/preferences_icon_da2.png). En la ventana **[!UICONTROL Preferences]** , ajuste los valores de lo siguiente:

* [!UICONTROL Launch application on login].

* [!UICONTROL Show window when application starts].

* **[!UICONTROL Cache Directory]**: Ubicación de la caché local de la aplicación (contiene los recursos descargados localmente).

* **[!UICONTROL Network Drive Letter]**: La letra de unidad utilizada para asignar a  [!DNL Experience Manager] DAM. No cambie esto si no está seguro. La aplicación puede asignarse a cualquier letra de unidad en Windows. Si dos usuarios colocan recursos de distintas letras de unidad, no podrán ver los recursos colocados entre ellos. La ruta de los recursos cambia. Los recursos permanecen colocados en el archivo binario (por ejemplo, INDD) y no se eliminan. La aplicación enumera todas las letras de unidad disponibles y de forma predeterminada utiliza la última letra disponible que suele ser `Z`.

* **[!UICONTROL Maximum Cache Size]**: Caché permitida en disco duro en GB que se utiliza para almacenar recursos descargados localmente.

* **[!UICONTROL Current cache size]**: Tamaño de almacenamiento de los recursos descargados localmente. La información solo se muestra después de descargar los recursos mediante la aplicación.

* **[!UICONTROL Automatically download linked assets]**: Los recursos que se colocan en las aplicaciones de Creative Cloud nativas compatibles se recuperan automáticamente si descarga el archivo original.

* **[!UICONTROL Maximum number of downloads]**:  ![precaución ](assets/do-not-localize/caution-icon.png) iconCambie con precaución. Al descargar recursos por primera vez (mediante la opción Mostrar, Abrir, Editar, Descargar u otra opción similar), los recursos solo se descargan si el lote contiene menos de este número. El valor predeterminado es 50. No cambie si no está seguro. Aumentar el valor puede llevar a tiempos de espera más largos y disminuir el valor puede no permitirle descargar los recursos o carpetas necesarios de una sola vez.

* **[!UICONTROL Use legacy conventions when creating nodes for assets and folders]**:  ![precaución ](assets/do-not-localize/caution-icon.png) iconCambie con precaución. Esta configuración permite que la aplicación emule el comportamiento de la aplicación v1.10 al cargar carpetas. En v1.10, los nombres de nodo creados en el repositorio respetan los espacios y el formato en mayúsculas de los nombres de carpeta proporcionados por el usuario. Sin embargo, en la versión 2.1 de la aplicación, los espacios adicionales en los nombres de carpeta se convierten en guiones. Por ejemplo, cargar `New Folder` o `new   folder` crea el mismo nodo en el repositorio si la opción no está seleccionada y se mantiene el comportamiento predeterminado en v2.1. Si se selecciona esta opción, se crean diferentes nodos en el repositorio para las dos carpetas anteriores y coinciden con el comportamiento de la aplicación v1.10.

   El comportamiento predeterminado de v2.1 sigue siendo el mismo, es decir, reemplaza varios espacios en los nombres de carpeta con guiones en el nombre del nodo del repositorio y convierte en nombres de nodo en minúsculas.

* **[!UICONTROL Upload Acceleration]**:  ![precaución ](assets/do-not-localize/caution-icon.png) iconCambie con precaución. Al cargar recursos, la aplicación puede utilizar cargas simultáneas para mejorar la velocidad de carga. Puede aumentar la concurrencia de la carga moviendo el control deslizante hacia la derecha. El control deslizante en el extremo izquierdo significa que no hay concurrencia (carga de un solo subproceso), la posición media corresponde a 10 subprocesos simultáneos y el límite máximo en el extremo derecho corresponde a 20 subprocesos simultáneos. Un límite de concurrencia más alto requiere más recursos.

Para actualizar las preferencias no disponibles, cierre la sesión del servidor [!DNL Experience Manager] y, a continuación, actualice la sesión. Después de actualizar las preferencias, haga clic en ![Guardar preferencias](assets/do-not-localize/save_preferences_da2.png).

![Preferencias y configuración de la aplicación de escritorio](assets/preferences_da2.png)

*Figura: Preferencias de aplicación de escritorio.*

### Compatibilidad con proxy {#proxy-support}

[!DNL Experience Manager] la aplicación de escritorio utiliza el proxy predefinido del sistema para conectarse a Internet a través de HTTPS. La aplicación solo se puede conectar con un proxy de red que no requiera autenticación adicional.

Si configura o modifica la configuración del servidor proxy para Windows (Opciones de Internet > Configuración de LAN), reinicie la aplicación de escritorio [!DNL Experience Manager] para que los cambios surtan efecto. La configuración del proxy se aplica al iniciar la aplicación de escritorio. Cierre la aplicación y vuelva a iniciarla para que se apliquen los cambios.

Si el proxy requiere autenticación, el equipo de TI puede permitir que la [!DNL Experience Manager Assets] URL en la configuración del servidor proxy permita que el tráfico de la aplicación pase.

## Desinstalación de la aplicación {#uninstall-the-app}

Para desinstalar la aplicación en Windows, siga estos pasos:

1. Cargue todos los cambios a [!DNL Experience Manager] para evitar perder cualquier edición. Consulte [Editar recursos y cargar recursos actualizados a [!DNL Experience Manager]](using.md#edit-assets-upload-updated-assets). Cierre la sesión y [!UICONTROL Exit] la aplicación.

1. Elimine la aplicación ya que eliminaría cualquier otra aplicación del sistema operativo. Desinstálelo de Agregar y elimine programas en Windows.

1. Para eliminar la caché y los registros, seleccione la casilla de verificación necesaria.

   ![Desinstalar cuadro de diálogo para eliminar registros y caché](assets/uninstall_da2.png)

1. Siga las instrucciones que aparecen en la pantalla. Cuando termine, reinicie el equipo.

Para desinstalar la aplicación en Mac, siga estos pasos:

1. Cargue todos los cambios a [!DNL Experience Manager] para evitar perder cualquier edición. Consulte [Editar recursos y cargar recursos actualizados a [!DNL Experience Manager]](using.md#edit-assets-upload-updated-assets). Cierre la sesión y [!UICONTROL Exit] la aplicación.

1. Elimine `Adobe Experience Manager Desktop.app` de `/Applications`.

Como alternativa, para limpiar las cachés de aplicaciones internas en Mac y desinstalar la aplicación, puede ejecutar el siguiente comando en el terminal:

```shell
/Applications/Adobe Experience Manager Desktop/Contents/Resources/uninstall-osx/uninstall.sh
```
