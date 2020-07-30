---
title: Prácticas recomendadas de AEM versión 1.x de la aplicación de escritorio
description: Funciones clave y uso recomendado de la versión 1.x de la aplicación de escritorio de Adobe Experience Manager.
uuid: ba8fbc74-e1ad-4085-a031-ffd317628ba6
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: 57d5cd78-abce-4ede-a50e-7c161ddb43ae
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3eb9ab89ff6338fb29cfad1a031944119908d0a2
workflow-type: tm+mt
source-wordcount: '1707'
ht-degree: 0%

---


# Prácticas recomendadas de AEM aplicación de escritorio v1.x {#aem-desktop-app-best-practices}

## Información general {#overview}

La aplicación de escritorio de Adobe Experience Manager (AEM) vincula la solución de administración de recursos digitales (DAM) con el escritorio para que pueda abrir los archivos disponibles en la interfaz de usuario web de AEM directamente en el escritorio. Si guarda un recurso desde el escritorio, se carga en AEM en la ubicación adecuada.

AEM aplicación de escritorio elimina las posibilidades de actualizar copias locales incorrectas o actualizar un recurso incorrecto en AEM. el flujo de trabajo fácil de usar de la aplicación de escritorio se habilita mediante la tecnología de uso compartido de red que proporcionan los sistemas operativos de escritorio.

La aplicación de escritorio monta el repositorio de AEM Assets como recurso compartido de red en el escritorio. Por lo tanto, las carpetas y los archivos aparecen como si fueran locales. Sin embargo, no se recomienda realizar operaciones de administración de recursos digitales directamente desde el escritorio en el recurso compartido de red montado en Finder o Explorer. En su lugar, Adobe recomienda utilizar la interfaz de usuario web de AEM Assets para realizar operaciones, como copiar o mover un gran número de recursos.

>[!NOTE]
>
>Antes de leer este documento, puede revisar las optimizaciones [generales de integración de](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-integration-best-practices.html) AEM y Creative Cloud para obtener una descripción general de nivel superior del tema.

## AEM desktop app architecture {#aem-desktop-app-architecture}

AEM aplicación de escritorio utiliza recursos compartidos de red WebDAV (Windows) o SMB (Mac) para montar recursos compartidos de red. El recurso compartido de red montado solo es local. AEM aplicación de escritorio intercepta las llamadas (abrir, leer, escribir) y proporciona almacenamiento en caché local adicional. Traduce las llamadas remotas al servidor de AEM Assets para optimizar AEM solicitudes HTTP. En el diagrama siguiente se muestra la arquitectura de la aplicación de escritorio AEM.

![Arquitectura de aplicaciones de escritorio AEM](assets/chlimage_1.png)

*Figura: arquitectura de aplicaciones de escritorio*

El almacenamiento en caché adicional al guardar un archivo hace que se guarde primero el archivo localmente (para que el usuario no espere a la transferencia de red). A continuación, tras un retraso predefinido (30 segundos), el archivo se carga en AEM en segundo plano y, a continuación, el recurso se carga en AEM. AEM aplicación de escritorio proporciona una interfaz de usuario para supervisar el estado de las cargas de archivos en segundo plano.

## Uso recomendado de AEM aplicación de escritorio {#recommended-use-of-aem-desktop-app}

Las funciones clave de AEM aplicación de escritorio incluyen:

* **Apertura de archivos desde la interfaz de usuario web de AEM Assets en el escritorio**. Desde la interfaz de usuario web, puede mostrar recursos en el escritorio (en Finder, Explorer) o abrir un recurso mediante una aplicación de escritorio.

* **Check-out y check-in**. Los recursos se pueden desproteger para editarlos y se marcan como bloqueados para el usuario en AEM Assets. Después de editar, el recurso se puede desbloquear para desbloquearlo.

* **Guarde los cambios en los archivos**. Cualquier cambio que guarde en el archivo del recurso compartido de red se carga en AEM automáticamente y se crea una nueva versión.

* **Coloque los recursos vinculados en otros documentos**. En las aplicaciones, como Creative Cloud ([!DNL Adobe Photoshop], [!DNL Adobe InDesign], y [!DNL Adobe Illustrator]), puede colocar un archivo externo como vínculo. Por ejemplo, puede colocar una imagen en un documento de InDesign. En este caso, el montaje del recurso compartido de red permite examinar y seleccionar recursos de AEM para colocarlos. La colocación de archivos vinculados también funciona en algunas aplicaciones que no son de Adobe, como MS Office.

* **Resolución de referencia en AEM**. Si ambos archivos, los archivos colocados y los archivos principales con vínculo, se almacenan en AEM puede proporcionar automáticamente información del lado del servidor sobre las referencias de recursos.

