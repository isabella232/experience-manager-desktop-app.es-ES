---
title: Uso de la aplicación de escritorio Adobe Experience Manager
description: Aprenda a instalar y utilizar la aplicación de escritorio Adobe Experience Manager para trabajar con los recursos DAM de Adobe Experience Manager directamente desde el escritorio de Windows o Mac. Conozca las prácticas recomendadas y la información de solución de problemas.
uuid: 55057617-89de-43cd-8419-1252a42ab2fb
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: 39d7bcad-d7b0-4978-a790-4cb68b8a7d6a
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: b92e47456f9e16c24eac43d1c5fef9a582f143b5

---


# Use Adobe Experience Manager desktop app {#use-aem-desktop-app-v2}

Utilice la aplicación de escritorio Adobe Experience Manager (AEM) para acceder fácilmente a los recursos DAM de Adobe Experience Manager en el escritorio local y utilizar estos recursos en cualquier aplicación de escritorio. Puede abrir los recursos en aplicaciones de escritorio y editarlos localmente; vuelva a cargar los cambios en Experience Manager con control de versiones para compartirlos con otros usuarios. También puede cargar nuevos archivos y jerarquías de carpetas en Experience Manager, crear carpetas y eliminar recursos o carpetas de Experience Manager DAM.

La integración permite que diversas funciones de la organización gestionen los recursos de forma centralizada en Experience Manager Assets y accedan a los recursos en el escritorio local en las aplicaciones nativas en Windows o Mac OS.

Cuando abra la aplicación después de cerrar la sesión o por primera vez, proporcione la URL de su servidor de Experience Manager. Haga clic en Conectar. Proporcione sus credenciales para conectar la aplicación con el servidor.

Las tareas clave que realiza con la aplicación de escritorio de Experience Manager son:

![Flujos de trabajo y tareas que puede realizar con la](assets/aem_desktop_app_usecases_v2.png "aplicación de escritorio de Experience ManagerFlujos de trabajo y tareas que puede realizar con la aplicación")de escritorio de Adobe Experience Manager Descargue [este](assets/aem_desktop_app_usecases_print.pdf) archivo PDF listo para imprimir.

## Funcionamiento de la aplicación de escritorio {#how-app-works2}

