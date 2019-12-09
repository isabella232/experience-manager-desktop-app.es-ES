---
title: Notas de la versión de la aplicación de escritorio de AEM
description: Detalles de la versión, mejoras, nuevas funciones, compatibilidad y vínculos de descarga para la aplicación de escritorio de AEM.
uuid: b783c3f8-aa1e-4c05-b687-5894909769f5
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: 3052549b-fe75-44fb-a55e-5cc612868f54
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ad5337c8e1697d0a37d3020d25802dc1d732f320

---


# Notas de la versión de la aplicación de escritorio de AEM {#release-notes-v2}

| Productos | Aplicación de escritorio de Adobe Experience Manager (AEM) |
|---------------|--------------------------------------------------------------------|
| Versión de la aplicación (revisión) | 2.0 (2.0.0.4) |
| Versiones de AEM compatibles | AEM 6.5, AEM 6.4, AEM 6.3 (con paquete de compatibilidad) |
| Tipo | Versión principal |
| Fecha de lanzamiento | 30 de agosto de 2019 (Mac), 9 de septiembre de 2019 (Win) |
| Direcciones URL de descarga | [MacOS de 64 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-osx-2.0.0.4.dmg); [Windows de 64 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win64-2.0.0.4.exe); [Windows de 32 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win32-2.0.0.4.exe) |

## Requisitos y requisitos previos del sistema {#system-requirements-and-prerequisites-v2}

La aplicación de escritorio de AEM es compatible con los siguientes sistemas operativos:

* Mac OS X 10.10 o posterior, con las últimas correcciones de errores.
* Windows 7 y Windows 10 con los paquetes de servicios y las correcciones de errores más recientes.

La aplicación funciona con las siguientes versiones de AEM, tanto si se implementa in situ como en Adobe Managed Services (AMS):