* **Acceda al recurso desde el escritorio**. En el recurso compartido de red montado, un menú contextual proporciona un [!UICONTROL More Info] cuadro de diálogo (previsualización más grande, metadatos clave) y la capacidad de abrir un recurso en la interfaz de usuario de AEM.

* **Carga masiva de carpetas jerárquicas de gran tamaño**. Si utiliza la opción Crear > Cargar carpeta en AEM interfaz de usuario para cargar recursos, AEM aplicación de escritorio carga la jerarquía de carpetas seleccionada para AEM en segundo plano. El progreso de la carga se puede supervisar con una interfaz de usuario dedicada en la aplicación de escritorio.

## Uso inapropiado de AEM aplicación de escritorio {#inappropriate-use-of-aem-desktop-app}

* No utilice AEM aplicación de escritorio para administrar recursos desde el escritorio. AEM aplicación de escritorio no se ha creado como un reemplazo de las unidades de red. En su lugar, utilice las siguientes capacidades:

   * Interfaz de usuario web de AEM Assets para la administración de recursos digitales (búsqueda o uso compartido de recursos, metadatos y copiar o mover).

   * AEM aplicación de escritorio [!UICONTROL Folder Upload] para cargar carpetas grandes y jerárquicas.

* No trate AEM aplicación de escritorio como un cliente de &quot;sincronización de escritorio&quot; para AEM Assets. La ventaja clave de AEM aplicación de escritorio es que proporciona acceso &quot;virtual&quot; a todo el repositorio, y las aplicaciones de sincronización de escritorio generalmente sincronizan solo los recursos que pertenecen a un usuario. AEM aplicación de escritorio proporciona cierto nivel de almacenamiento en caché y carga en segundo plano; sin embargo, funciona de forma muy distinta a las aplicaciones de &quot;sincronización&quot; típicas, como la aplicación de escritorio de Adobe Creative Cloud o Microsoft OneDrive.

* No utilice AEM unidades de red de aplicaciones de escritorio para guardar los recursos con frecuencia. Todas las operaciones de guardado se transmiten a los AEM Assets. Por lo tanto, no es práctico realizar operaciones intensivas de edición directamente en el repositorio de AEM Assets montados. La edición de un recurso directamente en el repositorio montado bloquea la línea de tiempo del recurso con versiones irrelevantes e impone cargas adicionales en el servidor.

