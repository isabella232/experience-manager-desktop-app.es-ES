---
title: Notas de la versión de la aplicación de escritorio de AEM
seo-title: Notas de la versión de la aplicación de escritorio de AEM
description: Detalles de la versión, mejoras, nuevas funciones, compatibilidad y vínculos de descarga para la aplicación de escritorio de AEM v1.x.
seo-description: Detalles de la versión, mejoras, nuevas funciones, compatibilidad y vínculos de descarga para la aplicación de escritorio de AEM v1.x.
uuid: b783c3f8-aa1e-4c05-b687-5894909769f5
contentOwner: asgupta
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: 3052549b-fe75-44fb-a55e-5cc612868f54
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b74a3ff5c9a25ee1433dd661a1bce677271a5ebe

---


# Notas de la versión de la aplicación de escritorio de AEM {#release-notes-v2}

| Productos | Aplicación de escritorio de Adobe Experience Manager (AEM) |
|---------------|--------------------------------------------------------------------|
| Versión de la aplicación (revisión) | 2.0 (2.0.0.4) |
| Versiones de AEM admitidas | AEM 6.5, AEM 6.4, AEM 6.3 (con paquete de compatibilidad) |
| Tipo | Versión principal |
| Fecha de lanzamiento | 30 de agosto de 2019 (Mac), 9 de septiembre de 2019 (Win) |
| Descargar direcciones URL | [MacOS de 64 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-osx-2.0.0.4.dmg); [Windows de 64 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win64-2.0.0.4.exe); [Windows de 32 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win32-2.0.0.4.exe) |

## Requisitos y requisitos previos del sistema {#system-requirements-and-prerequisites-v2}

La aplicación de escritorio AEM es compatible con los siguientes sistemas operativos:

* Mac OS X 10.10 o posterior, con las últimas correcciones de errores.
* Windows 7 y Windows 10 con los paquetes de servicios y las correcciones de errores más recientes.

La aplicación funciona con las siguientes versiones de AEM, tanto si se implementa in situ como en los servicios gestionados de Adobe (AMS):