Antes de realizar el inicio con la aplicación, debe comprender [cómo funciona](release-notes.md#how-app-works)la aplicación. Además, familiarícese con los siguientes términos:

* **[!UICONTROL Desktop Actions]**:: Desde la interfaz web Recursos, desde dentro de un navegador, puede explorar las ubicaciones de los recursos o la retirada y abrir el recurso para editarlo en la aplicación de escritorio nativa. Estas acciones están disponibles en la interfaz web y utilizan la funcionalidad de la aplicación de escritorio. Consulte [cómo habilitar las acciones](using.md#desktopactions-v2)de escritorio.

* El estado del archivo es **[!UICONTROL Cloud Only]**: Estos recursos no se descargan en el equipo local y solo están disponibles en el servidor de Experience Manager.

* El estado del archivo es **[!UICONTROL Available locally]**: Los recursos se descargan y están disponibles en el equipo local tal como están. Los recursos no se modifican.

* El estado del archivo es **[!UICONTROL Edited locally]**: Estos recursos se modifican localmente y los cambios permanecen en el servidor de Experience Manager cargado. Después de cargar, el estado cambia a [!UICONTROL Available locally]. Consulte [Edición de recursos](using.md#edit-assets-upload-updated-assets).

* El estado del archivo es **[!UICONTROL Editing conflict]**: Si usted y otros usuarios modifican un recurso simultáneamente, la aplicación indica que se ha producido un conflicto de edición. La aplicación también ofrece opciones para conservar o descartar los cambios. Consulte [cómo evitar conflictos](using.md#adv-workflow-collaborate-avoid-conflicts)de edición.

* El estado del archivo es **[!UICONTROL Modified remotely]**: La aplicación indica si un recurso que ha descargado ha cambiado en el servidor de Experience Manager. La aplicación también ofrece la opción de descargar la versión más reciente y actualizar la copia local. Consulte [cómo evitar conflictos](using.md#adv-workflow-collaborate-avoid-conflicts)de edición.

* **[!UICONTROL Check-out]**:: Si está editando un archivo o tiene intención de editarlo, puede alternar el estado para extraerlo. Agrega un icono de candado al recurso en la aplicación y en la interfaz web de AEM. El icono de candado indica a los demás usuarios que eviten editar simultáneamente el mismo recurso, ya que provoca un conflicto de edición.

* **[!UICONTROL Check-in]**:: Marque el recurso como seguro para que otros usuarios lo editen sin provocar un conflicto de edición. Al cargar los cambios, el icono de bloqueo se elimina automáticamente. Al cambiar el estado de la protección también se elimina el icono de bloqueo, aunque se recomienda no registrarse manualmente sin cargar los cambios. Si descarta los cambios, active manualmente la protección.

* **[!UICONTROL Open]** acción: Basta con abrir el recurso para previsualización en la aplicación nativa. No se recomienda editar el recurso mediante esta acción, ya que no cierra la compra del recurso y otros usuarios pueden realizar modificaciones que conduzcan a conflictos de edición.

* **[!UICONTROL Edit]** acción: Utilice la acción para modificar la imagen. Al hacer clic en [!UICONTROL Edit] acción, se extrae automáticamente el recurso y se agrega un icono de candado al recurso. Después de hacer clic en Editar, si no desea editar el recurso, haga clic en [!UICONTROL Toggle check-in]. Para eliminar, cambiar el nombre o mover recursos en la jerarquía de carpetas de AEM DAM, utilice las acciones de la interfaz web de AEM y no la acción de edición.

* **[!UICONTROL Download]** acción: Descargue el recurso en el equipo local. Ahora puede descargar los recursos y editarlos más tarde; trabajar sin conexión y cargar los cambios más tarde. Los recursos se descargan en una carpeta de caché del sistema de archivos.

* **[!UICONTROL Reveal File]** o **[!UICONTROL Reveal Folder]** acción: Mientras los recursos se descargan en una carpeta de caché local, la aplicación imita una unidad de red local y proporciona una ruta local para cada recurso. Para conocer esta ruta, utilice la opción de revelación adecuada en la aplicación. Se requiere una acción de revelar para colocar recursos en la aplicación Creative Cloud. Consulte [Colocación de recursos](using.md#place-assets-in-native-documents).

* **[!UICONTROL Open In Web]** acción: Para vista del recurso en la interfaz web de AEM, ábralo en web. Puede iniciar más flujos de trabajo desde la interfaz de AEM, como actualizar metadatos o detección de recursos.

* **[!UICONTROL Delete]** acción: Elimine el recurso del repositorio de AEM DAM. La acción elimina la copia original del recurso en el servidor AEM. Si solo desea descartar las modificaciones del recurso local, consulte [Descartar cambios](using.md#edit-assets-upload-updated-assets).

* **[!UICONTROL Upload Changes]**:: La aplicación de escritorio carga el recurso actualizado solo cuando se carga explícitamente en el servidor AEM. Al guardar las ediciones, los cambios solo se guardan en el equipo local. Al cargar, el recurso se protege automáticamente y se elimina el icono de bloqueo. Consulte [Edición de recursos](using.md#edit-assets-upload-updated-assets).

## Habilitar acciones de escritorio en la interfaz web de AEM {#desktopactions-v2}

Desde la interfaz de usuario de Recursos en un navegador, puede explorar las ubicaciones de los recursos o el cierre de compra y abrir el recurso para editarlo en la aplicación de escritorio. Estas opciones se llaman [!UICONTROL Desktop Actions] y no están activadas de forma predeterminada. Para habilitarlo, siga estos pasos.

1. En la consola Recursos, toque o haga clic en el **[!UICONTROL User]** icono de la barra de herramientas.
1. Toque o haga clic en el **[!UICONTROL My Preferences]** para mostrar el **[!UICONTROL Preferences]** cuadro de diálogo.
1. En el cuadro de diálogo Preferencias de usuario, seleccione **[!UICONTROL Show Desktop Actions For Assets]**. Toque o haga clic en **[!UICONTROL Accept]**.

   ![Marque Mostrar acciones de escritorio para recursos para habilitar las acciones de escritorio](assets/chlimage_1-3.png)

   Marque [!UICONTROL Show Desktop Actions For Assets] para habilitar las acciones de escritorio

## Examinar, buscar y previsualización de recursos {#browse-search-preview-assets}

Puede buscar, buscar y previsualización los recursos disponibles en el repositorio de AEM desde la aplicación de escritorio. Pruebe lo siguiente en la aplicación:

1. Vaya a una carpeta y vea información básica sobre los recursos disponibles en ella, junto con miniaturas pequeñas de todos los recursos.

   ![Explorar los archivos y](assets/browse_folder_da2.png "carpetas DAMojear los archivos y carpetas DAM")

1. Para vista de más información y una miniatura más grande de un recurso individual, haga clic en el nombre del archivo.

   ![Ver una previsualización más grande de un recurso y](assets/large_preview_actions_da2.png "accionesVer una previsualización más grande de un recurso y acciones")

1. Haga clic **[!UICONTROL Open]** o **[!UICONTROL Edit]** para descargar el archivo localmente y solo tiene que vista o editarlo en la aplicación nativa, respectivamente.
1. Busque con palabras clave para encontrar un recurso relacionado en el repositorio de AEM. Use `?` y `*` como comodines. Estos comodines sustituyen a un solo carácter o a varios caracteres, respectivamente. Filtre y ordene los resultados según sea necesario.

   ![Búsqueda de muestra con](assets/search_wildcard_da2.png "comodín asterisco Búsqueda de muestra con comodín asterisco")

   ![Otra búsqueda de muestra utilizando](assets/search_wildcard2_da2.png "comodín asteriscoOtra búsqueda de muestra con una ubicación diferente del comodín asterisco")

>[!NOTE]
>
>La aplicación muestra los recursos cumpliendo los criterios de búsqueda en varios campos de metadatos y no solo en el título del recurso o en el nombre del archivo.

## Descargar recursos {#download-assets}

Puede descargar los recursos en el sistema de archivos local. La aplicación obtiene los recursos del servidor AEM y guarda la misma copia en el sistema de archivos local.

Haga clic en el icono ![](assets/do-not-localize/more2_da2.png) Más opciones para ver las opciones y haga clic en el icono ![](assets/do-not-localize/download_cloud_da2.png) Descargar para descargar.

![Opción de descarga de un](assets/download_option_da2.png "recursoOpción de descarga de un recurso")

>[!NOTE]
>
>Al descargar o cargar un archivo grande o varios archivos, la aplicación desactiva las acciones en recursos y carpetas. Las acciones están disponibles cuando se completa la descarga o carga.

Si el tamaño de la cola es grande o si tiene algún problema de red, la descarga de varios recursos puede producir un rendimiento deficiente. Además, es posible que, sin saberlo, coloque muchos recursos en la cola para descargarlos al descargar una carpeta. Para evitar largos tiempos de espera, la aplicación restringe el número de recursos descargados de una sola vez. Para saber cómo configurarlo, consulte [Configuración de preferencias](install-upgrade.md#set-preferences). Incluso por debajo de este límite, la aplicación puede buscar a veces una confirmación antes de descargar una carpeta aparentemente grande.

![La aplicación confirma la descarga de un número relativamente grande de](assets/download_confirmation_da2.png "recursosApp confirma la descarga de un número relativamente grande de recursos")

Si las carpetas están seleccionadas y descargadas, la aplicación solo descarga los recursos almacenados directamente en las carpetas de AEM. No descarga recursos de subcarpetas automáticamente.

## Abrir recursos en el escritorio {#openondesktop-v2}

Puede abrir los recursos remotos para visualizarlos en la aplicación nativa. Los recursos se descargan en una carpeta local y se inician en la aplicación nativa asociada al formato de archivo. Puede cambiar la aplicación nativa para abrir tipos de archivo específicos (extensiones) en su Mac o Windows.

Haga clic en **[!UICONTROL Open]** en el menú Recurso. El recurso se descarga localmente y se abre en la aplicación nativa. Compruebe el progreso de la descarga y la velocidad de transferencia de los recursos de gran tamaño en la barra de estado.

<!-- ![Download progress bar for large-sized assets](assets/download_status_bar_da2.png "Download progress bar for large-sized assets")
-->

>[!NOTE]
>
>Si los cambios esperados no se reflejan en la aplicación, haga clic en el icono de actualización ![Icono](assets/do-not-localize/refresh.png) de actualización o haga clic con el botón derecho en la interfaz de la aplicación y haga clic en **[!UICONTROL Refresh]**. Las acciones no están disponibles mientras hay descargas o cargas más grandes en curso.

Para abrir la carpeta de descarga local de un recurso, haga clic en el icono ![](assets/do-not-localize/more2_da2.png) Más acciones y luego en ![Mostrar acción de icono](assets/do-not-localize/reveal_action2_da2.png)**[!UICONTROL Reveal File]** .

## Uso o colocación de recursos en documentos nativos {#place-assets-in-native-documents}

En algunos casos, por ejemplo, al colocar un recurso en un documento nativo, se accede a un archivo en el Explorador de Windows o en el Buscador de Mac. Para llegar a la ubicación del sistema de archivos del archivo descargado localmente, utilice la opción de icono ![](assets/do-not-localize/reveal_action2_da2.png) Mostrar **[!UICONTROL Reveal File]** .

![Acción Revelar archivo para un](assets/revealfile_action_da2.png "recurso Acción Revelar archivo para un recurso")

Haga clic **[!UICONTROL Reveal File]**, o **[!UICONTROL Reveal Folder]** en una carpeta, para abrir el Explorador de Windows o el Buscador de Mac con el archivo o la carpeta preseleccionados en el equipo local. La opción resulta útil, por ejemplo, para colocar los archivos AEM en las aplicaciones nativas que admiten la colocación o vinculación de archivos locales. Para ver cómo colocar archivos en Adobe InDesign, consulte [Colocación de gráficos](https://helpx.adobe.com/indesign/using/placing-graphics.html).

La **[!UICONTROL Reveal File]** acción abre un recurso compartido de red local, que solo muestra los recursos disponibles localmente, es decir, muestra los recursos que se han revelado, descargado o abierto/editado con la aplicación. El recurso compartido de red local no carga ningún cambio en AEM. Para cargar los cambios, use **[!UICONTROL Upload Changes]** o **[!UICONTROL Upload]** acciones explícitamente en la aplicación.

>[!NOTE]
>
>Para la compatibilidad con versiones anteriores de la aplicación de escritorio v1.x de AEM, los archivos mostrados se proporcionan desde un recurso compartido de red local, lo que solo muestra los archivos disponibles localmente. Las rutas de escritorio de los archivos revelados son las mismas que las rutas creadas por la aplicación v1.x.

>[!CAUTION]
>
>No utilice **[!UICONTROL Reveal File]** la opción para editar recursos en aplicaciones nativas. En su lugar, utilice las **[!UICONTROL Edit]** acciones. Para obtener más información, consulte Flujo de trabajo [avanzado: colaborar en los mismos archivos y evitar conflictos](#adv-workflow-collaborate-avoid-conflicts)de edición.

## Editar recursos y cargar recursos actualizados en AEM {#edit-assets-upload-updated-assets}

Abra recursos para editarlos cuando desee realizar cambios y cargue los recursos actualizados en el servidor AEM. Para evitar conflictos con las ediciones de otros usuarios, utilice la aplicación para iniciar una sesión de edición. Antes de editar el inicio, asegúrese de que el recurso no tiene un icono de candado, es decir, que otro usuario no está editando el recurso.

Para editar un recurso, busque el recurso o navegue hasta su ubicación. Haga clic en el icono ![](assets/do-not-localize/more2_da2.png) Más y luego en **[!UICONTROL Edit]**.

Utilice **[!UICONTROL Toggle Check-out]** para bloquear el recurso para evitar conflictos con ediciones de otros usuarios en las dos situaciones siguientes:

* Ha empezado a editar un recurso sin desprotegerlo primero (por ejemplo, solo abriéndolo).
* Tiene la intención de editar un inicio en breve y no desea que otros usuarios lo editen.

Una vez que haya terminado de realizar las ediciones, la aplicación muestra el estado de los **[!UICONTROL Edited Locally]** recursos modificados. Todos los cambios guardados en los recursos son solo locales hasta que se carguen los cambios en AEM. Para cargar un recurso individual o algunos recursos uno a uno, haga clic en **[!UICONTROL Upload Changes]** las opciones de un recurso. Crea una versión del recurso en AEM. Con la interfaz web de Recursos AEM, puede ver el historial de recursos en la vista [de la](https://docs.adobe.com/content/help/en/experience-manager-65/assets/using/activity-stream.html)línea de tiempo.

![Opción de carga de cambios en la opción de cambios](assets/upload_changes_single1_da2.png "appCargar en la aplicación")

![Opción de carga de cambios al ver una previsualización grande de un](assets/upload_changes_single2_da2.png "recursoOpción de carga de cambios al ver una previsualización grande de un recurso")

Para conocer las prácticas recomendadas sobre la edición en colaboración, consulte Flujo de trabajo [avanzado: colaborar en los mismos archivos y evitar conflictos](#adv-workflow-collaborate-avoid-conflicts)de edición.

En los siguientes casos, es posible que desee descartar los cambios y las ediciones en el recurso local. Haga clic **[!UICONTROL Discard Changes]**.

* Si no desea guardar los cambios locales en AEM.
* Inicio realizando cambios en el recurso original después de guardar algunos cambios.
* Deje de editar el recurso porque ya no lo necesita.

Si es necesario, active la desprotección. El recurso actualizado se elimina de la carpeta de caché local y se descarga de nuevo al editarlo o abrirlo.

## Carga y adición de nuevos recursos a AEM {#upload-and-add-new-assets-to-aem}

Los usuarios pueden agregar recursos nuevos al repositorio de DAM. Por ejemplo, puede ser un fotógrafo o contratista de la agencia que quiera añadir un gran número de fotos de una sesión fotográfica al repositorio de AEM. Para añadir contenido nuevo a AEM, haga clic en el icono ![](assets/do-not-localize/upload_to_cloud_da2.png) Cargar en la nube en la barra superior de la aplicación. Busque los archivos de recursos en el sistema de archivos local y haga clic en **[!UICONTROL Select]**. La aplicación inicio la carga del recurso y muestra una barra de progreso en la parte inferior si el recurso tarda más en cargarse. No utilice espacios en blanco ni caracteres no válidos al crear o cargar carpetas. Consulte una lista de caracteres en [Creación de carpetas en Recursos](https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/managing-assets-touch-ui.html#Creatingfolders)AEM.

<!-- ![Download progress bar for large-sized assets](assets/upload_status_da2.png "Download progress bar for large-sized assets")
-->

Puede cargar carpetas o archivos individuales desde el sistema de archivos local. La jerarquía de una carpeta se conserva al cargarse. Antes de cargar los recursos de forma masiva, consulte Cargas [masivas](#bulk-upload-assets).

Para vista de la lista de los recursos transferidos en una sesión determinada, haga clic en **[!UICONTROL View]** > **[!UICONTROL Assets transfers]**. La lista le permite realizar vistas y comprobar rápidamente las transferencias de archivos de la sesión actual.

![Lista de los activos transferidos en una](assets/assets_transfered_da2.png "sesión determinada Lista de los activos transferidos en una sesión determinada")

Puede controlar la concurrencia de carga (aceleración) en **[!UICONTROL Preferences]** > **[!UICONTROL Upload acceleration]** . La mayor concurrencia suele proporcionar cargas más rápidas, pero puede requerir muchos recursos, lo que consume más potencia de procesamiento de la máquina local. Si experimenta un sistema lento, vuelva a intentar cargar con un valor de concurrencia inferior.

>[!NOTE]
>
>La lista de transferencia no es persistente y no está disponible si sale de la aplicación y la vuelve a abrir.

>[!NOTE]
>
>Si los archivos no se pueden cargar y se está conectando a AEM 6.5.1 o a una implementación posterior, consulte esta información [sobre la](troubleshoot.md#upload-fails)solución de problemas.

## Trabajar con varios recursos {#work-with-multiple-assets}

Los usuarios pueden trabajar fácilmente con varios recursos y administrarlos mediante acciones como cargar todas las ediciones de una sola vez o cargar carpetas anidadas en pocos clics.

### Examinar carpetas grandes {#browse-large-folders}

Al trabajar con carpetas que contienen muchos recursos, desplácese hasta la vista de más recursos. Para desplazarse con el teclado, pulse la ficha unas cuantas veces para seleccionar el recurso en la parte superior. Observe el recurso resaltado para saber cuándo está seleccionado. Ahora utilice la tecla de flecha abajo para desplazarse por la lista de recursos.

### Acciones rápidas para recursos seleccionados {#quick-actions-for-selected-assets}

Haga clic en la miniatura de algunos recursos para seleccionarlos. Para seleccionar todos los recursos, haga clic en la casilla de verificación de la barra superior de la aplicación. El conjunto de acciones aplicables a todos los recursos seleccionados de forma colectiva se muestra en una barra de herramientas en la parte inferior de la aplicación.

![La barra de herramientas de la parte inferior muestra las acciones relevantes para los](assets/actions_bottom_toolbar1_da2.png "recursos seleccionadosLa barra de herramientas de la parte inferior muestra las acciones comunes para los recursos seleccionados")

![No hay acciones en la barra de herramientas cuando no hay acciones comunes para la](assets/actions_bottom_toolbar2_da2.png "selecciónNo hay acciones en la barra de herramientas cuando no hay acciones comunes para la selección")

Las acciones disponibles en la barra de herramientas de la parte inferior dependen del estado de los archivos seleccionados. Por ejemplo, si sólo selecciona **[!UICONTROL Edited Locally]** archivos, verá el **[!UICONTROL Upload Changes]** icono . Si selecciona una combinación de **[!UICONTROL Edited locally]** y **[!UICONTROL Cloud only]**, la **[!UICONTROL Upload Changes]** acción no está disponible.

### Buscar todas las imágenes editadas {#find-all-edited-images}

La aplicación proporciona una vista, llamada **[!UICONTROL Edited locally]**, para que pueda acceder rápidamente a todos los archivos que descargó localmente (mediante [!UICONTROL Open] acciones o [!UICONTROL Edit] ) y que luego modificó. La aplicación le permite seleccionar todos los recursos editados localmente y cargar los cambios en unos pocos clics. Esta vista también muestra los recursos editados localmente que tienen un conflicto de edición.

![Filtrar para ver todos los](assets/edited_locally_filter_da2.png "recursos editados localmenteFiltrar para ver todos los recursos editados localmente, por ejemplo, para la carga masiva de ediciones")

### Carga masiva de recursos {#bulk-upload-assets}

Los usuarios o la organización, como fotógrafos o agencias creativas, pueden crear numerosos recursos locales en escenarios como, por ejemplo, fotografías, retoques o la selección de un conjunto mayor realizado fuera de AEM. Pueden cargar estas carpetas locales de gran tamaño a Recursos AEM directamente desde la aplicación de escritorio. Las jerarquías de carpetas se conservan y se cargan todas las subcarpetas anidadas y los recursos incluidos. Los recursos cargados también están disponibles de inmediato para otros usuarios del mismo servidor para su consumo. Los recursos se cargan en segundo plano, por lo que la operación no está vinculada a una sesión del explorador web.

![Carga masiva de varias carpetas locales desde el escritorio en](assets/upload_local_folders_da2.png "AEMBulk carga varias carpetas locales desde el escritorio en AEM")

Después de cargar, si los cambios esperados no se reflejan en la aplicación, haga clic en el icono ![](assets/do-not-localize/refresh.png)Actualizar.

>[!NOTE]
>
>No utilice la función de carga para migrar recursos en dos implementaciones de AEM. En su lugar, consulte la guía [de](https://docs.adobe.com/content/help/en/experience-manager-65/assets/administer/assets-migration-guide.html)migración.

### Lista de los activos transferidos {#list-of-transferred-assets}

Para vista de la lista de recursos transferidos en una sesión determinada, consulte [Carga de recursos en AEM](#upload-and-add-new-assets-to-aem).

## Flujo de trabajo avanzado: inicio de la interfaz web de AEM Assets {#adv-workflow-start-from-aem-ui}

Si es necesario, inicie el flujo de trabajo desde la interfaz web de Recursos AEM. La aplicación de escritorio se integra con AEM para hacerse cargo cuando se solicita mediante las acciones de escritorio.

Un caso especial de inicio del flujo de trabajo desde la interfaz web es la detección de recursos. La interfaz de usuario de la barra de Omniture en Recursos oferta una experiencia de búsqueda avanzada y enriquecida. Es posible que primero desee ubicar un recurso deseado en la web y, a continuación, iniciar el flujo de trabajo en la aplicación mediante [!UICONTROL Desktop Actions]. Algunos ejemplos de casos incluyen el filtrado de resultados de búsqueda mediante facetas, la localización de un recurso específico con licencia de Adobe Stock o una personalización implementada por su organización que le permita realizar un mejor descubrimiento desde la interfaz web.

La funcionalidad de la aplicación de escritorio se utiliza cuando se intentan realizar las siguientes acciones en la interfaz web de Recursos:

* El [!UICONTROL Desktop Actions] que permite [!UICONTROL Open], [!UICONTROL Edit]y [!UICONTROL Reveal]
* [!UICONTROL Upload folder]
* [!UICONTROL Check-out] o [!UICONTROL check-in]

Por ejemplo, las acciones de la interfaz web disponibles para un recurso extraído en la aplicación son [!UICONTROL Open], [!UICONTROL Reveal]y [!UICONTROL Check-in].

![Acciones de escritorio en la](assets/assets_web_actions_da2.png "interfaz web de AEM Acciones de escritorio en la interfaz web de AEM")

>[!NOTE]
>
>Es posible que el explorador le solicite que permita el inicio de Adobe Experience Manager Desktop. Para disfrutar de una transferencia ininterrumpida del navegador a la aplicación, active la casilla de verificación correspondiente para permitir siempre que la aplicación se haga cargo.

No se puede encontrar la siguiente información o flujo de trabajo mediante la interfaz web. Utilice la aplicación de escritorio, ya que la interfaz web no realiza el seguimiento de los cambios locales y no tiene en cuenta lo siguiente:

* Archivos editados localmente.
* Archivos que tienen un conflicto de edición y la forma de resolverlo.
* Cargue los cambios locales en AEM.
* Varios estados de los archivos disponibles localmente.

Por el contrario, puede abrir el recurso en la interfaz web a partir de la aplicación de escritorio mediante la **[!UICONTROL Open In Web]** acción.

## Flujo de trabajo avanzado: colaborar en los mismos archivos y evitar conflictos de edición {#adv-workflow-collaborate-avoid-conflicts}

En los entornos de colaboración, varios usuarios pueden trabajar en el mismo conjunto de recursos que pueden provocar conflictos de versiones. Para evitar conflictos, siga estas optimizaciones:

* No edite ningún recurso haciendo clic en [!UICONTROL Open]. No edite los recursos descargados localmente abriéndolos desde la carpeta del sistema de archivos. Otros usuarios no saben que se está editando el recurso.
* Para editar un recurso, haga clic siempre en [!UICONTROL Edit]. Abre el recurso en la aplicación nativa y agrega un icono de candado al recurso para que los demás usuarios sepan que el recurso se está editando.
* Haga clic [!UICONTROL Toggle Check-in] si accidentalmente inicio la edición sin hacer clic en [!UICONTROL Edit]. Esto agrega un icono de candado al recurso. Incluso si planea editar un recurso más adelante pero desea evitar que otros lo editen, haga clic en [!UICONTROL Toggle Check-in] para bloquearlo.
* Antes de editar un recurso, asegúrese de que otros usuarios no lo están editando. Busque el icono de candado en el recurso.
* Después de completar las ediciones, cargue todos los cambios y, a continuación, registre el recurso.

![Estados de](assets/edits_conflicts_status_da2.png "conflictos de ediciónEstados de conflictos de edición")

Si un recurso descargado localmente se actualiza en el servidor de AEM, la aplicación muestra un **[!UICONTROL Modified remotely]** estado. Puede quitar la copia local o actualizar la copia local haciendo clic en [!UICONTROL Remove] o [!UICONTROL Update] respectivamente. Los vínculos del cuadro de diálogo permiten la vista de ambas versiones del recurso.

![Opciones para resolver el conflicto cuando se](assets/modified_remotely_dialog_da2.png "modifica el recurso de forma remotaOpciones para resolver el conflicto cuando se modifica el recurso de forma remota")

Si un recurso que está editando localmente también se actualiza en el servidor sin su conocimiento, la aplicación muestra un **[!UICONTROL Editing Conflict]** estado. Puede conservar un conjunto de cambios, ya sea conservando las actualizaciones (haga clic en **[!UICONTROL Keep Mine]**) y eliminando la edición del otro usuario o respetando las actualizaciones del otro usuario y eliminando las suyas (**[!UICONTROL Overwrite Mine]**).

![Opciones para resolver un](assets/editing_conflict_dialog_da2.png "conflicto de ediciónOpciones para resolver un conflicto de edición")

## Flujo de trabajo avanzado: colocar y vincular recursos en un archivo de InDesign {#adv-workflow-place-assets-indesign}

Al utilizar la aplicación de escritorio de AEM para abrir archivos con recursos vinculados, los recursos se descargan previamente y aparecen colocados en las aplicaciones nativas. Para que este flujo de trabajo funcione, la aplicación nativa debe admitir la colocación de vínculos a recursos locales y AEM debe admitir la resolución de estos vínculos en los archivos binarios a referencias del lado del servidor.

La aplicación de escritorio AEM admite este flujo de trabajo con algunas aplicaciones de escritorio y formatos de archivo de Adobe Creative Cloud seleccionados: Adobe InDesign, Adobe Illustrator y Adobe Photoshop. El flujo de trabajo le permite trabajar de forma eficaz con los archivos de Creative Cloud admitidos. Por lo tanto, si el usuario A coloca algunos recursos en un archivo de InDesign y lo comprueba en AEM, el usuario B ve los recursos en el archivo de InDesign aunque los recursos no formen parte del archivo. Los recursos se descargan localmente en el equipo del usuario B.

>[!NOTE]
>
>La aplicación de escritorio puede asignarse a cualquier unidad de Windows. Sin embargo, para operaciones suaves, no cambie la letra de unidad predeterminada. Si los usuarios de la misma organización utilizan distintas letras de unidad, no pueden ver los recursos colocados por otros usuarios. Los recursos colocados no se recuperan a medida que cambia la ruta. Los recursos colocados siguen colocados en el archivo binario (digamos INDD) y no se eliminan.

Para conocer las limitaciones de este flujo de trabajo, consulte los requisitos [del sistema y las versiones](release-notes.md#system-requirements-and-prerequisites-v2)compatibles.

Para probar este flujo de trabajo con un recurso de imagen e InDesign, siga estos pasos:

1. Tenga a mano un archivo INDD con los recursos colocados en AEM. Para saber cómo crear un archivo INDD de este tipo, consulte [Colocación de gráficos](https://helpx.adobe.com/indesign/using/placing-graphics.html).
1. Desde la aplicación de escritorio, **[!UICONTROL Edit]** el archivo INDD con los recursos colocados en AEM.
1. La aplicación descarga tanto el archivo de InDesign como los recursos vinculados. Cuando InDesign abre el documento, los vínculos se resuelven, los recursos se descargan y los recursos se muestran en el documento de InDesign.
1. Para colocar un nuevo gráfico en el archivo de InDesign, utilice **[!UICONTROL Reveal File]** la acción en el recurso. La acción descarga el recurso localmente y abre la ubicación del recurso compartido de red local en el Explorador de Windows o en el Buscador de Mac.
1. Coloque el recurso revelado en InDesign documento. Esto crea un vínculo en el documento.
1. Una vez finalizadas las ediciones en InDesign documento, guárdelas y cárguelas en AEM mediante la aplicación de escritorio.

## Flujo de trabajo avanzado: descargar los recursos localmente {#adv-workflow-download-assets-locally}

La aplicación descarga los recursos del servidor AEM localmente en el sistema de archivos en muchos casos. Las descargas consumen ancho de banda y espacio en disco. Conocer los escenarios le ayuda a optimizar el tiempo de espera para que se completen las descargas.

Puede descargar los recursos desde la aplicación a petición. Consulte [Descargar recursos](#download-assets).

Cuando se utiliza la [!UICONTROL Open] acción para abrir un recurso en una aplicación de escritorio nativa, el recurso se descarga localmente si no se encuentra disponible localmente. Consulte [Abrir recursos](#openondesktop-v2).

Cuando se muestra la ubicación de un recurso o una carpeta desde la aplicación, el recurso o la carpeta se descarga primero localmente y, a continuación, se abre en el equipo en el recurso compartido de red local. Consulte [Abrir recursos](#openondesktop-v2).

Cuando se utiliza la [!UICONTROL Edit] acción para editar un recurso en una aplicación de escritorio nativa, el recurso se descarga localmente si no se encuentra disponible localmente. Consulte [Edición de recursos y carga de recursos actualizados en AEM](#edit-assets-upload-updated-assets).

Si la aplicación está instalada y tiene permiso para hacerlo, se completan las acciones cuando se utiliza [!UICONTROL Desktop Actions] desde la interfaz web de AEM. La aplicación descarga el recurso primero y, a continuación, completa la acción.
