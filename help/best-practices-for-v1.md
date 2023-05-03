---
title: Prácticas recomendadas de la aplicación de escritorio v1.10
description: Funciones clave y uso recomendado [!DNL Adobe Experience Manager] versión 1.10 de la aplicación de escritorio.
exl-id: 5de06b33-c05c-47eb-b884-408b6f9afc94
source-git-commit: 7a7236c36f615e97e9d040e6139368a931eb579e
workflow-type: tm+mt
source-wordcount: '1676'
ht-degree: 0%

---

# Prácticas recomendadas de AEM aplicación de escritorio v1.10 {#aem-desktop-app-best-practices}

## Información general {#overview}

[!DNL Adobe Experience Manager] la aplicación de escritorio vincula la solución de administración de recursos digitales (DAM) con el escritorio para que pueda abrir los archivos disponibles en la interfaz de usuario web de AEM directamente en el escritorio. Si guarda un recurso desde el escritorio, se carga en AEM en la ubicación adecuada.

AEM aplicación de escritorio elimina las probabilidades de que actualice copias locales incorrectas o de que actualice un recurso incorrecto en AEM. el flujo de trabajo fácil de usar de la aplicación de escritorio está habilitado mediante la tecnología de uso compartido de red que ofrecen los sistemas operativos de escritorio.

La aplicación de escritorio monta el repositorio de AEM Assets como recurso compartido de red en el escritorio. Por lo tanto, las carpetas y los archivos aparecen como si fueran locales. Sin embargo, no se recomienda realizar operaciones de administración de recursos digitales directamente desde el escritorio en el recurso compartido de red montado en Finder o Explorer. En su lugar, Adobe recomienda utilizar la interfaz de usuario web de AEM Assets para llevar a cabo operaciones como copiar o mover un gran número de recursos.

>[!NOTE]
>
>Antes de leer este documento, puede revisar el [Prácticas recomendadas para la integración de AEM y Creative Cloud](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/aem-cc-integration-best-practices.html) para obtener una descripción general de nivel superior del tema.

## arquitectura de la aplicación de escritorio AEM {#aem-desktop-app-architecture}

AEM aplicación de escritorio utiliza redes compartidas WebDAV (Windows) o SMB (Mac) para montar redes compartidas. El recurso compartido de red montado solo es local. AEM aplicación de escritorio intercepta las llamadas (abrir, leer, escribir) y proporciona almacenamiento en caché local adicional. Traduce las llamadas remotas al servidor de AEM Assets a solicitudes HTTP AEM optimizadas. El diagrama siguiente muestra la arquitectura de la aplicación de escritorio de AEM.

![arquitectura de la aplicación de escritorio AEM](assets/arch_v1.png)

*Figura: arquitectura de aplicaciones de escritorio*

El almacenamiento en caché adicional al escribir cuando se guarda un archivo hace que el archivo se guarde primero localmente (de modo que el usuario no espere a la transferencia de red). A continuación, tras un retraso predefinido (30 segundos), el archivo se carga en AEM en segundo plano y, a continuación, el recurso se carga en AEM. AEM aplicación de escritorio proporciona una interfaz de usuario para supervisar el estado de las cargas de archivos en segundo plano.

## Uso recomendado de AEM aplicación de escritorio {#recommended-use-of-aem-desktop-app}

Entre las funcionalidades clave de AEM aplicación de escritorio se incluyen:

* **Apertura de archivos desde la interfaz de usuario web de AEM Assets en el escritorio**. Desde la interfaz de usuario web, puede mostrar los recursos en el escritorio (en Finder, Explorer) o abrir un recurso mediante una aplicación de escritorio.

* **Extracción y registro**. Los recursos se pueden desproteger para editarlos y se marcan como bloqueados para el usuario en AEM Assets. Tras la edición, se puede proteger el recurso para desbloquearlo.

* **Guardar cambios en archivos**. Cualquier cambio que guarde en el archivo del recurso compartido de red se carga en AEM automáticamente y se crea una nueva versión.

* **Colocación de recursos vinculados en otros documentos**. En las aplicaciones, como Creative Cloud ([!DNL Adobe Photoshop], [!DNL Adobe InDesign]y [!DNL Adobe Illustrator]), puede colocar un archivo externo como vínculo. Por ejemplo, puede colocar una imagen en un documento de InDesign. En este caso, el montaje del recurso compartido de red le permite examinar y seleccionar los recursos de AEM para su ubicación. La colocación de archivos vinculados también funciona en algunas aplicaciones que no son de Adobe, como MS Office.

* **Resolución de referencia en AEM**. Si ambos, los archivos colocados y los archivos principales con vínculo, se almacenan en AEM puede proporcionar automáticamente información del lado del servidor sobre las referencias de recursos.

