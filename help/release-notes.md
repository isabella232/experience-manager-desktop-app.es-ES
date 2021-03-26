---
title: '[!DNL Adobe Experience Manager] Notas de la versión de la aplicación de escritorio'
description: Detalles de la versión, mejoras, nuevas funciones, compatibilidad y vínculos de descarga para la aplicación de escritorio [!DNL Adobe Experience Manager] .
mini-toc-levels: 1
feature: Experience Manager Aplicación de escritorio, información de la versión
translation-type: tm+mt
source-git-commit: e8a299c7357faf2c19c11a56f2868f6679c15ac1
workflow-type: tm+mt
source-wordcount: '1507'
ht-degree: 28%

---


# [!DNL Adobe Experience Manager] Notas de la versión de la aplicación de escritorio  {#release-notes-v2}

A continuación se muestra la información de la versión 2.1 (2.1.2.0) de la aplicación de escritorio más reciente. La fecha de la versión es el 26 de marzo de 2021. Se trata de una versión menor con una mejora.

Las **versiones [!DNL Experience Manager] compatibles** son:

* [!DNL Experience Manager] as a [!DNL Cloud Service]. Consulte [notas de la versión](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/home.html?lang=es).
* [!DNL Experience Manager] 6.5.0 o posterior, en Adobe Managed Services (AMS) o local. Consulte las [notas de la versión del Service Pack](https://experienceleague.adobe.com/docs/experience-manager-65/release-notes/service-pack/sp-release-notes.html?lang=es).
* [!DNL Experience Manager] 6.4.4 o posterior, en Adobe Managed Services (AMS) o local. Consulte las [notas de la versión del Service Pack](https://experienceleague.adobe.com/docs/experience-manager-64/release-notes/sp-release-notes.html?lang=es).
* [!DNL Experience Manager] 6.4.0 - 6.4.3 con el paquete de  [compatibilidad ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) instalado, en Adobe Managed Services (AMS) o On-Premise.
* [!DNL Experience Manager] 6.3 (con paquete de compatibilidad)
* [!DNL Experience Manager] 6.3.3.1 o posterior con el paquete de  [compatibilidad ](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/featurepack/adobe-asset-link-support) instalado. La aplicación de escritorio no es compatible con [!DNL Experience Manager] 6.3.3.0 ni con versiones anteriores.

[!DNL Adobe Experience Manager] la aplicación de escritorio está disponible para los siguientes sistemas  **operativos**:

* macOS X 10.14 o posterior, con las últimas correcciones de errores.
* Windows 10 con los paquetes de servicios y las correcciones de errores más recientes.

Las **URL de descarga** para el sistema operativo compatible son:

| Sistema operativo | [!DNL Experience Manager] as a [!DNL Cloud Service] | [!DNL Experience Manager] 6.x |
|---|---|---|
| macOS de 64 bits | [Vínculo de descarga](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-osx-2.1.2.0.dmg) | [Vínculo de descarga](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-osx-2.1.2.0.dmg) |
| Windows de 64 bits | [Vínculo de descarga](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-win64-2.1.2.0.exe) | [Vínculo de descarga](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win64-2.1.2.0.exe) |
| Windows de 32 bits | [Vínculo de descarga](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html?package=/content/software-distribution/en/details.html/content/dam/aemcloud/public/aem-desktop-app/aem-desktop-win32-2.1.2.0.exe) | [Vínculo de descarga](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win32-2.1.2.0.exe) |

>[!NOTE]
>
>Windows 7 ya no es compatible. Consulte [el artículo sobre EOL de Windows 7](https://support.microsoft.com/en-us/help/4057281/windows-7-support-ended-on-january-14-2020).

<!-- The version of the app you plan to install on your local machine requires a specific [!DNL Adobe Experience Manager] server version/additional server-side components (service packs, hot fixes, or feature packs). Contact your [!DNL Experience Manager] administrator for help.
-->

## Compatibilidad con distintos activos y tipos de archivos {#support-for-file-types}

La aplicación admite activos almacenados en [!DNL Experience Manager] que representan archivos binarios para sus operaciones básicas. La apertura de archivos en la aplicación de escritorio nativa depende de la asociación de sistema operativo de los tipos de archivo específicos, como PNG o JPG, a aplicaciones específicas, como Vista previa de Mac o Adobe Photoshop.

Algunos tipos de archivo admiten la colocación de recursos vinculados en el archivo binario. La aplicación descarga previamente los recursos vinculados si el recurso está presente en el repositorio [!DNL Experience Manager] cuando estos archivos binarios se abren con la aplicación de escritorio. Los tipos de archivo admitidos actualmente son:

* [!DNL Adobe InDesign] archivos (formato INDD)
* [!DNL Adobe Illustrator] archivos (formato AI)
* [!DNL Adobe Photoshop] archivos (formato PS)

La función es compatible con las versiones [!DNL Adobe Creative Cloud] 2018 y [!DNL Adobe Creative Cloud] 2019 de la aplicación anterior. La aplicación utiliza un método heurístico que se adapta mejor a las rutas de escritorio locales de los recursos vinculados a las URL en el servidor [!DNL Experience Manager]. Se basa en algunos supuestos:

* Las rutas para colocar archivos en la aplicación nativa utilizan una ruta de escritorio global (ubicada desde el recurso compartido de red local que se muestra con la opción [!UICONTROL Reveal] ).

* La aplicación nativa almacena las rutas en el registro XMP del archivo.

* [!DNL Experience Manager] ha extraído el registro XMP con las rutas al registro de metadatos del recurso.

* Las rutas pueden coincidir con los recursos de [!DNL Experience Manager], es decir, los archivos colocados también están en [!DNL Experience Manager] en una ruta coincidente.

## Nuevas funciones, mejoras y correcciones de errores {#what-is-new}

Para conocer los detalles, consulte [Novedades de v2.0](introduction.md#whats-new-v2).

**Actualización en la aplicación v2.1.2.0**

* Se agrega una nueva opción a [!UICONTROL Clear Cookies] al menú principal de la aplicación. Ayuda con posibles problemas de inicio de sesión, por ejemplo, al cambiar la conexión de un servidor a otro.

**Actualización en la aplicación v2.1.1.0**

* Una configuración avanzada permite que la aplicación emule el comportamiento de la aplicación v1.10 al cargar carpetas. En v1.10, los nombres de nodo creados en el repositorio respetan los espacios y el formato en mayúsculas de los nombres de carpeta proporcionados por el usuario. El comportamiento predeterminado de v2.1 sigue siendo el mismo, es decir, reemplaza varios espacios en los nombres de carpetas con un guión en el nombre del nodo del repositorio y convierte en nombres de nodos en minúsculas. Consulte [las preferencias de la aplicación](/help/install-upgrade.md#set-preferences).

**Actualización en la aplicación v2.1.0.0**

* Para cargar recursos, los usuarios ahora pueden arrastrar los archivos o carpetas de la interfaz de la aplicación, directamente desde el Explorador de Windows o el Buscador de Mac. Esto funciona además de la opción de carga previamente disponible en la aplicación. <!-- CQ-4309527 -->

**Actualización en la aplicación v2.0.3**

El error corregido en la versión actual es:

* Se ha corregido un problema de inicio de sesión para usuarios de aplicaciones en Windows que intentan acceder al repositorio de DAM en [!DNL Adobe Experience Manager] 6.5.5.0.

**Actualizaciones en la aplicación v2.0.2**

Las correcciones y actualizaciones de errores son:

* La configuración de aceleración de carga ya está disponible para mejorar el rendimiento de carga. Cuando se activa esta configuración, la aplicación se carga más rápido mediante más subprocesos de CPU locales y consume más recursos.

* Cargas de recursos cuando los nombres de archivo o las rutas que contienen ciertos caracteres GB18030 están fijos. <!-- CQ-4283494 -->

* La opción Ordenar por relevancia está disponible después de cambiar a otro tipo de ordenación en los resultados de búsqueda. <!-- CQ-4286874 -->

* La aplicación de escritorio ahora enumera las subcarpetas sin necesidad de actualizarlas explícitamente. <!-- CQ-4285711 -->

* (Windows) Se ha corregido un problema poco frecuente de la interfaz de aplicación no utilizable en algunos equipos con Windows. Los usuarios no pueden hacer clic en la interfaz de la aplicación porque parece distorsionada con el área de clic de los elementos de la interfaz &quot;desplazados&quot; hacia el lateral. <!-- CQ-4280785 -->

**Actualizaciones en la aplicación v2.0.1**

Las correcciones y actualizaciones de errores son:

* Permitir opción para configurar el directorio `%Temp%` para que coincida con la ruta `%APPDATA%`. <!-- CQ-4282665 -->

* Permita que los usuarios inicien sesión en [!DNL Experience Manager] Author a través de la autenticación Okta SAML. <!-- CQ-4278134 -->

## Instrucciones de instalación {#installation-instructions-v2}

Para obtener información sobre cómo instalar y configurar la aplicación, consulte [Instalar [!DNL Experience Manager] aplicación de escritorio](install-upgrade.md).

Si está actualizando desde una aplicación de escritorio anterior [!DNL Experience Manager], debe seguir estas prácticas recomendadas para la transición que se enumeran en [actualización de la versión anterior](install-upgrade.md#upgrade-from-previous-version).

## Notas importantes sobre el funcionamiento de la aplicación {#how-app-works}

Es importante comprender lo siguiente sobre la aplicación y su funcionamiento.

* La aplicación proporciona control total sobre las operaciones que requieren la transferencia completa de archivos binarios de recursos de y a [!DNL Experience Manager] (abrir, editar, cargar cambios y cargar recursos).

   * Si desea trabajar con el recurso en el escritorio, debe abrir, editar o descargar explícitamente en el escritorio, ya sea de forma individual, en una carpeta o mediante selección múltiple.

   * Si desea obtener cambios locales en los recursos cargados en [!DNL Experience Manager], debe seleccionar [!UICONTROL Upload Changes], ya sea de forma individual o mediante selección múltiple.

   * La aplicación no es un &quot;cliente de sincronización&quot; que sincroniza recursos en el escritorio y en [!DNL Experience Manager].

   * La aplicación no proporciona un recurso compartido de red que asigne el repositorio [!DNL Experience Manager] como una estructura de carpetas virtuales.

* La aplicación muestra una lista de recursos que se basa en el estado del repositorio de Assets. La aplicación no muestra ni administra ningún archivo descargado localmente y cuyo nombre haya cambiado en los archivos locales o en la carpeta de caché.

* Si la aplicación no muestra los resultados esperados, haga clic en el icono de actualización situado en la barra superior.

* El recurso compartido de red local, que se muestra cuando se usa la acción [!UICONTROL Reveal File], solo muestra los archivos (y carpetas) disponibles a nivel local. [!UICONTROL Reveal File] y [!UICONTROL Reveal Folder] descarga previamente los recursos para que se muestren los que son correctos en el recurso compartido de red local.

* El recurso compartido de red local SMB (Mac) o WebDAV (Win) se utiliza cuando una aplicación de Adobe Creative Cloud lee los archivos de recursos vinculados o colocados en un archivo nativo de la aplicación de Creative Cloud.

En el diagrama siguiente se ilustra el flujo de recursos y archivos desde la nube al sistema de archivos local y de forma opuesta, tal como lo inician las acciones del usuario.

![[!DNL Experience Manager]Flujo de recursos desde el servidor de a las aplicaciones de escritorio nativas a través de la aplicación de escritorio](assets/da20_flow_diagram.png)

## Problemas conocidos {#known-issues-v2}

**Problemas de la interfaz de usuario:**

* A veces, la interfaz de la aplicación de escritorio puede quedar en blanco. Haga clic con el botón derecho del ratón y haga clic en [!UICONTROL Refresh] para volver a cargar la aplicación. Después de esta actualización, se inicia en la raíz del repositorio de DAM. Se conservan las actualizaciones o los estados de los recursos. <!-- CQ-4270267 -->

* Es difícil navegar por carpetas o buscar resultados sin un panel de seguimiento o un puntero del ratón. Es posible que la barra de desplazamiento no aparezca en los dispositivos que utilizan ratón sin rueda. <!-- CQ-4269947 -->

* De forma poco frecuente, la barra de progreso no se muestra correctamente cuando se producen cambios en el recurso que se carga.

* Después de aplicar y quitar el filtro para buscar todos los recursos editados a nivel local, la aplicación no lleva a los usuarios a la vista de carpetas o a los resultados de búsqueda con los que los usuarios empezaron. La aplicación muestra la carpeta raíz del repositorio de DAM.

* A veces, cuando se conecta a una dirección URL que no tiene [!DNL Experience Manager] servidor en ejecución, la pantalla de conexión deja de responder. Salga de la aplicación y vuelva a iniciarla.

**Problemas de CRUD (Crear, Leer, Actualizar y Eliminar):**

* La aplicación intenta cargar archivos incluso cuando incluye caracteres no válidos, lo que puede provocar un error de carga en el servidor. <!-- CQ-4273652 -->

* Al cargar cambios en un recurso con comentarios, los comentarios se almacenan con el recurso en [!DNL Experience Manager] pero no se pueden ver como comentarios de versiones. Este problema se resuelve en [!DNL Experience Manager] 6.4.5 y [!DNL Experience Manager] 6.5.1. Adobe recomienda instalar los service packs más recientes. <!-- CQ-4268990 -->

* El usuario no puede cancelar las transferencias de recursos. Si ha activado una transferencia de gran volumen sin querer, salga de la aplicación y vuelva a iniciarla. <!-- CQ-4278940 -->

**Problemas de la plataforma:**

* En ocasiones, en Windows, el estado de un recurso puede cambiar inmediatamente a [!UICONTROL Edited Locally] después de abrirlo, aunque no lo haya editado. Haga clic en [!UICONTROL Refresh] para actualizar.

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] documentación.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/landing/home.html)
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] [!DNL Assets] documentación.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/home.html)
>* [Cómo usar la aplicación de  [!DNL Experience Manager] escritorio](using.md)
>* [Instalación y actualización de la aplicación de escritorio](install-upgrade.md)
>* [Procedimientos recomendados y sugerencias para la solución de problemas](troubleshoot.md)