* No utilice AEM aplicación de escritorio para migrar grandes cantidades de datos de una instancia de AEM a otra. Consulte la Guía [de](https://docs.adobe.com/content/help/en/experience-manager-65/assets/administer/assets-migration-guide.html) migración para planificar y ejecutar migraciones de recursos. Por el contrario, la aplicación de escritorio [admite la carga](use-app-v1.md#bulkupload) masiva de un gran número de recursos por primera vez en [!DNL Adobe Experience Manager].

## Recommendations para casos de uso seleccionados {#recommendations-for-selected-use-cases}

### Acceso a recursos para usuarios creativos {#access-to-assets-for-creative-users}

AEM aplicación de escritorio proporciona acceso virtual a todo el repositorio de DAM, y puede resultar complicado para los usuarios creativos en el escritorio encontrar y acceder a los recursos adecuados en su escritorio. Utilice estas prácticas recomendadas para simplificarlo.

* Utilice las funciones de colaboración de la interfaz de usuario web de AEM Assets para proporcionar un acceso más directo a los recursos adecuados para el usuario creativo. Compartir carpetas o colecciones, proporcionar colecciones inteligentes (búsquedas guardadas) o enviar notificaciones con punteros a los recursos adecuados son algunos de ellos. Los usuarios creativos pueden utilizar las acciones de escritorio en la interfaz de usuario web para acceder rápidamente a estos recursos en su escritorio.

* Considere los permisos adecuados para los recursos (control de acceso) para simplificar la vista en el repositorio DAM para los usuarios creativos, limitando básicamente su acceso a los recursos que necesitan o que están interesados en:

   * Es posible que se denieguen ciertas áreas que no son relevantes para los usuarios creativos para sus grupos de usuarios, para eliminarlas de su vista, también en el escritorio.

   * La mayoría de los recursos de DAM son definitivos y no están destinados a cambiarse; estos recursos deben ser de solo lectura para los usuarios creativos.

   * Solo los recursos que requieren cambios o retoques deben estar habilitados para escritura para los usuarios creativos. Algunas organizaciones utilizan AEM proyectos y las carpetas que crean para alojar recursos que siguen sujetos a cambios.

### Búsqueda de recursos {#searching-assets}

Para buscar un archivo que desea abrir en el escritorio:

* Utilice la interfaz de usuario web de AEM Assets para localizar el recurso. La búsqueda no sólo es potente en AEM Assets (facetas de búsqueda, búsquedas guardadas), sino que también proporciona funciones adicionales para encontrar el recurso correcto. Estos incluyen filtros adicionales, como la capacidad de buscar recursos en función del estado (aprobación, caducidad), colecciones, tareas, notificaciones y compartir carpetas/colecciones con otros usuarios/grupos.

* Después de localizar el recurso, utilice Acciones de escritorio en AEM interfaz de usuario para acceder al recurso en el escritorio.

### Actualización de recursos abiertos con AEM aplicación de escritorio {#updating-assets-opened-using-aem-desktop-app}

Si edita un recurso directamente en la ubicación asignada de AEM Assets a un recurso compartido de red local, el recurso se carga en AEM cada vez que lo guarda en el escritorio. Además, AEM crea una versión y genera representaciones.

Si un recurso almacenado en AEM necesita una actualización:

* Para actualizaciones **** menores, como solicitudes de retoque menores en el proceso de aprobación:

   * Extraiga el archivo y ábralo en el escritorio.

   * Actualice el archivo.

   * Guarde la versión actualizada. El recurso se actualiza y la línea de tiempo muestra la versión original para la comparación.

* Para actualizaciones **** importantes, como una solicitud de cambio que requiere un ciclo de trabajo en curso creativo pequeño:

   * Utilice la opción Mostrar para abrir la carpeta adecuada en el escritorio.

   * Copie el archivo en una carpeta WIP fuera del recurso compartido de AEM Assets asignado (por ejemplo, copie el archivo en una carpeta sincronizada con la aplicación de escritorio de Adobe Creative Cloud).

   * Trabaje en el archivo y guárdelo de forma intermitente. Los cambios no se guardan en AEM Assets.

   * Una vez finalizadas las ediciones, mueva, copie o guarde el archivo asignado desde AEM para cargarlo como una nueva versión.

## Rendimiento de red {#network-performance}

La buena experiencia de los usuarios que utilizan la aplicación de escritorio AEM depende en gran medida de la buena y estable conectividad de red entre sus escritorios y el servidor AEM, así como del servidor adaptado para un buen rendimiento, especialmente en lo que respecta a la carga y actualización de recursos. Estas recomendaciones están destinadas a los equipos de red/TI de las organizaciones.

### Consideraciones de red {#network-considerations}

Para conocer las prácticas recomendadas en cuanto a la configuración de red de AEM Assets, consulte el documento de consideraciones [de red de](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/assets-migration-guide.html) AEM Assets. Algunos de los aspectos importantes que ayudan a optimizar AEM experiencia de la aplicación de escritorio para los usuarios son:

* **Utilice Dispatcher** configurado correctamente. Use AEM Dispatcher para obtener seguridad adicional y asegúrese de que está configurado para que [AEM conexión de la aplicación de escritorio AEM detrás de un despachante](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher)

* **Ahorre ancho de banda**. Considere desactivar la previsualización de iconos en Finder en Mac al explorar el repositorio montado con Finder. Finder solicita a cada archivo que genere una previsualización y hace que la aplicación de escritorio descargue y almacene en caché el recurso localmente. Tenga en cuenta que, al ahorrar ancho de banda, también disminuiría la experiencia del usuario en el escritorio, por lo que debería hacerse al trabajar con repositorios con recursos grandes y/o ancho de banda limitado.

>[!NOTE]
>
>Para desactivar las previsualizaciones de iconos, en Finder vaya a Vista, seleccione Opciones de Vista y, a continuación, desmarque la opción &quot;Mostrar previsualización de iconos&quot;. Esto solo funciona para la carpeta actual; para que sea predeterminada, haga clic en el botón &quot;Usar como predeterminado&quot; en la misma ventana.

### Optimización del rendimiento del servidor {#optimizing-server-performance}

Para comprender cómo se debe optimizar el rendimiento del servidor de AEM Assets, consulte la Guía [de ajuste de rendimiento de](https://docs.adobe.com/content/help/en/experience-manager-65/assets/administer/performance-tuning-guidelines.html)AEM Assets. Algunos de los aspectos importantes del rendimiento del servidor para AEM aplicación de escritorio son la optimización de la configuración del flujo de trabajo para que funcione correctamente en las cargas de recursos:

* **Carga** de recursos de mayor rendimiento. Configure el modelo de flujo de trabajo de actualización de recursos [AEM para que sea transitorio](https://docs.adobe.com/content/help/en/experience-manager-65/assets/administer/performance-tuning-guidelines.html#Workflows).

* **Limitar la CPU del servidor para cargas**. Asegúrese de que el parámetro de trabajo de flujo de trabajo paralelo máximo esté configurado correctamente, de modo que las cargas no agoten toda la CPU.
