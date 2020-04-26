---
title: Uso de la versión 1.x de la aplicación de escritorio de AEM
description: Obtenga información sobre cómo utilizar la versión 1.x de la aplicación de escritorio Adobe Experience Manager y optimizar su trabajo con recursos en el escritorio.
uuid: 55057617-89de-43cd-8419-1252a42ab2fb
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: 39d7bcad-d7b0-4978-a790-4cb68b8a7d6a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b92e47456f9e16c24eac43d1c5fef9a582f143b5

---


# Uso de la aplicación de escritorio de AEM v1.x {#use-aem-desktop-app-v1x}

Con la aplicación, los recursos de AEM son fácilmente accesibles en el escritorio local y se pueden utilizar en cualquier aplicación de escritorio. Los recursos se pueden revelar fácilmente en Mac Finder o el Explorador de Windows, abrirse en aplicaciones de escritorio y cambiarse localmente; los cambios se guardan de nuevo en AEM con una nueva versión creada en el repositorio.

Esta integración permite que varios roles de la organización gestionen los recursos de forma centralizada en Recursos AEM y accedan a ellos en Creative Cloud y otras aplicaciones, al tiempo que facilita el cumplimiento de los distintos estándares, incluida la marca.

Las tareas clave que realiza con la aplicación de escritorio v1 de AEM incluyen:

