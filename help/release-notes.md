---
title: Notas de la versión de la aplicación de escritorio de Adobe Experience Manager
description: Detalles de la versión, mejoras, nuevas funciones, compatibilidad y vínculos de descarga para la aplicación de escritorio de Adobe Experience Manager.
uuid: b783c3f8-aa1e-4c05-b687-5894909769f5
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: 3052549b-fe75-44fb-a55e-5cc612868f54
index: y
internal: n
snippet: y
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 63cb82b6bdafeb87d296a895d68cb3912045839a

---


# Notas de la versión de la aplicación de escritorio de Adobe Experience Manager {#release-notes-v2}

| Productos | Aplicación de escritorio de Adobe Experience Manager |
|----|----|
| Versión de la aplicación (revisión) | 2.0 (2.0.2.0) |
| Versiones de AEM compatibles | AEM como servicio de nube; AEM 6.5; AEM 6.4; AEM 6.3 (con paquete de compatibilidad) |
| Tipo | Versión menor |
| Fecha de lanzamiento | 15 de abril de 2020 (Mac y Win) |
| Direcciones URL de descarga | [macOS de 64 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-osx-2.0.2.0.dmg); [Windows de 64 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win64-2.0.2.0.exe); [Windows de 32 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win32-2.0.2.0.exe) |

## Requisitos y requisitos previos del sistema {#system-requirements-and-prerequisites-v2}

La aplicación de escritorio Adobe Experience Manager es compatible con los siguientes sistemas operativos:

* Mac OS X 10.10 o posterior, con las últimas correcciones de errores.
* Windows 7 y Windows 10 con los paquetes de servicios y las correcciones de errores más recientes.

La aplicación funciona con las siguientes versiones de Experience Manager, tanto si se implementa como un servicio de nube, en los servicios gestionados de Adobe (AMS) como in situ:

* [Experience Manager as a Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/release-notes/home.html)
* [Experience Manager 6.5.0+](https://docs.adobe.com/content/help/en/experience-manager-65/release-notes/release-notes.html) o posterior
* [Experience Manager 6.4.4+](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/release-notes.html) o posterior
* Experience Manager 6.4.0 - 6.4.3 con paquete de [compatibilidad](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)

>[!NOTE]
>
>La compatibilidad de la aplicación de escritorio con Experience Manager 6.3 está obsoleta. Adobe recomienda actualizar a una versión más reciente y compatible de Adobe Experience Manager.
>Experience Manager 6.3.3.1 o posterior funciona con la aplicación de escritorio después de instalar el paquete [de](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)compatibilidad. Este paquete no está disponible para Experience Manager 6.3, ya que no hay paquetes [de servicios planificados](https://helpx.adobe.com/experience-manager/maintenance-releases-roadmap.html).

La versión de la aplicación que planea instalar en su equipo local requiere una versión específica del servidor de Adobe Experience Manager o componentes adicionales del servidor (paquetes de servicio, correcciones rápidas o paquetes de funciones). Póngase en contacto con el administrador de Adobe Experience Manager para obtener ayuda.

### Support for different assets and file types {#support-for-file-types}

La aplicación admite recursos almacenados en Adobe Experience Manager que representan archivos binarios para sus operaciones básicas. La apertura de archivos en la aplicación de escritorio nativa depende de la asociación de sistema operativo de los tipos de archivo específicos, como PNG o JPG, a aplicaciones específicas, como Vista previa de Mac o Adobe Photoshop.

Algunos tipos de archivo admiten la colocación de recursos vinculados en el archivo binario. La aplicación descarga previamente los recursos vinculados si el recurso está presente en el repositorio de Experience Manager cuando estos archivos binarios se abren con la aplicación de escritorio. Los tipos de archivo admitidos actualmente son:

* Archivos de Adobe InDesign (formato INDD)
* Archivos de Adobe Illustrator (formato AI)
* Archivos de Adobe Photoshop (formato PS)

La función es compatible con las versiones de Adobe Creative Cloud 2018 y Adobe Creative Cloud 2019 de la aplicación anterior. La aplicación utiliza un método heurístico y de mejor coincidencia para asignar las rutas de escritorio locales de los recursos vinculados a las direcciones URL en el servidor de Experience Manager. Se basa en algunos supuestos:

* Paths to placed files in the native application use a global desktop path (placed from the local network share shown with [!UICONTROL Reveal] option).
* La aplicación nativa almacena las rutas en el registro XMP del archivo.
* Experience Manager ha extraído el registro XMP con las rutas al registro de metadatos del recurso.
* Las rutas pueden coincidir con los recursos de Experience Manager, es decir, los archivos colocados también están en Experience Manager bajo una ruta coincidente.

## Nuevas funciones y mejoras {#whats-new-added}

To know the details, see [What&#39;s new in v2.0](introduction.md#whats-new-v2).

**Actualizaciones en la aplicación v2.0.2**

Las correcciones y actualizaciones de errores son:

* Para mejorar el rendimiento de carga, aumente la aceleración de carga en [!UICONTROL Preferences]. Cuando se activa esta opción, la aplicación utiliza más subprocesos de CPU locales y utiliza más recursos.
* Se ha corregido un problema con las cargas de recursos cuando los nombres de archivo o las rutas contienen determinados caracteres GB18030. <!-- CQ-4283494 -->
* La opción Ordenar por relevancia está disponible después de cambiar a otro tipo de ordenación en los resultados de búsqueda. <!-- CQ-4286874 -->
* La aplicación de escritorio ahora lista subcarpetas sin necesidad de actualizarlas explícitamente. <!-- CQ-4285711 -->
* (Windows) Se ha corregido un problema poco frecuente de la interfaz de la aplicación no utilizable en algunos equipos Windows. Los usuarios no pueden hacer clic en la interfaz de la aplicación, ya que parece distorsionada con el área de clic de los elementos de la interfaz &#39;cambiados&#39; en el lateral. <!-- CQ-4280785 -->

**Actualizaciones en la aplicación v2.0.1**

Las correcciones y actualizaciones de errores son:

* Permitir la opción de configurar `%Temp%` el directorio para que coincida con la `%APPDATA%` ruta. <!-- CQ-4282665 -->
* Permita que los usuarios inicien sesión en AEM Author mediante la autenticación de Okta SAML. <!-- CQ-4278134 -->

## Instrucciones de instalación {#installation-instructions-v2}

To know how to install and configure the app, see [Install Experience Manager desktop app](install-upgrade.md).

If you are upgrading from a previous Experience Manager desktop app, you must follow these best practices for transitioning that are listed at [upgrade from previous version](install-upgrade.md#upgrade-from-previous-version).

## Notas importantes sobre el funcionamiento de la aplicación {#how-app-works}

Es importante comprender lo siguiente sobre la aplicación y su funcionamiento.

* La aplicación proporciona control total sobre las operaciones que requieren la transferencia completa de archivos binarios de recursos desde y hacia AEM (abrir, editar, cargar cambios y cargar recursos).
   * Si desea trabajar con el recurso en el escritorio, debe abrir, editar o descargar contenido en el mismo escritorio, ya sea de forma individual, en una carpeta o mediante selección múltiple.
   * Si desea realizar cambios locales en los recursos cargados en AEM, debe seleccionarlos [!UICONTROL Upload Changes], ya sea de forma individual o mediante selección múltiple.
   * La aplicación no es un &quot;cliente de sincronización&quot; que sincroniza recursos en el escritorio y en AEM.
   * La aplicación no proporciona un recurso compartido de red que asigne el repositorio de AEM como una estructura de carpetas virtuales.
* La aplicación muestra una lista de recursos que se basa en el estado del repositorio de AEM Assets. La aplicación no muestra ni administra ningún archivo descargado localmente y cuyo nombre haya cambiado en los archivos locales o en la carpeta de caché.
* Si la aplicación no muestra los resultados esperados, haga clic en el icono de actualización situado en la barra superior.
* El recurso compartido de red local, que se muestra cuando se usa la acción [!UICONTROL Reveal File], solo muestra los archivos (y carpetas) disponibles a nivel local. [!UICONTROL Reveal File] y [!UICONTROL Reveal Folder] descarga previamente los recursos para que se muestren los que son correctos en el recurso compartido de red local.
* El recurso compartido de red local SMB (Mac) o WebDAV (Win) se utiliza cuando una aplicación de Adobe Creative Cloud lee los archivos de recursos vinculados o colocados en un archivo nativo de la aplicación de Creative Cloud.

En el diagrama siguiente se ilustra el flujo de recursos y archivos desde la nube al sistema de archivos local y viceversa, cuando este proceso se inicia mediante las acciones del usuario.

![Flujo de recursos desde el servidor de AEM a las aplicaciones de escritorio nativas a través de la aplicación de escritorio](assets/da20_flow_diagram.png)

## Problemas conocidos {#known-issues-v2}

**Problemas de la interfaz de usuario:**

* En ocasiones, la interfaz de la aplicación de escritorio puede quedar en blanco. Right-click and click [!UICONTROL Refresh] to re-load the application. Después de una actualización de este tipo, inicio en la raíz del repositorio DAM. Se conservan las actualizaciones o los estados de los recursos. <!-- CQ-4270267 -->
* Difícil desplazarse por las carpetas o los resultados de la búsqueda sin un panel de seguimiento o un puntero del ratón. The scroll-bar might not appear with mouse devices without mouse wheel. <!-- CQ-4269947 -->
* De forma poco frecuente, la barra de progreso no se muestra correctamente cuando se producen cambios en el recurso que se carga.
* Después de aplicar y quitar el filtro para buscar todos los recursos editados a nivel local, la aplicación no lleva a los usuarios a la vista de carpetas o a los resultados de búsqueda con los que los usuarios empezaron. La aplicación muestra la carpeta raíz del repositorio de DAM.
* En ocasiones, cuando se conecta a una dirección URL que no tiene el servidor AEM en ejecución, la pantalla de conexión deja de responder. Salga de la aplicación y vuelva a iniciarla.

**Problemas de CRUD (Crear, Leer, Actualizar y Eliminar):**

* La aplicación intenta cargar archivos incluso cuando incluye caracteres no válidos, lo que puede provocar un error de carga en el servidor. <!-- CQ-4273652 -->
* Al cargar cambios en un recurso con comentarios, los comentarios se almacenan con el recurso en AEM, pero no se pueden ver como comentarios de versiones. Este problema se ha resuelto en AEM 6.4.5 y AEM 6.5.1. Adobe recomienda encarecidamente instalar los Service Packs más recientes. <!-- CQ-4268990 -->
* El usuario no puede cancelar las transferencias de recursos. Si ha activado una transferencia de gran volumen sin querer, salga de la aplicación y vuelva a iniciarla. <!-- CQ-4278940 -->

**Problemas de la plataforma:**

* En ocasiones, en Windows, el estado de un recurso puede cambiar inmediatamente a [!UICONTROL Edited Locally] después de abrirlo, aunque no lo haya editado. Haga clic en [!UICONTROL Refresh] para actualizar.

>[!MORELIKETHIS]
>
>* [Documentación de AEM como servicio de nube](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/landing/home.html)
>* [Documentación de AEM as a Cloud Service Assets](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/home.html)
>* [Cómo utilizar la aplicación de escritorio de Experience Manager](using.md)
>* [Instalación y actualización de la aplicación de escritorio](install-upgrade.md)
>* [Procedimientos recomendados y sugerencias para la solución de problemas](troubleshoot.md)