* **Acceso al recurso desde el escritorio**. En el recurso compartido de red montado, un menú contextual proporciona un [!UICONTROL More Info] (vista previa más grande, metadatos clave) y la capacidad de abrir un recurso en la interfaz de usuario de AEM.

* **Carga masiva de carpetas jerárquicas**. Si utiliza la opción Crear > Carga de carpeta en AEM interfaz de usuario para cargar recursos, AEM aplicación de escritorio carga la jerarquía de carpetas seleccionada para AEM en segundo plano. El progreso de la carga se puede supervisar con una interfaz de usuario dedicada en la aplicación de escritorio.

## Uso inapropiado de AEM aplicación de escritorio {#inappropriate-use-of-aem-desktop-app}

* No utilice AEM aplicación de escritorio para administrar recursos desde el escritorio. AEM aplicación de escritorio no se creó como reemplazo de las unidades de red. En su lugar, utilice las siguientes capacidades:

   * Interfaz de usuario web de AEM Assets para la administración de recursos digitales (buscar o compartir recursos, metadatos y copiar o mover).

   * aplicación de escritorio AEM [!UICONTROL Folder Upload] para cargar carpetas grandes y jerárquicas.

* No trate AEM aplicación de escritorio como un cliente de &quot;sincronización de escritorio&quot; para AEM Assets. La ventaja clave de AEM aplicación de escritorio es que proporciona acceso &quot;virtual&quot; a todo el repositorio, y las aplicaciones de sincronización de escritorio generalmente sincronizan solo los activos que pertenecen a un usuario. AEM aplicación de escritorio proporciona un cierto nivel de almacenamiento en caché y carga en segundo plano; sin embargo, funciona de forma muy diferente a las aplicaciones de &quot;sincronización&quot; típicas, como la aplicación de escritorio de Adobe Creative Cloud o Microsoft OneDrive.

* No utilice AEM unidades de red de aplicaciones de escritorio para guardar recursos con frecuencia. Todas las operaciones de guardado se transmiten a AEM Assets. Por lo tanto, no es práctico realizar operaciones de edición intensivas directamente en el repositorio de AEM Assets montado. La edición de un recurso directamente en el repositorio montado bloquea la línea de tiempo del recurso con versiones irrelevantes e impone sobrecargas adicionales en el servidor.