* [Conexión con un servidor AEM](#installandconnect)

* [Abrir recursos directamente en el escritorio](#openondesktop)
* [Editar y proteger recursos desde el escritorio](#workonassets)

* [Carga masiva de recursos y carpetas](#bulkupload)

Para ver las distintas opciones recomendadas, consulte las [prácticas recomendadas para usar la aplicación](best-practices-for-v1.md). Si tiene problemas con el uso de la aplicación, consulte cómo [solucionar problemas de AEM Desktop](troubleshoot-app-v1.md).

>[!NOTE]
>La aplicación de escritorio de AEM se introdujo en la versión 6.1 de AEM y se denominaba AEM Assets Companion App.

## Puntos de contacto de la aplicación de AEM Desktop en el flujo de trabajo creativo {#aem-desktop-app-touch-points-in-the-creative-workflow}

La aplicación de AEM Desktop, junto con Recursos AEM, se integra en el flujo de trabajo creativo y oferta los siguientes puntos de contacto.

![La aplicación de AEM Desktop remarca el flujo de trabajo creativo](assets/aem_desktopapp_workflow.png)

La aplicación de AEM Desktop remarca el flujo de trabajo creativo

## Instalación y conexión de la aplicación de escritorio de AEM al servidor de AEM {#installandconnect}

Antes de empezar a crear o editar los recursos creativos, conecte la aplicación de escritorio con el servidor de AEM Assets para descargar y cargar recursos en el repositorio. Realice las siguientes tareas:

1. [Instale la aplicación](#installapp).
1. [Configure sus preferencias](#inapppref) y detalles de conexión.
1. [Conéctese a un servidor](#connect) AEM y monte el repositorio de recursos como unidad local.
1. [Habilite acciones](#desktopactions) de escritorio en el servidor AEM.

La aplicación de escritorio de AEM utiliza una conexión HTTPS para conectarse al servidor AEM con el fin de transferir sus recursos de forma segura y segura.

>[!NOTE]
>Para todos o parte de los pasos de instalación y configuración, es posible que necesite ayuda del administrador de AEM o del sistema.

### Instalar la aplicación {#installapp}

Para utilizar la aplicación de escritorio de AEM, asegúrese de que la versión del servidor de AEM es compatible con la aplicación de AEM Desktop. Descargue el archivo de instalación (binario) correspondiente al sistema operativo (Mac o Windows) e instale la aplicación.

La configuración detallada puede ser necesaria en función de las preferencias de red y sistema. Consulte [Instalación y configuración de la aplicación](install-configure-app-v1.md) AEM Desktop para obtener más información.

1. Vaya a la página [de descarga de la aplicación de](https://helpx.adobe.com/experience-manager/kb/download-companion-app.html) AEM Desktop y descargue el binario adecuado para su sistema operativo.
1. Inicie el archivo de instalación descargado y siga las instrucciones que aparecen en pantalla para instalar la aplicación.

   >[!NOTE]
   >Solo se puede instalar y activar una instancia de la aplicación de escritorio de AEM a la vez.

### Comprenda las opciones y preferencias en la aplicación {#inapppref}

La aplicación permite que la configuración se conecte y desconecte de los servidores de AEM, el estado de vista de las cargas, la administración de la caché local, etc. La configuración predeterminada funciona para un usuario típico de la aplicación. Puede ajustar la configuración para sacar más provecho de la aplicación y de la integración con el servidor AEM. Los distintos ajustes se describen a continuación en detalle.

**Explorar recursos** Abra la unidad local en la que está montado el repositorio de AEM Assets. En otras palabras, explore los recursos que ahora están disponibles en su equipo local.

**Estado** de los recursos de Vista Cuando se cargan los recursos modificados o se añaden nuevos al repositorio de AEM Assets, la aplicación carga los recursos en segundo plano. La carga en segundo plano permite realizar operaciones sin problemas, sin tener que esperar a que finalice la carga, especialmente en el caso de los recursos de gran tamaño. Puede guardar los cambios localmente y olvidarlos. La aplicación tarda algún tiempo en enviar estos recursos al servidor, según el ancho de banda disponible. Puede comprobar el estado de la carga, junto con información más básica.

**Opciones** Haga clic o toque Opciones en la bandeja de aplicaciones de AEM Desktop para acceder a la configuración e iniciar la aplicación cuando el sistema lo inicio; para conectarse al servidor de AEM cuando se inicie la aplicación; y cambiar la letra de unidad local donde AEM Assets está disponible después de montarla.

**Avanzadas > Administrar caché** Puede controlar la cantidad de espacio en disco disponible para el almacenamiento en caché local. Los artefactos del servidor de AEM Assets se almacenan en caché localmente para una experiencia más fluida. Puede cambiar los valores predeterminados para adaptarlos a sus necesidades. Además, puede borrar la caché para recuperar todos los recursos de nuevo. Cuando borra la caché, conserva los cambios no guardados. Los recursos que no estén protegidos en el servidor AEM se conservan y no se eliminan.

### Conexión a un servidor AEM {#connect}

La aplicación admite la configuración proxy en Mac y Windows. La configuración se lee cuando la aplicación se inicio. Si modifica la configuración del proxy, reinicie la aplicación para que los cambios surtan efecto.

>[!NOTE]
>
>Si modifica la configuración del proxy, reinicie la aplicación para que los cambios surtan efecto. De lo contrario, la aplicación continúa utilizando el servidor proxy configurado anteriormente.

1. Inicie la aplicación de AEM Desktop. Para asignar la instancia de AEM a la aplicación, especifique el servidor de AEM en el formato `https://[aem-server-url]:[port]`.

   ![Autentique en Mac y proporcione la URL del servidor AEM](assets/aem_desktop_app_server_url.png)

1. En la pantalla de inicio de sesión, especifique el nombre de usuario y la contraseña de su instancia. Para especificar una instancia de AEM alternativa, seleccione la **[!UICONTROL Alternate Login URL]** opción.

   ![Proporcione las credenciales del servidor AEM en la pantalla de inicio de sesión de AEM Desktop](assets/chlimage_1-2.png)

### Habilitar acciones de escritorio en la interfaz web de AEM {#desktopactions}

Desde la interfaz de usuario de Recursos en un navegador, puede explorar las ubicaciones de los recursos o el cierre de compra y abrir el recurso para editarlo en la aplicación de escritorio. Estas opciones se denominan Acciones de escritorio y no están activadas de forma predeterminada. Siga estos pasos para habilitarlo.

1. En la consola Recursos, toque o haga clic en el icono **Usuario** de la barra de herramientas.
1. Toque o haga clic en el **[!UICONTROL My Preferences]** para mostrar el **[!UICONTROL Preferences]** cuadro de diálogo.
1. En el cuadro de diálogo Preferencias de usuario, seleccione **[!UICONTROL Show Desktop Actions For Assets]**. Toque o haga clic en **[!UICONTROL Accept]**.

   ![Marque Mostrar acciones de escritorio para recursos para habilitar las acciones de escritorio](assets/chlimage_1-3.png)

   Marque Mostrar acciones de escritorio para recursos para habilitar las acciones de escritorio

## Acceso y apertura de recursos en el escritorio {#openondesktop}

>[!NOTE]
>En Windows, la configuración [](https://support.microsoft.com/en-us/kb/2668751) predeterminada de Windows 7 impide que la aplicación de escritorio AEM gestione recursos de más de 50 MB.

### Revelar la ubicación de los recursos asignados desde la interfaz web de AEM {#reveal-the-location-of-mapped-assets-from-aem-web-interface}

Después de asignar el repositorio de Recursos AEM a la unidad local, puede activar iconos adicionales y la función Carga de carpetas para que aparezcan en los recursos y carpetas asignados.

1. Abra la interfaz de Recursos AEM y coloque el puntero sobre una carpeta o un recurso para mostrar las acciones de escritorio como acciones rápidas en la vista de tarjetas.

   ![En la interfaz de usuario de Recursos, abra el menú de acciones rápidas para ver las acciones de escritorio](assets/chlimage_1-4.png)

   En la interfaz de usuario de Recursos, abra el menú de acciones rápidas para ver las acciones de escritorio

   Estas acciones de escritorio también están disponibles cuando toca o hace clic en el icono Acciones **de** escritorio de la barra de herramientas después de seleccionar el recurso o de la barra de herramientas de la página de recursos.

1. Para abrir el recurso en la aplicación de escritorio asociada a la extensión de archivo específica, toque o haga clic en el icono **** Abrir en escritorio ![Acción rápida](assets/aemassets_icon_openondesktop.png)Abrir en escritorio.

   También puede seleccionar **Abrir** en el menú Acciones **de** escritorio de la barra de herramientas.

1. Toque o haga clic en el icono **** Descubrir ![acción rápida](assets/aemassets_reveal_icon.png) Descubrir para localizar el recurso concreto en el sistema de archivos local.

   También puede seleccionar **Mostrar** en el menú Acciones **de** escritorio de la barra de herramientas.

### Abrir recursos de AEM desde el Finder o el Explorador {#open-aem-assets-from-the-finder-or-the-explorer}

En Mac, seleccione Abrir en el menú contextual para abrir un recurso a través de AEM Desktop.

Para archivos de Adobe InDesign (INDD), seleccione **[!UICONTROL Open]** en el menú contextual. Al hacer clic en esta opción, la aplicación descarga los recursos vinculados en el sistema de archivos local y, a continuación, abre el archivo INDD en Adobe InDesign. Este método garantiza que los recursos necesarios estén disponibles localmente al editar el archivo INDD.

En Windows, seleccione Abrir en Web en el menú contextual para abrir el recurso. En la ventana Estado del recurso, toque o haga clic en el icono ![](assets/aemassets_icon_openondesktop.png) Abrir en escritorio para abrir el recurso.

![Opciones de menú contextual para acceder y abrir recursos con la aplicación AEM Desktop](assets/aem_desktopapp_mac_context_menu.png)

Opciones de menú contextual para acceder y abrir recursos con la aplicación AEM Desktop

### Comprender los estados de los recursos {#understand-the-asset-statuses}

| ![Icono de aplicación predeterminado de Windows](assets/win_default.png) | La aplicación está conectada al servidor y todos los recursos están sincronizados. |
|------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![Icono deshabilitado de Windows](assets/win_disabled.png) | La aplicación se inicia pero no está conectada con el servidor. Es posible que algunos recursos estén pendientes de sincronización. |
| ![Icono de sincronización de archivos de Windows](assets/win_sync.png) | Los recursos se están sincronizando. Los archivos se están cargando o descargando. Puede ver los estados exactos y pausar las transferencias desde la ventana Estado del activo. |
| ![Icono de reconexión de Windows](assets/win_refresh.png) | La aplicación está intentando volver a conectarse. Potencialmente, los problemas de red están provocando que se desconecte. |

## Trabajar con sus recursos {#workonassets}

### Extraer recursos de la interfaz web de AEM {#check-out-assets-from-the-aem-web-interface}

Recursos AEM le permite retirar recursos para editarlos y volver a protegerlos después de realizar los cambios. Después de retirar un recurso, solo podrá editarlo, anotarlo, publicarlo, moverlo o eliminarlo. Al retirar un recurso, éste se bloquea y se impide que otros usuarios realicen cualquiera de estas operaciones. Para poder extraer o registrar recursos, necesita tener acceso de escritura en ellos.

Existen dos formas de extraer recursos de la interfaz web de AEM. Para obtener información detallada sobre el primer método, consulte [protección y cierre de compra de archivos desde la interfaz de usuario](https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/check-out-and-submit-assets.html)de Assets. Siga estos pasos para ver los segundos métodos para desproteger y abrir el recurso cuando la aplicación AEM Desktop esté instalada.

1. Abra la interfaz de Recursos AEM y coloque el puntero sobre una carpeta o un recurso para mostrar las acciones de escritorio como acciones rápidas en la vista de tarjetas.

   ![Propiedades, opción en Vista de tarjeta](assets/chlimage_1-4.png)

   Estas acciones de escritorio también están disponibles cuando toca o hace clic en el icono Acciones de escritorio en la barra de herramientas después de seleccionar el recurso o en la barra de herramientas de la página de recursos.

1. Para abrir el recurso, toque o haga clic en el icono ![Abrir en escritorio Acción rápida](assets/aemassets_icon_openondesktop.png)Abrir en escritorio.

   También puede seleccionar Abrir en el menú Acciones de escritorio de la barra de herramientas.

   >[!NOTE]
   >Cuando edita un archivo que se acaba de abrir y no se ha extraído, otros usuarios no llegan a saber que usted está actualizando un recurso.

1. Para abrir un recurso para editarlo en una aplicación de Adobe Creative Cloud, toque o haga clic en el icono ![Editar escritorio acción rápida](assets/aemassets_icon_editdesktop.png)Editar escritorio. Esto también cierra la compra del recurso para editarlo. Cuando termine de editar, desproteja el recurso para actualizar los cambios en Recursos AEM.

   También puede seleccionar Editar en el menú Acciones de escritorio de la barra de herramientas.

1. Seleccione la opción de menú Abrir. Los recursos seleccionados se abren en modo de previsualización.
1. Para editar los recursos, seleccione la opción Editar. Los recursos se abren en modo de edición.

### Comprobación de recursos en Mac {#check-out-assets-on-mac}

La aplicación le permite extraer archivos de recursos para evitar que otros usuarios modifiquen los archivos en los que está trabajando.

1. En el menú contextual de Mac, seleccione Abrir carpeta de AEM Assets para abrir Finder.

   ![Opciones de menú contextual para acceder y abrir recursos con la aplicación AEM Desktop](assets/aem_desktopapp_mac_context_menu.png)

   Opciones de menú contextual para acceder y abrir recursos con la aplicación AEM Desktop

1. Desplácese hasta el recurso que desee desproteger.

   ![Abrir en el menú contextual de Recursos AEM en Mac](assets/chlimage_1-5.png)

1. Haga clic con el botón derecho en el recurso y seleccione Más información de recursos en el menú contextual.
1. En el cuadro de diálogo Información del recurso, toque o haga clic en el icono Cierre de compra para extraer el recurso. El icono Cierre de compra se desplaza al icono de ingreso después de tocar o hacer clic en él.

   ![Explorar hasta el recurso para realizar la compra](assets/chlimage_1-6.png)

1. Para desproteger el recurso para que esté disponible para otros usuarios, toque o haga clic en el icono de protección del cuadro de diálogo Información del recurso.

### Proteger recursos en Windows {#check-out-assets-on-windows}

La aplicación le permite extraer archivos de recursos para evitar que otros usuarios modifiquen los archivos en los que está trabajando.

1. En el menú Contexto, seleccione Explorar recursos para abrir el Explorador.
1. En el Explorador, navegue a la ubicación del recurso que desee desproteger.

   ![Icono de cierre de compra](assets/chlimage_1-7.png)

1. Haga clic con el botón derecho en el recurso y seleccione Abrir en Web en el menú contextual.
1. En el cuadro de diálogo Información del recurso, toque o haga clic en el icono Cierre de compra. El icono Cierre de compra se desplaza al icono de ingreso.

   ![Icono de cierre de compra](assets/chlimage_1-8.png)

1. Revise el recurso en el Explorador. El icono de candado del icono ![de candado de](assets/aemassets_icon_lockcheckout.png) recursos indica que ha extraído el recurso.

   >[!NOTE]
   >El icono de candado puede aparecer después de unos minutos de retraso. La aplicación de AEM Desktop almacena en caché los recursos para un acceso rápido, por lo que puede tardar unos minutos en actualizar el estado de bloqueo.

1. Para desproteger el recurso para que esté disponible para otros usuarios, toque o haga clic en el icono de desprotección del cuadro de diálogo Información **de** recurso.

### Buscar un recurso mediante Finder o Explorer y mediante la interfaz Web {#check-in-an-asset-using-finder-or-explorer-and-using-web-interface}

Cuando haya terminado de editar los recursos, guárdelos en la aplicación de escritorio. En el menú contextual, seleccione Más información de recursos y toque o haga clic en el registro.

Los recursos se cargan en el servidor AEM. Si lo desea, puede comprobar el estado de la carga seleccionando Estado del recurso de Vista en el icono de bandeja.

![Ventana de estado de carga y transferencia de archivos de la aplicación de AEM Desktop](assets/aem_desktopapp_upload_status.png)

También puede registrar un recurso desde la interfaz web de AEM. Toque o haga clic en los recursos extraídos o selecciónelos. En la barra de herramientas, toque o haga clic en el icono de ![protección](assets/aemassets_icon_checkin.png).

### Carga masiva de recursos y carpetas en el servidor AEM {#bulkupload}

Con AEM Desktop, puede cargar una carpeta completa que contenga recursos del directorio de archivos local en Recursos AEM. De este modo, todos los recursos de la carpeta se cargan de forma masiva en lugar de tener que cargarlos de uno en uno.

1. En la interfaz de usuario de Recursos, toque o haga clic en **Crear** en la barra de herramientas y elija **Cargar carpeta** en el menú.
1. Vaya a la carpeta que desee cargar y selecciónela.
1. Toque o haga clic en Aceptar. El cuadro de diálogo Estado de los recursos muestra el estado de la carga.

   ![Consulte el estado de la carga en la ventana Estado del recurso](assets/aem_desktopapp_bulkupload_status.png)

   Consulte el estado de la carga en la ventana Estado del recurso

   >[!NOTE]
   >Para pausar o cancelar la carga manualmente, toque o haga clic en el icono correspondiente.

1. Después de cargar la carpeta, cierre el cuadro de diálogo y vaya a la interfaz de usuario de Recursos. La carpeta cargada se muestra en la interfaz web.

Tenga en cuenta que *no se recomienda* copiar y pegar o arrastrar y soltar un mayor número de archivos o carpetas anidadas del disco local en Finder o Explorer en el área de uso compartido de red asignada por la aplicación de escritorio de AEM. Es mucho menos fiable que la funcionalidad Cargar carpeta descrita anteriormente.

Otra alternativa si prefiere trabajar en el escritorio es seleccionar los archivos o carpetas que desea cargar a AEM en Finder o Explorer, copiarlos en el portapapeles del sistema y, a continuación, navegar a la carpeta de destinatario en el área de uso compartido de la red, y en el menú contextual de la aplicación de escritorio de AEM, seleccione &quot;Pegar recursos&quot;. De este modo, la aplicación de escritorio de AEM inicio cargar los recursos pegados de forma similar a la carpeta de carga descrita anteriormente.

>[!MORELIKETHIS]
>
>* [Introducción a la aplicación de escritorio de AEM](https://helpx.adobe.com/customer-care-office-hours/aem/desktop-app.html)
>* [Obtenga información sobre la llegada y la salida con la aplicación de escritorio de AEM](https://docs.adobe.com/content/help/en/experience-manager-learn/assets/collaboration/checkin-checkout-technical-video-understand.html)
>* [Solución de problemas de la aplicación AEM Desktop](troubleshoot-app-v1.md)

