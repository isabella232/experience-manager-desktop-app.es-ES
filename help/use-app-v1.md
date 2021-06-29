---
title: Utilice la versión 1.10 de la aplicación de escritorio [!DNL Experience Manager] .
description: Aprenda a utilizar la versión 1.10 de la aplicación de escritorio de Adobe Experience Manager y a optimizar su trabajo con recursos en el escritorio.
feature: Aplicación de escritorio, administración de recursos
exl-id: 2fdc1c8d-b822-4cca-ad06-bd875a00aa6d
source-git-commit: dcd29d0bbb32004d970d334c256e659f4a4c39e1
workflow-type: tm+mt
source-wordcount: '2371'
ht-degree: 0%

---

# Usar la aplicación de escritorio v1.10 de [!DNL Experience Manager] {#use-aem-desktop-app-v1x}

Con la aplicación, los recursos de [!DNL Experience Manager] son fácilmente accesibles desde el escritorio local y se pueden usar en cualquier aplicación de escritorio. Los recursos pueden mostrarse fácilmente en el Buscador de Mac o en el Explorador de Windows, abrirse en aplicaciones de escritorio y modificarse localmente. Los cambios se guardan de nuevo en [!DNL Experience Manager] con una nueva versión creada en el repositorio.

Esta integración permite que diversas funciones de la organización administren los recursos de forma centralizada en Assets y accedan a ellos en el Creative Cloud y en otras aplicaciones, a la vez que facilita el cumplimiento de los distintos estándares, incluida la promoción de la marca.

Las tareas clave que realiza mediante la aplicación de escritorio v1 [!DNL Experience Manager] incluyen:

1. [Conectarse con un servidor [!DNL Experience Manager] ](#installandconnect)
1. [Abrir recursos directamente en el escritorio](#openondesktop)
1. [Editar y extraer recursos del escritorio](#workonassets)
1. [Cargar recursos y carpetas de forma masiva](#bulkupload)

Para ver las distintas recomendaciones recomendadas y no recomendadas, consulte las [prácticas recomendadas para usar app](best-practices-for-v1.md). Si tiene problemas al usar la aplicación, consulte cómo [solucionar problemas [!DNL Experience Manager] escritorio](troubleshoot-app-v1.md).

>[!NOTE]
>
>La aplicación de escritorio se introdujo en la versión [!DNL Experience Manager] 6.1 y se denominó [!DNL Experience Manager Assets Companion App].

## [!DNL Experience Manager] puntos de contacto de la aplicación de escritorio en el flujo de trabajo creativo {#aem-desktop-app-touch-points-in-the-creative-workflow}

[!DNL Experience Manager] la aplicación de escritorio, junto con  [!DNL Assets], se integra en el flujo de trabajo creativo y ofrece los siguientes puntos de contacto.

![[!DNL Experience Manager] puntos de contacto de la aplicación de escritorio en el flujo de trabajo creativo](assets/aem_desktopapp_workflow.png)

[!DNL Experience Manager] puntos de contacto de la aplicación de escritorio en el flujo de trabajo creativo

## Instalación y conexión de la aplicación al servidor [!DNL Experience Manager] {#installandconnect}

Antes de empezar a crear o editar los recursos creativos, conecte la aplicación de escritorio con el servidor [!DNL Assets] para descargar y cargar recursos en el repositorio. Realice las siguientes tareas:

1. [Instale la aplicación](#installapp).
1. [Establezca sus ](#inapppref) preferencias y los detalles de conexión.
1. [Conéctese a la  [!DNL Experience Manager] ](#connect) respuesta y monte el repositorio de recursos como una unidad local.
1. [Habilite las ](#desktopactions) acciones de escritorio en el  [!DNL Experience Manager] servidor.

[!DNL Experience Manager] la aplicación de escritorio utiliza una conexión HTTPS para conectarse al  [!DNL Experience Manager] servidor y transferir sus recursos de forma segura y robusta.

>[!NOTE]
>
>Para parte de o todos los pasos de instalación y configuración, es posible que necesite ayuda de su [!DNL Experience Manager] administrador o administrador del sistema.

### Instalación de la aplicación {#installapp}

Para utilizar la aplicación de escritorio [!DNL Experience Manager], asegúrese de que la aplicación admite la versión del servidor [!DNL Experience Manager]. Descargue el archivo de instalación (binario) apropiado para su sistema operativo (Mac o Windows) e instale la aplicación.

Puede ser necesaria una configuración detallada en función de las preferencias de red y sistema. Consulte [Instalar y configurar [!DNL Experience Manager] aplicación de escritorio](install-configure-app-v1.md) para obtener más información.

1. Vaya a la página de descarga [[!DNL Experience Manager] aplicación de escritorio v1.10](/help/release-notes-of-v1.md) y descargue el binario apropiado para su sistema operativo.
1. Inicie el archivo de instalación descargado y siga las instrucciones que aparecen en la pantalla para instalar la aplicación.

   >[!NOTE]
   >
   >Solo se puede instalar una instancia de la aplicación de escritorio [!DNL Experience Manager] y estar activa a la vez.

### Conozca las opciones y preferencias en la aplicación {#inapppref}

La aplicación permite que la configuración se conecte y desconecte de los servidores [!DNL Experience Manager], vea el estado de las cargas, administre la caché local, etc. La configuración predeterminada funciona para un usuario típico de la aplicación. Puede modificar la configuración para obtener más información de la aplicación y de la integración con el servidor [!DNL Experience Manager]. Los distintos ajustes se describen a continuación en detalle.

**Explorar** recursosAbra la unidad local en la que se monta el  [!DNL Assets] repositorio. En otras palabras, explore los recursos que ahora están disponibles en su equipo local.

**Ver** estado de los recursosCuando se cargan los recursos modificados o se añaden nuevos recursos al  [!DNL Assets] repositorio, la aplicación los carga en segundo plano. La carga en segundo plano permite realizar operaciones sin problemas, sin tener que esperar a que finalice la carga, especialmente para los recursos de gran tamaño. Puede guardar los cambios localmente y olvidarlos. La aplicación tarda algún tiempo en enviar estos recursos al servidor, según el ancho de banda disponible. Puede comprobar el estado de la carga, junto con información más básica.

**** OpcionesHaga clic en las opciones de la bandeja de aplicaciones de escritorio para acceder a la configuración para iniciar la aplicación cuando se inicie el sistema; para conectarse al  [!DNL Experience Manager] servidor cuando se inicie la aplicación; y cambiar la letra de la unidad local donde  [!DNL Assets] esté disponible después de montarla.

**Avanzado > Administrar** cachéPuede controlar la cantidad de espacio en disco disponible para el almacenamiento en caché local. Los artefactos del servidor [!DNL Assets] se almacenan en caché localmente para una experiencia más suave. Puede cambiar los valores predeterminados para adaptarlos a sus necesidades. Además, puede borrar la caché para recuperar todos los recursos de nuevo. Cuando borra la caché, conserva los cambios sin guardar. Los recursos que no estén registrados en el servidor [!DNL Experience Manager] se conservan y no se eliminan.

### Conectarse a un servidor [!DNL Experience Manager] {#connect}

La aplicación admite la configuración proxy en Mac y Windows. La configuración se lee al iniciarse la aplicación. Si modifica la configuración del proxy, reinicie la aplicación para que los cambios surtan efecto.

>[!NOTE]
>
>Si modifica la configuración del proxy, reinicie la aplicación para que los cambios surtan efecto. De lo contrario, la aplicación continúa utilizando el servidor proxy configurado anteriormente.

1. Inicie la aplicación de escritorio [!DNL Experience Manager]. Para asignar la instancia [!DNL Experience Manager] a la aplicación, especifique el servidor [!DNL Experience Manager] con el formato `https://[aem-server-url]:[port]`.

   ![Autenticar en Mac y proporcionar la URL del  [!DNL Experience Manager] servidor](assets/aem_desktop_app_server_url.png)

1. En la pantalla de inicio de sesión, especifique el nombre de usuario y la contraseña de la instancia. Para especificar una instancia [!DNL Experience Manager] alternativa, seleccione la opción **[!UICONTROL Alternate Login URL]**.

   ![Proporcionar credenciales de  [!DNL Experience Manager] servidor en la pantalla de inicio de sesión de la aplicación de  [!DNL Experience Manager] escritorio](assets/login_screen_v1.png)

### Habilitar acciones de escritorio en la interfaz web [!DNL Experience Manager] {#desktopactions}

Desde la interfaz de usuario de Assets, puede explorar las ubicaciones de los recursos o retirarse y abrir el recurso para editarlo en la aplicación de escritorio. Estas opciones se denominan acciones de escritorio y no están activadas de forma predeterminada. Siga estos pasos para habilitarlo.

1. En la interfaz de Assets, toque o haga clic en el icono Usuario en la esquina superior derecha de la barra de herramientas.
1. Haga clic en **[!UICONTROL My Preferences]** para mostrar el cuadro de diálogo **[!UICONTROL Preferences]**.

   ![[!DNL Experience Manager] interfaz con preferencias de usuario](assets/aem_ui_user_preferences.png)

1. En el cuadro de diálogo [!UICONTROL User Preferences], seleccione **[!UICONTROL Show Desktop Actions For Assets]** y haga clic en **[!UICONTROL Accept]**.

   ![Marque  [!UICONTROL Show Desktop Actions For Assets] para habilitar acciones de escritorio](assets/enable_desktop_actions.png)

   *Figura: Marque  [!UICONTROL Show Desktop Actions For Assets] para habilitar las acciones de escritorio.*

## Acceso y apertura de recursos en el escritorio {#openondesktop}

Al hacer clic en **Abrir** para abrir un recurso en el equipo local, la aplicación descarga el recurso en su caché interna. La aplicación inicia la aplicación de escritorio nativa asociada al tipo de archivo del recurso descargado.

En Mac, seleccione **Abrir** en el menú contextual para abrir un recurso a través de la aplicación de escritorio [!DNL Experience Manager]. En Windows, seleccione Abrir en Web en el menú contextual para abrir el recurso. En la ventana Estado del recurso, pulse o haga clic en ![Abrir en escritorio icono](assets/do-not-localize/aemassets_icon_openondesktop.png) para abrir el recurso.

Para los archivos Adobe InDesign (INDD), seleccione **[!UICONTROL Open]** en el menú contextual. Al hacer clic en esta opción, la aplicación descarga los recursos vinculados a su sistema de archivos local y, a continuación, abre el archivo INDD en Adobe InDesign. Este método garantiza que los recursos necesarios estén disponibles localmente al editar el archivo INDD.

![Opciones del menú contextual para acceder y abrir recursos mediante la aplicación de  [!DNL Experience Manager] escritorio](assets/aem_desktopapp_mac_context_menu.png)

*Figura: Opciones del menú contextual para acceder y abrir recursos mediante la aplicación de  [!DNL Experience Manager] escritorio.*

>[!NOTE]
>
>En Windows, la [configuración predeterminada de Windows 7](https://support.microsoft.com/es-es/kb/2668751) evita que la aplicación de escritorio [!DNL Experience Manager] gestione recursos que superen los 50 MB.

<!-- TBD: The above note is for Windows 7 which is not supported by the app anymore. Remove it later.
-->

>[!NOTE]
>
>Adobe recomienda ir a Opciones de vista de buscador en Mac y desactivar las opciones **Mostrar información de elemento**, **Mostrar vista previa de elemento** y **Mostrar columna de vista previa** para la carpeta [!DNL Assets] montada. Mejora el rendimiento.

### Opciones adicionales en la interfaz [!DNL Experience Manager] {#additional-options-in-aem-assets}

Después de asignar el repositorio [!DNL Assets] a la unidad local, puede activar iconos adicionales y la función Carga de carpetas para que aparezcan en los recursos y carpetas asignados.

1. Abra la interfaz [!DNL Assets] y pase el puntero sobre una carpeta o un recurso para mostrar las acciones de escritorio como acciones rápidas en la vista de tarjeta.

   ![En la interfaz de usuario de Assets, abra el menú de acciones rápidas para ver las acciones de escritorio](assets/desktop_actions_in_card_view.png)

   *Figura: En la interfaz de usuario de Assets, abra el menú de acciones rápidas para ver las acciones de escritorio.*

   Estas acciones de escritorio también están disponibles cuando hace clic en la opción **Acciones de escritorio** de la barra de herramientas después de seleccionar el recurso o de la barra de herramientas de la página de recursos.

1. Para abrir el recurso en la aplicación de escritorio asociada a la extensión de archivo específica, haga clic en la acción rápida **Abrir en escritorio** ![Abrir en escritorio icono](assets/do-not-localize/aemassets_icon_openondesktop.png).

   Como alternativa, elija **Abrir** en el menú **Acciones de escritorio** de la barra de herramientas.

Para localizar el recurso en particular en el sistema de archivos local, haga clic en **Mostrar** acción rápida ![Mostrar icono](assets/do-not-localize/aemassets_reveal_icon.png). Como alternativa, elija **Mostrar** en el menú **Acciones de escritorio** de la barra de herramientas.

## Explicación de los estados de los recursos {#understand-the-asset-statuses}

| ![Icono de aplicación predeterminado de Windows](assets/do-not-localize/win_default.png) | La aplicación está conectada al servidor y todos los recursos están sincronizados. |
--- |--- |
| ![Icono deshabilitado de Windows](assets/do-not-localize/win_disabled.png) | La aplicación se inicia, pero no está conectada con el servidor. Es posible que algunos recursos estén pendientes de sincronización. |
| ![Icono de sincronización de archivos de Windows](assets/do-not-localize/win_sync.png) | Los recursos se están sincronizando. Los archivos se están cargando o descargando. Puede ver los estados exactos y pausar las transferencias desde la ventana Estado del recurso. |
| ![Icono de reconexión de Windows](assets/do-not-localize/win_refresh.png) | La aplicación está intentando volver a conectarse. Potencialmente, los problemas de red están provocando que se desconecte. |

## Trabajar en los recursos {#workonassets}

### Consulte los recursos de la interfaz web [!DNL Experience Manager] {#check-out-assets-from-the-aem-web-interface}

[!DNL Assets] permite extraer recursos para editarlos y volver a protegerlos después de completar los cambios. Después de retirar un recurso, solo puede editarlo, anotarlo, publicarlo, moverlo o eliminarlo. Si se cierra un recurso, este se bloquea y se evita que otros usuarios realicen cualquiera de estas operaciones. Para poder extraer o incorporar recursos, debe disponer de acceso de escritura.

Existen dos formas de extraer recursos de la interfaz web [!DNL Experience Manager]. Para obtener información detallada sobre el primer método, consulte [protección de archivos desde la interfaz de usuario de Assets](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/check-out-and-submit-assets.html). Siga estos pasos para que los segundos métodos desprotejan y abran el recurso cuando esté instalada la aplicación de escritorio [!DNL Experience Manager].

1. Abra la interfaz [!DNL Assets] y pase el puntero sobre una carpeta o un recurso para mostrar las acciones de escritorio como acciones rápidas en la vista de tarjeta.

   ![Opción Propiedades en la vista de tarjeta](assets/desktop_actions_in_card_view.png)

   Estas acciones de escritorio también están disponibles cuando toca o hace clic en el icono Acciones de escritorio de la barra de herramientas después de seleccionar el recurso o de la barra de herramientas de la página de recursos.

1. Para abrir el recurso, pulse o haga clic en la acción rápida Abrir en el escritorio ![Abrir en el escritorio icono](assets/do-not-localize/aemassets_icon_openondesktop.png).

   Como alternativa, seleccione Abrir en el menú Acciones de escritorio de la barra de herramientas.

   >[!NOTE]
   >
   >Cuando edita un archivo que acaba de abrirse y no está desprotegido, otros usuarios no se dan cuenta de que usted está actualizando un recurso.

1. Para abrir un recurso para editarlo en una aplicación de Adobe Creative Cloud, toque o haga clic en el icono Editar escritorio acción rápida ![Editar escritorio](assets/do-not-localize/aemassets_icon_editdesktop.png). Esto también extrae el recurso para editarlo. Cuando termine de editar, desproteja el recurso para actualizar los cambios en [!DNL Assets].

   Como alternativa, seleccione Editar en el menú Acciones de escritorio de la barra de herramientas.

1. Seleccione la opción de menú Abrir. Los recursos seleccionados se abren en modo de vista previa.
1. Para editar los recursos, seleccione la opción Editar . Los recursos se abren en modo de edición.

### Consulte los recursos desde Finder en Mac OS {#check-out-assets-on-mac}

La aplicación permite extraer archivos de recursos para evitar que otros usuarios modifiquen los archivos en los que está trabajando.

1. En el menú contextual de Mac, seleccione la opción Abrir carpeta de AEM Assets para abrir Finder.

   ![Opciones del menú contextual para acceder y abrir recursos mediante la aplicación de  [!DNL Experience Manager] escritorio](assets/aem_desktopapp_mac_context_menu.png)

   *Figura: Opciones del menú contextual para acceder y abrir recursos mediante la aplicación de  [!DNL Experience Manager] escritorio.*

1. Vaya al recurso que desea desproteger.
1. Haga clic con el botón derecho en el recurso y seleccione Más información de recursos en el menú contextual.
1. En el cuadro de diálogo Información del recurso, pulse o haga clic en el icono de cierre de compra para extraer el recurso. El icono Cierre de compra le permite acceder al icono de protección después de tocar o hacer clic en él.

   ![Vaya al recurso para cerrar la compra](assets/browse_assets_to_checkout.png)

1. Para proteger el recurso y que esté disponible para otros usuarios, toque o haga clic en el icono de protección del cuadro de diálogo Información del recurso .

### Comprobar recursos en Windows {#check-out-assets-on-windows}

La aplicación permite extraer archivos de recursos para evitar que otros usuarios modifiquen los archivos en los que está trabajando.

1. En el menú Contexto, seleccione Explorar recursos para abrir Explorer.
1. En Explorer, vaya a la ubicación del recurso que desea desproteger.
1. Haga clic con el botón derecho en el recurso y seleccione Abrir en la web en el menú contextual.
1. En el cuadro de diálogo Información de recursos, pulse o haga clic en el icono Cierre de compra . El icono Cierre de compra le permite acceder al icono de protección.

   ![Icono de cierre de compra](assets/checkout_icon_toggles.png)

1. Revise el recurso en Explorer. El icono de bloqueo del recurso ![Icono de bloqueo de recursos](assets/do-not-localize/aemassets_icon_lockcheckout.png) indica que ha extraído el recurso.

   >[!NOTE]
   >
   >El icono de candado puede aparecer después de un retraso. [!DNL Experience Manager] la aplicación de escritorio almacena en caché los recursos para un acceso rápido, por lo que puede tardar unos minutos en actualizar el estado bloqueado.

1. Para proteger el recurso y que esté disponible para otros usuarios, toque o haga clic en el icono de registro del cuadro de diálogo **Información del recurso**.

### Insertar un recurso mediante Finder o Explorer y utilizando la interfaz web {#check-in-an-asset-using-finder-or-explorer-and-using-web-interface}

Cuando haya terminado de editar los recursos, guárdelos en la aplicación de escritorio. En el menú contextual, seleccione **Más información de recursos** y haga clic en proteger.

Los recursos se cargan en el servidor [!DNL Experience Manager]. De forma opcional, puede comprobar el estado de la carga seleccionando **View Asset Status** en el icono de la bandeja del sistema. También puede registrar un recurso desde la interfaz web [!DNL Experience Manager]. Haga clic en los recursos extraídos o selecciónelos. En la barra de herramientas, haga clic en el icono de protección ![icono de protección](assets/do-not-localize/aemassets_icon_checkin.png).

Un recurso se carga automáticamente en [!DNL Experience Manager] después de guardar los cambios localmente. El registro pone el recurso a disposición de otros usuarios [!DNL Experience Manager] para su edición.

### Carga masiva de recursos y carpetas al servidor [!DNL Experience Manager] {#bulkupload}

Con la aplicación de escritorio [!DNL Experience Manager], puede cargar una carpeta entera que contenga recursos del directorio de archivos local a [!DNL Assets]. De este modo, todos los recursos de la carpeta se cargan de forma masiva, en lugar de tener que cargarlos de a una.

1. En la interfaz de usuario de Assets, pulse o haga clic en **Crear** en la barra de herramientas y elija **Cargar carpeta** en el menú.
1. Vaya a la carpeta que desee cargar y selecciónela.
1. Pulse o haga clic en Aceptar. El cuadro de diálogo Estado de los recursos muestra el estado de la carga.

   ![Consulte el estado de la carga en la ventana Estado del recurso](assets/aem_desktopapp_bulkupload_status.png)

   Consulte el estado de la carga en la ventana Estado del recurso

   >[!NOTE]
   >
   >Para pausar o cancelar la carga manualmente, toque o haga clic en el icono correspondiente.

1. Una vez que se haya cargado la carpeta, cierre el cuadro de diálogo y vaya a la interfaz de usuario de Assets. La carpeta cargada se muestra en la interfaz web.

Adobe no recomienda copiar, pegar o arrastrar un mayor número de archivos o carpetas anidadas, desde el sistema de archivos local, al área de red compartida. La aplicación no puede controlar el proceso de carga debido a limitaciones técnicas y el rendimiento es deficiente.

También puede seleccionar los archivos o carpetas que desea cargar en [!DNL Experience Manager] en Finder o Explorer, copiarlos en el portapapeles del sistema, navegar a la carpeta de destino en el área de uso compartido de la red y, en el menú contextual de la aplicación de escritorio [!DNL Experience Manager], seleccionar **Pegar recursos**. De este modo, la aplicación de escritorio [!DNL Experience Manager] comienza a cargar los recursos pegados de forma similar a la opción **Upload Folder** disponible en la interfaz web [!DNL Experience Manager].

>[!MORELIKETHIS]
>
>* [Solución de problemas [!DNL Experience Manager] de la aplicación de la aplicación de escritorio](troubleshoot-app-v1.md)