* [AEM 6.5.0](https://helpx.adobe.com/experience-manager/6-5/release-notes.html) o posterior
* [AEM 6.4.4](https://helpx.adobe.com/experience-manager/6-4/release-notes/sp-release-notes.html) o posterior
* AEM 6.4.0 - 6.4.3 con [paquete de compatibilidad](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)
* AEM 6.3.3.1 y posterior con [paquete de compatibilidad](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)
* En AEM 6.3, no se [han planificado paquetes de servicios](https://helpx.adobe.com/experience-manager/maintenance-releases-roadmap.html). Adobe recomienda actualizar a una versión posterior de AEM.

La versión de la aplicación que planea instalar en su equipo local requiere una versión específica del servidor de Adobe Experience Manager o componentes adicionales del servidor (paquetes de servicio, correcciones rápidas o paquetes de funciones). Póngase en contacto con el administrador de AEM para obtener ayuda.

### Compatibilidad con distintos tipos de recursos y archivos {#support-for-file-types}

La aplicación admite recursos almacenados en AEM que representan archivos binarios para sus operaciones básicas. La apertura de archivos en la aplicación de escritorio nativa depende de la asociación de sistema operativo de los tipos de archivo específicos, como PNG o JPG, a aplicaciones específicas, como Vista previa de Mac o Adobe Photoshop.

Algunos tipos de archivo admiten la colocación de recursos vinculados en el archivo binario. La aplicación descarga previamente los recursos vinculados si el recurso está presente en el repositorio de AEM cuando estos archivos binarios se abren con la aplicación de escritorio. Los tipos de archivo admitidos actualmente son:

* Archivos de Adobe InDesign (formato INDD)
* Archivos de Adobe Illustrator (formato AI)
* Archivos de Adobe Photoshop (formato PS)

La función es compatible con las versiones de Adobe Creative Cloud 2018 y Creative Cloud 2019 de la aplicación anterior. La aplicación utiliza un método heurístico que busca la mejor coincidencia para asignar las rutas de escritorio locales de los recursos vinculados a las URL en el servidor de AEM. Se basa en algunos supuestos:

* Las rutas para colocar archivos en la aplicación nativa usan una ruta de escritorio global (desde el recurso compartido de red local que se muestra con la opción "Revelar")
* La aplicación nativa almacena las rutas en el registro XMP del archivo
* AEM ha extraído el registro XMP con las rutas al registro de metadatos del recurso
* Las rutas pueden coincidir con los recursos en AEM (es decir, los archivos colocados también están en AEM en una ruta coincidente)

## Nuevas funciones y mejoras {#whats-new-added}

Para obtener más información, consulte [Novedades de la aplicación](introduction.md#whats-new-v2).

## Instrucciones de instalación {#installation-instructions-v2}

Para obtener información sobre cómo instalar y configurar la aplicación, consulte [Instalación de la aplicación de escritorio de AEM](install-upgrade.md).

Si va a realizar la actualización desde una aplicación de escritorio de AEM anterior, debe seguir estos procedimientos recomendados para la transición y que se enumeran en [Actualización de la aplicación v1.x a la aplicación v2](install-upgrade.md#upgrade-from-previous-version).

## Notas importantes sobre el funcionamiento de la aplicación {#how-app-works}

Es importante comprender lo siguiente sobre la aplicación y su funcionamiento.

* La aplicación proporciona control total sobre las operaciones que requieren la transferencia completa de archivos binarios de recursos desde y hacia AEM (abrir, editar, cargar cambios y cargar recursos).
   * Si desea trabajar con el recurso en el escritorio, debe abrir, editar o descargar contenido en el mismo escritorio, ya sea de forma individual, en una carpeta o mediante selección múltiple.
   * Si desea realizar cambios locales en los recursos cargados en AEM, debe seleccionarlos [!UICONTROL Upload Changes], ya sea de forma individual o mediante selección múltiple.
   * La aplicación no es un "cliente de sincronización" que sincroniza recursos en el escritorio y en AEM.
   * La aplicación no proporciona un recurso compartido de red que asigne el repositorio de AEM como una estructura de carpetas virtuales.
* La aplicación muestra una lista de recursos que se basa en el estado del repositorio de AEM Assets. La aplicación no muestra ni administra ningún archivo descargado localmente y cuyo nombre haya cambiado en los archivos locales o en la carpeta de caché.
* Si la aplicación no muestra los resultados esperados, haga clic en el icono de actualización situado en la barra superior.
* El recurso compartido de red local, que se muestra cuando se usa la acción [!UICONTROL Reveal File], solo muestra los archivos (y carpetas) disponibles a nivel local. [!UICONTROL Reveal File] y [!UICONTROL Reveal Folder] descarga previamente los recursos para que se muestren los que son correctos en el recurso compartido de red local.
* El recurso compartido de red local SMB (Mac) o WebDAV (Win) se utiliza cuando una aplicación de Adobe Creative Cloud lee los archivos de recursos vinculados o colocados en un archivo nativo de la aplicación de Creative Cloud.

En el diagrama siguiente se ilustra el flujo de recursos y archivos desde la nube al sistema de archivos local y viceversa, cuando este proceso se inicia mediante las acciones del usuario.

![Flujo de recursos desde el servidor de AEM a las aplicaciones de escritorio nativas a través de la aplicación de escritorio](assets/da20_flow_diagram.png)

## Problemas conocidos {#known-issues-v2}

**Problemas de la interfaz de usuario:**
* En ocasiones, la interfaz de la aplicación de escritorio puede quedar en blanco. Right-click and click [!UICONTROL Refresh] to re-load the application. Después de esta actualización, se inicia en la raíz del repositorio DAM. Se conservan las actualizaciones o los estados de los recursos. <!-- CQ-4270267 -->
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
>* [Documentación de AEM 6.5](https://helpx.adobe.com/support/experience-manager/6-5.html)
>* [Documentación de AEM Assets 6.5](https://docs.adobe.com/content/help/en/experience-manager-64/assets/home.html)
>* [Uso de la aplicación de escritorio de AEM](using.md)
>* [Instalación y actualización de la aplicación de escritorio](install-upgrade.md)
>* [Procedimientos recomendados y sugerencias para la solución de problemas](troubleshoot.md)