* [AEM 6.5.0](https://helpx.adobe.com/experience-manager/6-5/release-notes.html) o posterior
* [AEM 6.4.4](https://helpx.adobe.com/experience-manager/6-4/release-notes/sp-release-notes.html) o posterior
* AEM 6.4.0 - 6.4.3 con paquete de [compatibilidad](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)
* AEM 6.3.3.1 y posterior con paquete de [compatibilidad](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support)
* En AEM 6.3, no se han planificado [paquetes](https://helpx.adobe.com/experience-manager/maintenance-releases-roadmap.html)de servicios. Adobe recomienda actualizar a una versión posterior de AEM.

La versión de la aplicación que planea instalar en su equipo local requiere una versión específica del servidor de Adobe Experience Manager/componentes adicionales del servidor (Service Packs, correcciones rápidas o paquetes de funciones). Póngase en contacto con el administrador de AEM para obtener ayuda.

### Compatibilidad con distintos tipos de recursos y archivos {#support-for-file-types}

La aplicación admite recursos almacenados en AEM que representan archivos binarios para sus operaciones básicas. La apertura de archivos en la aplicación de escritorio nativa depende de la asociación del sistema operativo de los tipos de archivo específicos como PNG o JPG a aplicaciones específicas como Mac Preview o Adobe Photoshop.

Algunos tipos de archivo admiten la colocación de recursos vinculados en el binario. La aplicación descarga previamente los recursos vinculados si el recurso está presente en el repositorio de AEM cuando estos archivos binarios se abren con la aplicación de escritorio. Los tipos de archivo admitidos actualmente son:

* Archivos de Adobe InDesign (formato INDD)
* Archivos de Adobe Illustrator (formato AI)
* Archivos de Adobe Photoshop (formato PS)

La función es compatible con las versiones de Adobe Creative Cloud 2018 y Creative Cloud 2019 de la aplicación anterior. La aplicación utiliza un método heurístico y de mejor coincidencia para asignar las rutas de escritorio locales de los recursos vinculados a las URL en el servidor AEM. Se basa en algunos supuestos:

* Las rutas para colocar archivos en la aplicación nativa utilizan una ruta de escritorio global (desde el recurso compartido de red local que se muestra con la opción "Revelar")
* La aplicación nativa almacena las rutas en el registro XMP del archivo
* AEM ha extraído el registro XMP con las rutas al registro de metadatos del recurso
* Las rutas pueden coincidir con los recursos en AEM (es decir, los archivos colocados también están en AEM en una ruta coincidente)

## Nuevas funciones y mejoras {#whats-new-added}

Para obtener más información, consulte [Novedades de la aplicación](introduction.md#whats-new-v2).

## Instrucciones de instalación {#installation-instructions-v2}

Para obtener información sobre cómo instalar y configurar la aplicación, consulte [Instalación de la aplicación](install-upgrade.md)de escritorio AEM.

Si va a realizar la actualización desde una aplicación de escritorio de AEM anterior, debe seguir estas prácticas recomendadas para la transición que se enumeran en la [actualización desde la versión](install-upgrade.md#upgrade-from-previous-version)anterior.

## Notas importantes sobre el funcionamiento de la aplicación {#how-app-works}

Es importante comprender lo siguiente sobre la aplicación y cómo funciona.

* La aplicación proporciona control total sobre las operaciones que requieren la transferencia completa de archivos binarios de recursos desde y hacia AEM (abrir, editar, cargar cambios y cargar recursos).
   * Si desea trabajar con el recurso en el escritorio, debe abrir, editar o descargar explícitamente en el escritorio, ya sea individualmente, en una carpeta o mediante selección múltiple.
   * Si desea realizar cambios locales en los recursos cargados en AEM, debe seleccionarlos [!UICONTROL Upload Changes], ya sea individualmente o mediante selección múltiple.
   * La aplicación no es un 'cliente de sincronización' que sincroniza recursos en el escritorio y en AEM.
   * La aplicación no proporciona un recurso compartido de red que asigne el repositorio de AEM como una estructura de carpetas virtuales.
* La lista de recursos mostrada por la aplicación se basa en el estado del repositorio de AEM Assets. La aplicación no muestra ni gestiona ningún archivo descargado localmente y cuyo nombre haya cambiado en los archivos locales o en la carpeta de caché.
* Si la aplicación no muestra los resultados esperados, haga clic en el icono de actualización en la barra superior.
* El recurso compartido de red local, que se muestra cuando se usa [!UICONTROL Reveal File] action, solo muestra los archivos (y carpetas) disponibles localmente. [!UICONTROL Reveal File] y [!UICONTROL Reveal Folder] predescarga recursos para ayudar a que se muestren los recursos correctos en el recurso compartido de red local.
* El recurso compartido de red local SMB (Mac)/WebDAV (Win) se utiliza cuando una aplicación de Adobe Creative Cloud lee los archivos de recursos vinculados/colocados en un archivo nativo de la aplicación de Creative Cloud.

El diagrama siguiente ilustra el flujo de recursos y archivos desde la nube al sistema de archivos local y viceversa, tal como se inicia con las acciones del usuario.

![Flujo de recursos desde el servidor AEM a las aplicaciones de escritorio nativas a través de la aplicación de escritorio](assets/do-not-localize/da20_flow_diagram.png)

## Known issues {#known-issues-v2}

**Problemas de la interfaz de usuario:**
* En ocasiones, la interfaz de la aplicación de escritorio podría quedar en blanco. Haga clic con el botón secundario y haga clic [!UICONTROL Refresh] para cargar la aplicación de nuevo. Esta actualización restablece el estado de la aplicación y comienza en la pantalla de bienvenida en la raíz del repositorio de DAM. <!-- CQ-4270267 -->
* Difícil desplazarse por las carpetas o los resultados de búsqueda sin un trackpad o rueda del ratón. Es posible que la barra de desplazamiento no aparezca con los dispositivos del ratón sin la rueda del ratón. <!-- CQ-4269947 -->
* Con poca frecuencia, la barra de progreso no se muestra correctamente cuando cambia el recurso que se carga.
* Después de aplicar y quitar el filtro para buscar todos los recursos editados localmente, la aplicación no lleva a los usuarios a los resultados de búsqueda o a la vista de carpetas con los que los usuarios han empezado. La aplicación muestra la carpeta raíz del repositorio de DAM.
* En ocasiones, cuando se conecta a una URL que no tiene el servidor AEM en ejecución, la pantalla de conexión deja de responder. Salga de la aplicación y vuelva a iniciarla.

**Problemas de CRUD (Crear, Leer, Actualizar y Eliminar):**
* La aplicación intenta cargar archivos incluso con caracteres no válidos, lo que puede provocar un error de carga en el servidor. <!-- CQ-4273652 -->
* Al cargar cambios en un recurso con comentarios, los comentarios se almacenan con el recurso en AEM, pero no se pueden ver como comentarios de versiones (resueltos en AEM 6.4.5, 6.5.1). <!-- CQ-4268990 -->
* El usuario no puede cancelar las transferencias de recursos. Si ha activado una transferencia grande no deseada, salga de la aplicación y vuelva a iniciarla. <!-- CQ-4278940 -->

**Problemas de plataforma:**
* En ocasiones, en Windows, el estado de un recurso puede cambiar inmediatamente a [!UICONTROL Edited Locally] después de abrirlo, aunque no lo haya editado. Haga clic [!UICONTROL Refresh] para actualizar.

>[!MORELIKETHIS]
>
>* [Documentación de AEM 6.5](https://helpx.adobe.com/support/experience-manager/6-5.html)
>* [Documentación de AEM Assets 6.5](https://docs.adobe.com/content/help/en/experience-manager-64/assets/home.html)
>* [Uso de la aplicación de escritorio de AEM](using.md)
>* [Instalación y actualización de la aplicación de escritorio](install-upgrade.md)
>* [Prácticas recomendadas y sugerencias para la solución de problemas](troubleshoot.md)

