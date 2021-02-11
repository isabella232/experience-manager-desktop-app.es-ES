---
title: Utilice [!DNL Experience Manager] versión 1.x de la aplicación de escritorio.
description: Aprenda a utilizar la versión 1.x de la aplicación de escritorio de Adobe Experience Manager y a optimizar su trabajo con recursos en el escritorio.
translation-type: tm+mt
source-git-commit: a25c1fa13895ae9eb7268e3e01c83a5f0b9d7d1d
workflow-type: tm+mt
source-wordcount: '2379'
ht-degree: 0%

---


# Utilice la aplicación de escritorio v1.x [!DNL Experience Manager] {#use-aem-desktop-app-v1x}

Al utilizar la aplicación, los recursos de [!DNL Experience Manager] son fácilmente accesibles en el escritorio local y se pueden utilizar en cualquier aplicación de escritorio. Los recursos se pueden revelar fácilmente en Mac Finder o el Explorador de Windows, abrirse en aplicaciones de escritorio y cambiarse localmente; los cambios se guardan de nuevo en [!DNL Experience Manager] con una nueva versión creada en el repositorio.

Esta integración permite que diversas funciones de la organización gestionen los activos de forma centralizada en Assets y accedan a ellos en el Creative Cloud y en otras aplicaciones, al tiempo que facilita el cumplimiento de las diversas normas, incluida la marca.

Las tareas clave que realiza con la aplicación de escritorio v1 [!DNL Experience Manager] incluyen:

1. [Conectar con  [!DNL Experience Manager] un servidor](#installandconnect)
1. [Abrir recursos directamente en el escritorio](#openondesktop)
1. [Editar y proteger recursos desde el escritorio](#workonassets)
1. [Carga masiva de recursos y carpetas](#bulkupload)

Para ver las distintas recomendaciones de administración y no, consulte las [prácticas recomendadas para usar la aplicación](best-practices-for-v1.md). Si tiene problemas con el uso de la aplicación, consulte cómo [solucionar problemas [!DNL Experience Manager] escritorio](troubleshoot-app-v1.md).

>[!NOTE]
>
>[!DNL Experience Manager] la aplicación de escritorio se introdujo en la versión  [!DNL Experience Manager] 6.1 y se llamó  [!DNL Experience Manager Assets Companion App].

## [!DNL Experience Manager] puntos de contacto de la aplicación de escritorio en el flujo de trabajo creativo  {#aem-desktop-app-touch-points-in-the-creative-workflow}

[!DNL Experience Manager] la aplicación de escritorio, junto con  [!DNL Assets], se integra en el flujo de trabajo creativo y oferta los siguientes puntos de contacto.

![[!DNL Experience Manager] aplicación de escritorio puntos de contacto en el flujo de trabajo creativo](assets/aem_desktopapp_workflow.png)

[!DNL Experience Manager] aplicación de escritorio puntos de contacto en el flujo de trabajo creativo

## Instale y conecte la aplicación al servidor [!DNL Experience Manager] {#installandconnect}

Antes de empezar a crear o editar los recursos creativos, conecte la aplicación de escritorio con el servidor [!DNL Assets] para descargar y cargar recursos en el repositorio. Realice las siguientes tareas:

1. [Instale la aplicación](#installapp).
1. [Configure sus ](#inapppref) preferencias y detalles de conexión.
1. [Conéctese a  [!DNL Experience Manager] ](#connect) un servidor y monte el repositorio de recursos como unidad local.
1. [Habilitar ](#desktopactions) acciones de escritorio en  [!DNL Experience Manager] servidor.

[!DNL Experience Manager] la aplicación de escritorio utiliza una conexión HTTPS para conectarse al  [!DNL Experience Manager] servidor y transferir sus recursos de forma segura y segura.

>[!NOTE]
>
>Para una parte o todos los pasos de instalación y configuración, es posible que necesite ayuda de su [!DNL Experience Manager] administrador o administrador del sistema.

### Instalar la aplicación {#installapp}

Para utilizar la aplicación de escritorio [!DNL Experience Manager], asegúrese de que la aplicación admite la versión del servidor [!DNL Experience Manager]. Descargue el archivo de instalación (binario) correspondiente al sistema operativo (Mac o Windows) e instale la aplicación.

La configuración detallada puede ser necesaria en función de las preferencias de red y sistema. Consulte [Instalación y configuración [!DNL Experience Manager] aplicación de escritorio](install-configure-app-v1.md) para obtener más información.

1. Vaya a la [[!DNL Experience Manager] página de descarga de la aplicación de escritorio](https://helpx.adobe.com/experience-manager/kb/download-companion-app.html) y descargue el binario apropiado para su sistema operativo.
1. Inicie el archivo de instalación descargado y siga las instrucciones que aparecen en pantalla para instalar la aplicación.

   >[!NOTE]
   >
   >Solo se puede instalar una instancia de la aplicación de escritorio [!DNL Experience Manager] y estar activa a la vez.

### Comprenda las opciones y preferencias en la aplicación {#inapppref}

La aplicación permite la conexión y desconexión de los servidores [!DNL Experience Manager], el estado de vista de las cargas, la administración de la caché local, etc. La configuración predeterminada funciona para un usuario típico de la aplicación. Puede ajustar la configuración para obtener más información sobre la aplicación y sobre la integración con el servidor [!DNL Experience Manager]. Los distintos ajustes se describen a continuación en detalle.

**Explorar** recursosAbra la unidad local en la que se monta el  [!DNL Assets] repositorio. En otras palabras, explore los recursos que ahora están disponibles en su equipo local.

**Estado** del recurso de vistaCuando se cargan los recursos modificados o se agregan nuevos al  [!DNL Assets] repositorio, la aplicación carga los recursos en segundo plano. La carga en segundo plano permite realizar operaciones sin problemas, sin tener que esperar a que finalice la carga, especialmente en el caso de los recursos de gran tamaño. Puede guardar los cambios localmente y olvidarlos. La aplicación tarda algún tiempo en enviar estos recursos al servidor, según el ancho de banda disponible. Puede comprobar el estado de la carga, junto con información más básica.

**** OpcionesHaga clic en las opciones de la bandeja de la aplicación de escritorio para acceder a la configuración e iniciar la aplicación cuando inicio el sistema; para conectarse al  [!DNL Experience Manager] servidor cuando se inicie la aplicación; y cambiar la letra de la unidad local donde  [!DNL Assets] está disponible después de montarla.

**Avanzadas > Administrar** cachéPuede controlar la cantidad de espacio en disco disponible para el almacenamiento en caché local. Los artefactos del servidor [!DNL Assets] se almacenan en caché localmente para una experiencia más fluida. Puede cambiar los valores predeterminados para adaptarlos a sus necesidades. Además, puede borrar la caché para recuperar todos los recursos de nuevo. Cuando borra la caché, conserva los cambios no guardados. Los recursos que no estén protegidos en el servidor [!DNL Experience Manager] se conservan y no se eliminan.

### Conectar con un servidor [!DNL Experience Manager] {#connect}

La aplicación admite la configuración proxy en Mac y Windows. La configuración se lee cuando la aplicación se inicio. Si modifica la configuración del proxy, reinicie la aplicación para que los cambios surtan efecto.

>[!NOTE]
>
>Si modifica la configuración del proxy, reinicie la aplicación para que los cambios surtan efecto. De lo contrario, la aplicación continúa utilizando el servidor proxy configurado anteriormente.

1. Inicie la aplicación de escritorio [!DNL Experience Manager]. Para asignar la instancia [!DNL Experience Manager] a la aplicación, especifique su servidor [!DNL Experience Manager] con el formato `https://[aem-server-url]:[port]`.

   ![Autentique en Mac y proporcione la URL  [!DNL Experience Manager] del servidor](assets/aem_desktop_app_server_url.png)

1. En la pantalla de inicio de sesión, especifique el nombre de usuario y la contraseña de su instancia. Para especificar una instancia [!DNL Experience Manager] alternativa, seleccione la opción **[!UICONTROL Alternate Login URL]**.

   ![Proporcione las credenciales  [!DNL Experience Manager] del servidor en la pantalla de inicio de sesión de la aplicación de  [!DNL Experience Manager] escritorio](assets/login_screen_v1.png)

### Habilitar acciones de escritorio en [!DNL Experience Manager] interfaz Web {#desktopactions}

Desde la interfaz de usuario de Recursos, puede explorar las ubicaciones de los recursos o el cierre de compra y abrir el recurso para editarlo en la aplicación de escritorio. Estas opciones se denominan acciones de escritorio y no están activadas de forma predeterminada. Siga estos pasos para habilitarlo.

1. En la interfaz de Recursos, toque o haga clic en el icono Usuario en la esquina superior derecha de la barra de herramientas.
1. Haga clic en **[!UICONTROL My Preferences]** para mostrar el cuadro de diálogo **[!UICONTROL Preferences]**.

   ![[!DNL Experience Manager] interfaz con preferencias de usuario](assets/aem_ui_user_preferences.png)

1. En el cuadro de diálogo Preferencias de usuario, seleccione **[!UICONTROL Show Desktop Actions For Assets]**. Haga clic **[!UICONTROL Accept]**.

   ![Marque  [!UICONTROL Show Desktop Actions For Assets] para habilitar las acciones de escritorio](assets/enable_desktop_actions.png)

   *Figura: Marque Mostrar acciones de escritorio para recursos para habilitar las acciones de escritorio.*

## Acceso y apertura de recursos en el escritorio {#openondesktop}

Al hacer clic en **Abrir** para abrir un recurso en un equipo local, la aplicación descarga el recurso en su caché interna. La aplicación inicia la aplicación de escritorio nativa asociada al tipo de archivo del recurso descargado.

En Mac, seleccione **Abrir** en el menú contextual para abrir un recurso a través de la aplicación de escritorio [!DNL Experience Manager]. En Windows, seleccione Abrir en Web en el menú contextual para abrir el recurso. En la ventana Estado del recurso, toque o haga clic en el icono ![Abrir en escritorio](assets/do-not-localize/aemassets_icon_openondesktop.png) para abrir el recurso.

Para archivos Adobe InDesign (INDD), seleccione **[!UICONTROL Open]** en el menú contextual. Al hacer clic en esta opción, la aplicación descarga los recursos vinculados en el sistema de archivos local y, a continuación, abre el archivo INDD en Adobe InDesign. Este método garantiza que los recursos necesarios estén disponibles localmente al editar el archivo INDD.

![Opciones del menú contextual para acceder y abrir recursos con la aplicación  [!DNL Experience Manager] de escritorio](assets/aem_desktopapp_mac_context_menu.png)

*Figura: Opciones de menú contextual para acceder a los recursos y abrirlos mediante la aplicación de  [!DNL Experience Manager] escritorio.*

>[!NOTE]
>
>En Windows, la configuración [predeterminada de Windows 7](https://support.microsoft.com/en-us/kb/2668751) evita que la aplicación de escritorio [!DNL Experience Manager] gestione recursos de más de 50 MB.

>[!NOTE]
>
>Adobe recomienda que vaya a Opciones de Vista de Finder en Mac y desactive las opciones **Mostrar información de elemento**, **Mostrar previsualización de elemento** y **Mostrar columna de previsualización** para la carpeta [!DNL Assets] montada. Mejora el rendimiento.

### Opciones adicionales en la interfaz [!DNL Experience Manager] {#additional-options-in-aem-assets}

Después de asignar el repositorio [!DNL Assets] a la unidad local, puede activar iconos adicionales y la función Carga de carpetas para que aparezcan en los recursos y carpetas asignados.

1. Abra la interfaz [!DNL Assets] y coloque el puntero sobre una carpeta o un recurso para mostrar las acciones de escritorio como acciones rápidas en la vista de tarjetas.

   ![En la interfaz de usuario de Recursos, abra el menú de acciones rápidas para ver las acciones de escritorio](assets/desktop_actions_in_card_view.png)

   *Figura: En la interfaz de usuario de Recursos, abra el menú de acciones rápidas para ver las acciones de escritorio.*

   Estas acciones de escritorio también están disponibles al hacer clic en la opción **Acciones de escritorio** de la barra de herramientas después de seleccionar el recurso o de la barra de herramientas de la página de recursos.

1. Para abrir el recurso en la aplicación de escritorio que está asociado con la extensión de archivo específica, haga clic en la **acción rápida Abrir en escritorio** ![Abrir en el icono de escritorio](assets/do-not-localize/aemassets_icon_openondesktop.png).

   Como alternativa, elija **Abrir** en el menú **Acciones de escritorio** de la barra de herramientas.

Para localizar el recurso concreto en el sistema de archivos local, haga clic en **Mostrar** acción rápida ![Icono de revelar](assets/do-not-localize/aemassets_reveal_icon.png). Como alternativa, elija **Mostrar** en el menú **Acciones de escritorio** de la barra de herramientas.

## Comprender los estados de los recursos {#understand-the-asset-statuses}

| ![Icono de aplicación predeterminado de Windows](assets/do-not-localize/win_default.png) | La aplicación está conectada al servidor y todos los recursos están sincronizados. |
--- |--- |
| ![Icono deshabilitado de Windows](assets/do-not-localize/win_disabled.png) | La aplicación se inicia pero no está conectada con el servidor. Es posible que algunos recursos estén pendientes de sincronización. |
| ![Icono de sincronización de archivos de Windows](assets/do-not-localize/win_sync.png) | Los recursos se están sincronizando. Los archivos se están cargando o descargando. Puede ver los estados exactos y pausar las transferencias desde la ventana Estado del activo. |
| ![Icono de reconexión de Windows](assets/do-not-localize/win_refresh.png) | La aplicación está intentando volver a conectarse. Potencialmente, los problemas de red están provocando que se desconecte. |

## Trabaje con sus recursos {#workonassets}

### Consulte los recursos de la [!DNL Experience Manager] interfaz Web {#check-out-assets-from-the-aem-web-interface}

[!DNL Assets] permite retirar recursos para editarlos y volver a protegerlos una vez que haya realizado los cambios. Después de retirar un recurso, solo podrá editarlo, anotarlo, publicarlo, moverlo o eliminarlo. Al retirar un recurso, éste se bloquea y se impide que otros usuarios realicen cualquiera de estas operaciones. Para poder extraer o registrar recursos, necesita tener acceso de escritura en ellos.

Existen dos formas de extraer recursos de la interfaz Web [!DNL Experience Manager]. Para obtener información detallada sobre el primer método, consulte [archivos de desprotección y protección de la interfaz de usuario de Assets](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/check-out-and-submit-assets.html). Siga estos pasos para ver los segundos métodos para retirar y abrir el recurso cuando se instale la aplicación de escritorio [!DNL Experience Manager].

1. Abra la interfaz [!DNL Assets] y coloque el puntero sobre una carpeta o un recurso para mostrar las acciones de escritorio como acciones rápidas en la vista de tarjetas.

   ![Propiedades, opción en Vista de tarjeta](assets/desktop_actions_in_card_view.png)

   Estas acciones de escritorio también están disponibles cuando toca o hace clic en el icono Acciones de escritorio en la barra de herramientas después de seleccionar el recurso o en la barra de herramientas de la página de recursos.

1. Para abrir el recurso, toque o haga clic en el icono Abrir en escritorio acción rápida ![Abrir en escritorio](assets/do-not-localize/aemassets_icon_openondesktop.png).

   También puede seleccionar Abrir en el menú Acciones de escritorio de la barra de herramientas.

   >[!NOTE]
   >
   >Cuando edita un archivo que se acaba de abrir y no se ha extraído, otros usuarios no llegan a saber que usted está actualizando un recurso.

1. Para abrir un recurso para editarlo en una aplicación de Adobe Creative Cloud, toque o haga clic en la acción rápida Editar escritorio ![Icono Editar escritorio](assets/do-not-localize/aemassets_icon_editdesktop.png). Esto también cierra la compra del recurso para editarlo. Después de terminar de editar, desproteja el recurso para actualizar los cambios en [!DNL Assets].

   También puede seleccionar Editar en el menú Acciones de escritorio de la barra de herramientas.

1. Seleccione la opción de menú Abrir. Los recursos seleccionados se abren en modo de previsualización.
1. Para editar los recursos, seleccione la opción Editar. Los recursos se abren en modo de edición.

### Consulte los recursos desde Finder en Mac OS {#check-out-assets-on-mac}

La aplicación le permite extraer archivos de recursos para evitar que otros usuarios modifiquen los archivos en los que está trabajando.

1. En el menú contextual de Mac, seleccione la opción Abrir carpeta de AEM Assets para abrir Finder.

   ![Opciones del menú contextual para acceder y abrir recursos con la aplicación  [!DNL Experience Manager] de escritorio](assets/aem_desktopapp_mac_context_menu.png)

   *Figura: Opciones de menú contextual para acceder a los recursos y abrirlos mediante la aplicación de  [!DNL Experience Manager] escritorio.*

1. Desplácese hasta el recurso que desee desproteger.
1. Haga clic con el botón derecho en el recurso y seleccione Más información de recursos en el menú contextual.
1. En el cuadro de diálogo Información del recurso, toque o haga clic en el icono Cierre de compra para extraer el recurso. El icono Cierre de compra se desplaza al icono de ingreso después de tocar o hacer clic en él.

   ![Explorar hasta el recurso para realizar la compra](assets/browse_assets_to_checkout.png)

1. Para desproteger el recurso para que esté disponible para otros usuarios, toque o haga clic en el icono de protección del cuadro de diálogo Información del recurso.

### Consulte los recursos en Windows {#check-out-assets-on-windows}

La aplicación le permite extraer archivos de recursos para evitar que otros usuarios modifiquen los archivos en los que está trabajando.

1. En el menú Contexto, seleccione Explorar recursos para abrir el Explorador.
1. En el Explorador, navegue a la ubicación del recurso que desee desproteger.
1. Haga clic con el botón derecho en el recurso y seleccione Abrir en Web en el menú contextual.
1. En el cuadro de diálogo Información del recurso, toque o haga clic en el icono Cierre de compra. El icono Cierre de compra se desplaza al icono de ingreso.

   ![Icono de cierre de compra](assets/checkout_icon_toggles.png)

1. Revise el recurso en el Explorador. El icono de bloqueo del recurso ![icono de bloqueo de recursos](assets/do-not-localize/aemassets_icon_lockcheckout.png) indica que ha extraído el recurso.

   >[!NOTE]
   >
   >El icono de candado puede aparecer después de un retraso. [!DNL Experience Manager] la aplicación de escritorio almacena en caché los recursos para un acceso rápido, por lo que puede tardar unos minutos en actualizar el estado de bloqueo.

1. Para desproteger el recurso para que esté disponible para otros usuarios, toque o haga clic en el icono de protección del cuadro de diálogo **Información del recurso**.

### Buscar un recurso mediante Finder o Explorer y utilizando la interfaz Web {#check-in-an-asset-using-finder-or-explorer-and-using-web-interface}

Cuando haya terminado de editar los recursos, guárdelos en la aplicación de escritorio. En el menú contextual, seleccione **Más información de recursos** y haga clic en Registrar.

Los recursos se cargan en el servidor [!DNL Experience Manager]. Si lo desea, puede comprobar el estado de la carga seleccionando **Estado del recurso de Vista** en el icono de la bandeja del sistema. También puede registrar un recurso desde la interfaz Web [!DNL Experience Manager]. Haga clic en los recursos extraídos o selecciónelos. En la barra de herramientas, haga clic en el icono de protección ![icono de protección](assets/do-not-localize/aemassets_icon_checkin.png).

Un recurso se carga automáticamente en [!DNL Experience Manager] después de guardar los cambios localmente. El registro pone el recurso a disposición de otros usuarios [!DNL Experience Manager] para su edición.

### Carga masiva de recursos y carpetas al servidor [!DNL Experience Manager] {#bulkupload}

Con la aplicación de escritorio [!DNL Experience Manager], puede cargar una carpeta completa que contenga recursos del directorio de archivos local a [!DNL Assets]. De este modo, todos los recursos de la carpeta se cargan de forma masiva en lugar de tener que cargarlos de uno en uno.

1. En la interfaz de usuario de Recursos, toque o haga clic en **Crear** en la barra de herramientas y elija **Cargar carpeta** en el menú.
1. Vaya a la carpeta que desee cargar y selecciónela.
1. Toque o haga clic en Aceptar. El cuadro de diálogo Estado de los recursos muestra el estado de la carga.

   ![Consulte el estado de la carga en la ventana Estado del recurso](assets/aem_desktopapp_bulkupload_status.png)

   Consulte el estado de la carga en la ventana Estado del recurso

   >[!NOTE]
   >
   >Para pausar o cancelar la carga manualmente, toque o haga clic en el icono correspondiente.

1. Después de cargar la carpeta, cierre el cuadro de diálogo y vaya a la interfaz de usuario de Recursos. La carpeta cargada se muestra en la interfaz web.

Adobe no recomienda copiar y pegar ni arrastrar un mayor número de archivos o carpetas anidadas, desde el sistema de archivos local, al área de uso compartido de la red. La aplicación no puede controlar el proceso de carga debido a limitaciones técnicas y el rendimiento es deficiente.

Como alternativa, seleccione los archivos y las carpetas que desea cargar en [!DNL Experience Manager] en Finder o Explorer, cópielos en el portapapeles del sistema, navegue a la carpeta de destinatario en el área de uso compartido de la red y, en el menú contextual de la aplicación de escritorio [!DNL Experience Manager], seleccione **Pegar recursos**. De este modo, [!DNL Experience Manager] inicios de la aplicación de escritorio al cargar los recursos pegados de forma similar a la opción **Cargar carpeta** disponible en la interfaz web [!DNL Experience Manager].

>[!MORELIKETHIS]
>
>* [ [!DNL Experience Manager] Solución de problemas de la aplicación de escritorio](troubleshoot-app-v1.md)