* No utilice AEM aplicación de escritorio para migrar grandes cantidades de datos de una instancia de AEM a otra. Consulte la [Guía de migración](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/assets-migration-guide.html) para planificar y ejecutar migraciones de recursos. Por el contrario, la aplicación de escritorio [admite la carga masiva](use-app-v1.md#bulkupload) gran número de activos por primera vez en [!DNL Adobe Experience Manager].

## Recommendations para casos de uso seleccionados {#recommendations-for-selected-use-cases}

### Acceso a recursos para usuarios creativos {#access-to-assets-for-creative-users}

AEM aplicación de escritorio proporciona acceso virtual a todo el repositorio de DAM, y puede ser complicado para los usuarios creativos de escritorio encontrar y acceder a los recursos adecuados en su escritorio. Utilice estas prácticas recomendadas para simplificarlas.

* Utilice las funciones de colaboración de la interfaz de usuario web de AEM Assets para proporcionar un acceso más directo a los recursos adecuados para el usuario creativo. Compartir carpetas o colecciones, proporcionar colecciones inteligentes (búsquedas guardadas) o enviar notificaciones con punteros a los recursos adecuados son algunas de ellas. Los usuarios creativos pueden utilizar acciones de escritorio en la interfaz de usuario web para obtener acceso rápidamente a estos recursos en su escritorio.

* Considere los permisos adecuados para los recursos (control de acceso) para simplificar la vista en el repositorio DAM para los usuarios creativos, limitando básicamente su acceso solo a los recursos que necesitan o que están interesados en:

   * Es posible que se denieguen ciertas áreas no relevantes para los usuarios creativos a sus grupos de usuarios, para eliminarlos de su vista, también en el escritorio.

   * La mayoría de los recursos de DAM son finales y no están pensados para cambiarlos; estos recursos deben ser de solo lectura para los usuarios creativos.

   * Solo los recursos que requieran cambios o retoque deben estar habilitados para escritura para los usuarios creativos. Algunas organizaciones utilizan AEM Proyectos y las carpetas que crean para alojar recursos que aún están sujetos a cambios.

### Búsqueda de recursos {#searching-assets}

Para buscar un archivo que desea abrir en el escritorio :

* Utilice la interfaz de usuario web de AEM Assets para localizar el recurso. No solo es potente la búsqueda en AEM Assets (facetas de búsqueda, búsquedas guardadas), sino que también proporciona funciones adicionales para encontrar el recurso correcto. Entre ellos se incluyen filtros adicionales, como la capacidad de buscar recursos en función del estado (aprobación, caducidad), colecciones, tareas, notificaciones y compartir carpetas/colecciones con otros usuarios/grupos.

* Después de localizar el recurso, utilice Acciones de escritorio en AEM interfaz de usuario para acceder al recurso en el escritorio .

### Actualización de recursos abiertos con AEM aplicación de escritorio {#updating-assets-opened-using-aem-desktop-app}

Si edita un recurso directamente en la ubicación asignada de AEM Assets a un recurso compartido de red local, el recurso se carga en AEM cada vez que lo guarda en el escritorio. Además, AEM crea una versión y genera representaciones.

Si un recurso almacenado en AEM necesita una actualización:

* Para **actualizaciones menores**, como solicitudes de retoque menores en el proceso de aprobación:

   * Extraiga el archivo y ábralo en el escritorio.

   * Actualice el archivo .

   * Guarde la versión actualizada. El recurso se actualiza y la cronología muestra la versión original para la comparación.

* Para **principales actualizaciones**, como una solicitud de cambio que requiere un ciclo de trabajo en curso creativo pequeño:

   * Utilice la opción Mostrar para abrir la carpeta adecuada en el escritorio.

   * Copie el archivo en una carpeta WIP fuera del recurso compartido de AEM Assets asignado (por ejemplo, copie el archivo en una carpeta sincronizada con la aplicación de escritorio de Adobe Creative Cloud).

   * Trabaje en el archivo y guárdelo de forma intermitente. Los cambios no se guardan en AEM Assets.

   * Una vez completadas las ediciones, mueva, copie o guarde el archivo asignado desde AEM para cargarlo como una nueva versión.

## Rendimiento de red {#network-performance}

La buena experiencia para los usuarios que utilizan la aplicación de escritorio de AEM depende en gran medida de la buena y estable conectividad de red entre sus escritorios y el servidor de AEM, así como del servidor adaptado para un buen rendimiento, especialmente en lo que respecta a la carga y actualización de recursos. Estas recomendaciones están destinadas a los equipos de red/TI de las organizaciones.

### Consideraciones de red {#network-considerations}

Para conocer las prácticas recomendadas sobre la configuración de red de AEM Assets, consulte [Cómo migrar recursos de forma masiva](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/assets-migration-guide.html) documento. Algunos de los aspectos importantes que ayudan a optimizar AEM experiencia de la aplicación de escritorio para los usuarios son:

* **Usar Dispatcher configurado correctamente**. Utilice AEM Dispatcher para obtener una seguridad adicional y asegúrese de que está configurado para [AEM conexión de aplicación de escritorio para AEM detrás de un dispatcher](install-configure-app-v1.md#connect-to-an-aem-instance-behind-a-dispatcher)

* **Ahorre ancho de banda**. Considere desactivar la previsualización de iconos en Finder en Mac al examinar el repositorio montado con Finder. El Buscador solicita a cada archivo que genere una vista previa y hace que la aplicación de escritorio descargue y almacene en caché el recurso localmente. Tenga en cuenta que, al ahorrar ancho de banda, también disminuiría la experiencia del usuario para los usuarios de escritorio, por lo que debería hacerse cuando trabajen con repositorios con grandes activos y/o ancho de banda limitado.

>[!NOTE]
>
>Para desactivar las vistas previas de los iconos, en Finder vaya a [!UICONTROL View], seleccione [!UICONTROL View Options]y, a continuación, desmarque la [!UICONTROL Show icon preview] . Esto solo funciona para la carpeta actual; para convertirla en predeterminada, haga clic en el botón [!UICONTROL Use as default] en el mismo cuadro de diálogo.

### Optimización del rendimiento del servidor {#optimizing-server-performance}

Para comprender cómo se debe optimizar el rendimiento del servidor de AEM Assets, consulte [Guía de ajuste del rendimiento de AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/performance-tuning-guidelines.html). Algunos aspectos importantes del rendimiento del servidor para AEM aplicación de escritorio se refieren a la optimización de la configuración del flujo de trabajo para que funcione correctamente en las cargas de recursos:

* **Carga de recursos de más rendimiento**. Configure las variables [AEM modelo de flujo de trabajo de Asset Update para que sea transitorio](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/performance-tuning-guidelines.html).

* **Limitar la CPU del servidor para cargas**. Asegúrese de que el parámetro de trabajos de flujo de trabajo paralelo máximo esté configurado correctamente, de modo que las cargas no agoten toda la CPU.
