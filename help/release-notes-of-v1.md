---
title: Notas de la versión de la aplicación de escritorio v1.10
description: Detalles de la versión, mejoras, nuevas funciones, compatibilidad y vínculos de descarga para la aplicación de escritorio de AEM versión 1.10.
translation-type: tm+mt
source-git-commit: 4870615ed40226964d077d6666b83b85b73da180
workflow-type: tm+mt
source-wordcount: '3897'
ht-degree: 1%

---


# [!DNL Adobe Experience Manager] notas de la versión 1.10 de la aplicación de escritorio  {#aem-desktop-app-release-notes}

Para la versión v1.x de la aplicación de escritorio, los siguientes son los vínculos de descarga y la información de compatibilidad de AEM.

| Productos | Aplicación de escritorio de [!DNL Adobe Experience Manager]  |
|--- |--- |
| Versión | 1.10 (1.10.0.6 en Mac y 1.10.0.3 en Windows) |
| Tipo | Versión menor |
| Fecha | 1.10.0.6 (Mac): 15 de abril de 2020; 1.10.0.3 (Win): 31 de agosto de 2018 |
| Direcciones URL de descarga | [Mac OS X de 64 bits](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-osx-1.10.0.6.dmg);  [Windows de 32 bits](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win32-1.10.0.3.exe);  [Windows de 64 bits](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/adobe/aem-desktop-app/aem-desktop-win64-1.10.0.3.exe) |
| Compatibilidad | AEM 6.5.x; AEM 6.4.x; AEM 6.3 SP2; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |

>[!NOTE]
>
>No se aplica el límite de tamaño de caché. Cuando se inicia la aplicación de escritorio, el tamaño de la caché se calcula una vez y se muestra una notificación si el tamaño está cerca del límite predefinido.

## Requisitos y requisitos previos del sistema {#system-requirements-and-prerequisites}

[!DNL Adobe Experience Manager]La aplicación de escritorio de es compatible con los siguientes sistemas operativos:

* Mac OS X 10.10 o posterior, con las últimas correcciones de errores.

* Windows 10 con los paquetes de servicios y las correcciones de errores más recientes.

>[!NOTE]
>
>Windows 7 ya no es compatible. Consulte [el artículo sobre EOL de Windows 7](https://support.microsoft.com/en-us/help/4057281/windows-7-support-ended-on-january-14-2020).

Adobe recomienda encarecidamente utilizar la última versión de la aplicación de escritorio de AEM para disponer de las últimas funciones, las correcciones de errores más recientes y el mejor rendimiento posible.

La versión de la aplicación de escritorio de AEM que planea instalar en su equipo local requiere una versión específica del servidor de AEM o componentes adicionales del lado del servidor (paquetes de servicio, correcciones rápidas o paquetes de funciones). Asegúrese de que el servidor AEM esté configurado correctamente antes de conectarse a él por primera vez. Si necesita ayuda, póngase en contacto con el administrador de AEM.

Consulte la [matriz de compatibilidad detallada](#compatibilitymatrix) al final de este documento para evaluar los requisitos previos para la configuración.

## Novedades de la aplicación de escritorio v1.10 {#what-s-new-in-aem-desktop-app}

La aplicación de escritorio de AEM 1.10 se centra en mejorar la experiencia del usuario en las cargas grandes, la información sobre las operaciones en segundo plano y la experiencia optimizada al abrir recursos con archivos vinculados (como InDesign).

>[!NOTE]
>
>Si utiliza macOS 10.15.4 o posterior, utilice al menos la versión 1.10.0.6 de la aplicación. Esta versión del parche cumple con los [requisitos de notarización de Apple](https://developer.apple.com/news/?id=04102019a).

**Edición/Extracción** locales: Las cargas automáticas de los cambios guardados en los recursos se pueden deshabilitar en la ventana de estado. De este modo, el usuario puede seguir trabajando en archivos y guardando cambios y, cuando esté listo, decidir cargar todos los cambios.

**Ventana** de estado del recurso simplificado. Se ha simplificado la ventana de estado. La pestaña [!UICONTROL Uploads] ahora muestra recursos individuales, así como cargas masivas o de carpetas. Se ha eliminado la pestaña Carga masiva anterior.

**Icono de aplicación para indicar cargas masivas**. El icono de la aplicación indica que una carga masiva está en curso al mostrar una superposición de &quot;transferencia&quot;.

**Notificaciones de conflictos de actualización**. Cuando la aplicación detecta un conflicto al intentar actualizar un recurso, muestra una notificación para que el usuario pueda revisarla sin necesidad de monitorizar la ventana de estado. Cuando la aplicación se inicie, buscará todos los conflictos para que el usuario pueda resolverlos.

**Mejor manejo de las pérdidas de conexión**. Las cargas masivas se pausarán si se produce una pérdida de conexión y el usuario podrá reanudarlas más tarde. Hay disponible una opción [!UICONTROL Retry] para reintentar una carga fallida de un archivo individual.

## Instrucciones de instalación {#installation-instructions}

Para obtener instrucciones detalladas, consulte [Instalación y configuración de la aplicación de escritorio de AEM](install-configure-app-v1.md).

## Mejoras en las versiones anteriores {#enhancements-in-the-previous-versions}

Esta versión amplía y reemplaza las versiones anteriores de la aplicación de escritorio [!DNL Experience Manager] , que proporciona las siguientes mejoras clave:

* **Versión 1.9/1.9.1**: cargas reanudables, ventana de estado mejorada, iconos de aplicación que indican el estado de la aplicación/conexión, recuperación previa de recursos vinculados para archivos de InDesign.

* **Versión 1.8**: mejor control del tamaño de la caché para el usuario, mejor experiencia de inicio de sesión para SAML/SSO en Windows, compatibilidad con el proxy de red .pac en Mac y problemas notificados por el cliente.

* **Versión 1.7**: mejoras en la estabilidad y la lógica de almacenamiento en caché, mejor compatibilidad con el proxy de red y capacidad para limpiar archivos internos después de la desinstalación.

* **Versión 1.6**: mejoras en el proceso de inicio de sesión para varias configuraciones de seguridad de AEM y estabilidad y rendimiento de la aplicación.

* **Versión 1.5**: estabilidad y flexibilidad de las aplicaciones frente a diversos problemas de red, mejor soporte.

* **Versión 1.4**: la capacidad de cargar carpetas jerárquicas en segundo plano con la supervisión del progreso.

* **Versión 1.3**: mejoras de rendimiento y estabilidad para acceder a archivos y guardar cambios en AEM, especialmente desde aplicaciones de escritorio de Creative Cloud, como InDesign, Illustrator o Photoshop. Su objetivo era ofrecer a los usuarios una experiencia más local similar a un escritorio cuando trabajan con archivos, mientras gestionan simultáneamente las operaciones de transferencia de datos de red en segundo plano.

### Mejoras disponibles desde la aplicación de escritorio de AEM 1.9 {#Enhancements-Available-Since-AEM-Desktop-App-19x}

[!DNL Adobe Experience Manager] la aplicación de escritorio 1.9.1 fue una versión de parches para abordar algunos problemas clave del cliente relacionados con el cierre de compra de recursos y la copia de archivos del recurso compartido de red a un directorio local.

* Los recursos extraídos por un usuario no deben estar disponibles para su modificación para otros usuarios (CQ-4246009)

* Compatibilidad con la copia de una carpeta asignada a una carpeta local cuando la carpeta del usuario está en una partición de disco independiente (CQ-4243978)

La aplicación de escritorio de AEM 1.9 se centra en mejorar la experiencia del usuario en las cargas grandes, la información sobre las operaciones en segundo plano y la experiencia optimizada al abrir recursos con archivos vinculados (como InDesign).

**Reanudar**
cargasPara cargas, especialmente alrededor de archivos grandes, existe la opción de pausarlas o reanudarlas en la nueva ventana Estado del recurso.

**Mejora de la**
ventana Estado de los recursosUna ventana de estado de los recursos mejorada proporciona la siguiente información sobre los recursos.

[!UICONTROL Changes]

* Muestra los cambios en cola actualmente.

* Muestra las cargas en curso, incluida una barra de progreso, la tasa de transferencia, el tamaño total del archivo y el tamaño transferido hasta el momento.

* Cargas completadas que se muestran con el total transferido y la tasa final.

* Las cargas fallidas se muestran junto con un mensaje de error y la información de transferencia, si está disponible.

* Las cargas que hayan fallado tres veces mostrarán un mensaje de error.

* Los archivos conflictivos que se muestran con un icono en el que el usuario puede hacer clic. Al hacer clic en el icono se muestra un cuadro de diálogo con una explicación y dos opciones:

   * [!UICONTROL Keep Mine] carga inmediatamente el archivo en el servidor.

   * [!UICONTROL Overwrite Mine] elimina inmediatamente el archivo local y descarga una copia nueva del servidor.

[!UICONTROL Downloads]

* Muestra las descargas en curso, incluida una tasa de transferencia y el tamaño transferido hasta el momento.

* Las descargas completadas se muestran con el total transferido, la tasa final y un icono que abrirá el archivo cuando se haga clic en él (solo disponible para archivos únicos).

* Las descargas fallidas se muestran con un mensaje de error y la información de transferencia, si está disponible.

* El pie de página muestra el número total de archivos descargados y la tasa media de transferencia.

* Si un usuario decide abrir o editar varios archivos desde la interfaz web [!DNL Experience Manager Assets], estos se agruparán. Por ejemplo, myasset.jpeg y 4 archivos más.

* Al descargar documentos de InDesign, incluidos los recursos vinculados almacenados en AEM Assets, la aplicación de escritorio descargará primero todos los recursos vinculados antes de abrir el documento [!UICONTROL Adobe InDesign] e indicará la descarga de los recursos vinculados. Por ejemplo, 5 de 24.

[!UICONTROL Bulk Uploads]

La carga de jerarquías de carpetas grandes a través de [!UICONTROL Create] > [!UICONTROL Upload Folder] en la interfaz de usuario web de AEM, o la copia y selección de &quot;Pegar recursos&quot; en Finder o Explorer en el menú contextual de la aplicación de escritorio activarán el uso de este cuadro de diálogo.

* Muestra las cargas en curso, incluida una barra de progreso y el nombre del archivo que se está transfiriendo.

* Las cargas en curso incluyen un icono que cancelará la carga cuando se haga clic en ella. La transferencia se detendrá cuando el archivo que se está transfiriendo finalice.

* Los procesos de transferencia fallidos se muestran con un mensaje de error (solo si falla toda la transferencia).

* Si un archivo individual no se puede transferir, se mostrará en la pestaña como un error. De lo contrario, los archivos individuales no se mostrarán en la pestaña * solo una entrada para toda la carga.

**Iconos para indicar el estado de las operaciones en segundo plano**

El icono de la aplicación indicará el estado de las operaciones en segundo plano para proporcionar una mejor señal visual a los usuarios. Por ejemplo, cuando la aplicación no está conectada a AEM, el icono aparece atenuado, cuando hay una carga activa, muestra una superposición &quot;sincrónica&quot;, etc.

**Recuperación previa de recursos vinculados**

Para mejorar la experiencia del usuario al trabajar con documentos de InDesign que incluyen recursos vinculados almacenados en AEM, la aplicación de escritorio intentará recuperar previamente estos archivos vinculados a la caché local antes de que se descargue y abra el documento de InDesign. De este modo, el usuario tendrá los archivos vinculados disponibles localmente y no tendrá que esperar más cuando acceda a ellos en InDesign (en el panel Vínculos).
Tenga en cuenta que la recuperación previa solo funciona si AEM reconoce los vínculos en el servidor. Un recurso con vínculos reconocidos tendrá una lista de &quot;Referencias&quot; incluida en la vista Propiedades del recurso de InDesign.

### Mejoras disponibles desde la aplicación de escritorio de AEM 1.8.x {#enhancements-available-since-aem-desktop-app-18x}

La aplicación de escritorio de AEM 1.8.1 de seguimiento rápido incorpora mejoras al abrir varios archivos a la vez desde la interfaz de usuario de AEM a la versión 1.8 (CQ-4237747, CQ-4238780). Las mejoras en la aplicación de escritorio 1.8 de AEM son:

* Almacenamiento en caché: nueva interfaz de usuario para administrar la caché de la aplicación de escritorio de AEM (CQ-4208690), que incluye:

   * ver el tamaño de la caché actual

   * definir el tamaño máximo de la caché antes de enviar una notificación

   * El tamaño de la caché se comprueba solo al inicio de la aplicación de escritorio y se muestra una notificación si alcanza el límite configurado

   * el botón borrar caché ya está disponible en la nueva interfaz de usuario

* Inicio de sesión: (Win) Se ha corregido el inicio de sesión en la instancia de AEM configurada para utilizar SAML y SSL (CQ-4216353)

* Red:

   * cuando caduca una sesión de AEM, ahora se notifica al usuario y puede hacer clic en la notificación para iniciar sesión de nuevo (CQ-4202028).

   * (Mac) Añada compatibilidad para conectarse a AEM mediante el uso de la configuración proxy .pac (CQ-4233430).

   * (Win) corrija problemas con Advanced - Login URL dialog (CQ-4236061).

* Corrección de errores:

   * Más información del recurso en el cuadro de diálogo: a veces la barra de acciones no estaba visible (CQ-4208540).

   * (Win) Ahora, el archivo se puede sincronizar después de revertir a una versión anterior desde la interfaz de usuario de AEM Assets (CQ-4216411).

### Mejoras disponibles desde la aplicación de escritorio de AEM 1.7 {#Enhancements-Available-Since-AEM-Desktop-App-17}

* Estabilidad:

   * Se ha mejorado la estabilidad cuando la aplicación de escritorio de AEM se conecta a un servidor AEM sobrecargado (CQ-4224803).

   * Se ha mejorado la estabilidad cuando se solicitan muchos archivos (CQ-4224212).

   * Actualización de recursos mejorada con comprobación adicional (CQ-4228291).

* Almacenamiento en caché:

   * Corrija errores de disco y abra problemas al abrir archivos en Photoshop, InDesign, Finder (CQ-4223993, CQ-4217603, CQ-4223717).

   * Se ha mejorado el almacenamiento en caché para evitar binarios de tamaño cero (CQ-4216599).

* Inicio de sesión: Permita la conexión con el código de SSL estricto deshabilitado para configuraciones especiales (como certificados emitidos localmente) (CQ-4223949).

* Redes: Se ha mejorado la compatibilidad con la conexión a través del proxy de red (CQ-4223477, CQ-4221280, CQ-4206854).

* Instalación y desinstalación:

   * (Win) Desinstalación más limpia (CQ-4220906).

   * [Windows 32]  bitInstaller no intenta instalar Microsoft .NET Framework v. 4.5 (CQ-4218084).

   * (Mac) Secuencia de comandos manual para eliminar archivos de aplicaciones de escritorio por completo (CQ-4216489).

>[!NOTE]
>
>Los problemas encontrados en las cargas beta de la aplicación de escritorio de AEM 1.7 (que no estaban presentes en la versión 1.6 no se notifican en las notas de la versión).

### Mejoras disponibles desde la aplicación de escritorio de AEM 1.6 {#Enhancements-Available-Since-AEM-Desktop-App-16}

* Documentación: Nueva documentación [Prácticas recomendadas para la aplicación v1.x](/help/best-practices-for-v1.md).

* Se ha mejorado el proceso de inicio de sesión en AEM:

   * Mejorar la gestión de SAML * relajar las reglas (CQ-4202781).

   * Añada la capacidad de configurar direcciones URL de inicio de sesión independientes en Preferencias (CQ-4214052, CQ-4214051).

* Uso: Notificar al usuario cuando el recurso aún se esté descargando para activos más grandes (CQ-4216284).

* Redes:

   * Almacenamiento en caché DNS (CQ-4210176).

   * Compatibilidad con la conexión mediante proxy en Windows (CQ-4206854).

* Almacenamiento en caché y acceso al recurso compartido de red en Finder/Explorer:

   * El icono de candado ahora está visible para los recursos desprotegidos en Windows 10 (CQ-90957).

   * El contenido de la carpeta puede desaparecer o reaparecer en el recurso compartido de red (CQ-4209160, CQ-4210180).

   * Error en la carga de archivos debido a un conflicto registrado en el Estado de cola de carga (CQ-4215727).

   * Al abrir varios archivos desde la carpeta de la aplicación de escritorio en PS, es posible que se muestren mensajes truncados o incompletos (CQ-4216276).

* Correcciones en estabilidad y rendimiento:

   * Se ha mejorado el rendimiento al examinar carpetas con muchos recursos (CQ-4214933).

   * la aplicación de escritorio 1.5 puede ralentizar el equipo de escritorio a lo largo del tiempo (CQ-4209159).

   * La función Mostrar el estado de la cola solo funciona para el usuario que instaló la aplicación (CQ-4212199).

   * (Windows) Asegúrese de que el instalador de 32 bits no contenga código de 64 bits (CQ-4217406).

* Problemas seleccionados encontrados y corregidos en la beta 1.6:

   * Alto uso de CPU (CQ-4218070).

   * Arrastre y suelte archivos que producen un error al cargarlos en AEM (CQ-4217006).

### Mejoras disponibles desde la aplicación de escritorio de AEM 1.5 {#Enhancements-Available-Since-AEM-Desktop-App-15}

**Versión 1.5.1.5 para Mac OS X:**  La versión 1.5.1.5 ofrece las siguientes ventajas:

* Nuevas funciones y mejoras: Agregue la funcionalidad Copiar/Pegar a la integración de Finder para permitir la transferencia directa de Escritorio a AEM (CQ-4208158).

* Correcciones de errores:

   * Se ha corregido un problema con el error 43 que se producía a veces durante el cambio de nombre de recursos (CQ-4207900).

   * Al volver a una versión anterior desde la línea de tiempo en AEM, el recurso no se actualiza en Finder (CQ-4205194).

   * la aplicación de escritorio se bloquea al examinar directorios anidados de gran tamaño (CQ-4208539).

   * el punto de montaje de la aplicación de escritorio es ahora /Volúmenes/DAM, por lo que es coherente para todos los usuarios (CQ-4208159).

   * Colocar el archivo en InDesign por primera vez inicia una advertencia de actualización (CQ-4207454).

Nota sobre las advertencias de vínculo: Las aplicaciones de Creative Cloud (como InDesign) toman una &quot;instantánea&quot; de la hora de la última modificación del elemento en el momento en que se coloca. Si esa fecha cambia más adelante, la aplicación Adobe Creative Cloud informará de que los vínculos no están actualizados. Esto se informa de dos maneras:

* Cuando se inicie la aplicación Adobe Creative Cloud, se mostrará un cuadro de diálogo en el que se informará al usuario de que los recursos vinculados no están actualizados y se le pedirá que tome medidas.

* Si la aplicación Adobe Creative Cloud ya se está ejecutando, mostrará un icono de advertencia de triángulo amarillo en el recurso vinculado.

Este comportamiento es el mismo para los recursos en el disco local y los recursos en un directorio montado en AEM Desktop, con las siguientes excepciones:

* Si otro usuario modifica un recurso colocado, el icono de advertencia aparecerá la primera vez que otros usuarios abran un documento que contenga el recurso colocado. Esto solo sucede si el recurso colocado ya se ha almacenado en la caché local.

* Si un usuario modifica un recurso colocado a través del directorio montado del escritorio de AEM y luego borra su caché local, el recurso colocado se considerará obsoleto.

Ambos casos son esperados y son efectos secundarios de la arquitectura de &quot;sincronización retardada&quot; de AEM Desktop.

**Versión 1.5.0.x para Mac OS X y Windows:** esta versión de la aplicación de escritorio de AEM ofrece las siguientes ventajas:

* Mejor estabilidad y resiliencia frente a problemas de redes.

   * Asignación más estable de carpetas de AEM Assets (CQ-103276, CQ-4204669, CQ-4203957).

   * Mejor manejo de archivos en caché (CQ-4204336, CQ-4206263).

   * Se ha mejorado el manejo de la descarga/carga de archivos grandes de más de 2 GB de tamaño (CQ-4206438).

   * Se ha corregido el error 36 al mover o cambiar el nombre de un número mayor de archivos en Finder (CQ-4204640).

* Optimizaciones en la comunicación de red con AEM Server (CQ-4204974, CQ-100903).

* Se ha mejorado la fiabilidad de abrir, colocar y guardar recursos de AEM en aplicaciones de Creative Cloud (CQ-4203968, CQ-4205511, CQ-103543, CQ-4207141, CQ-90980).

* Compatibilidad mejorada: para borrar la caché (CQ-4202541), fácil acceso a los registros (CQ-4202340, CQ-4204673).

* Otras correcciones:
   * Mejor compatibilidad con recursos y carpetas con caracteres japoneses en configuración de nombre/idioma que no sea inglés (CQ-4195433, CQ-4205793, CQ-4199446).

   * Mejor manejo del inicio de sesión con SSL (CQ-4200217).

   * Montaje compartido más fiable (CQ-4200793).

   * Varias mejoras en la estabilidad (CQ-4207539, CQ-4200378).

   * Mejor administración de la URL de AEM Assets en Preferencias (CQ-97388).

### Mejoras disponibles desde la aplicación de escritorio de AEM 1.4 {#Enhancements-Available-Since-AEM-Desktop-App-14}

* Carga simplificada de carpetas jerárquicas mediante la nueva acción Crear > Cargar carpeta en la interfaz de usuario táctil.
   * La acción inicia una operación de carga de carpetas realizada por la aplicación de escritorio
   * La aplicación de escritorio atraviesa la jerarquía de carpetas determinada en el escritorio en segundo plano y carga los archivos en AEM Assets
   * El usuario puede controlar el progreso en la nueva ventana Estado de cola de carga con la barra de progreso para las operaciones en curso
   * El estado de la cola de carga también proporciona mejor información sobre la resolución de problemas (por ejemplo, sin conexión con el servidor)
* Nueva acción Editar en la interfaz de usuario táctil, que combina operaciones de desprotección y apertura en una
* Agrupación optimizada de acciones relacionadas con el escritorio en la interfaz de usuario táctil (AEM 6.3)
* Compatibilidad mejorada con las últimas versiones de SO
* Correcciones informadas por el cliente

### Mejoras disponibles desde la aplicación de escritorio de AEM 1.3 {#Enhancements-Available-Since-AEM-Desktop-App-13}

* Mayor eficiencia. Los usuarios pasan menos tiempo esperando a que se completen las operaciones de red.
* Se ha mejorado la integración del Buscador, que proporciona más estabilidad y acceso a funciones como miniaturas.
* Mejoras en el almacenamiento en caché y el rendimiento.
* Mejor compatibilidad para guardar directamente desde aplicaciones de escritorio (PS, ID, AI, etc.).
* Se ha mejorado la integración con Mac OS (el protocolo de unidad de red local cambió de WebDAV a SMB1 más estable).
* La aplicación de escritorio se conecta con el servidor de AEM mediante el protocolo HTTP RESTful nativo de AEM.
* Los archivos se guardan localmente primero y luego se cargan de nuevo en AEM en segundo plano después de un tiempo predefinido (30 segundos). Esto reduce el tiempo para guardar archivos.
* Mejor gestión de las aplicaciones de escritorio que utilizan operaciones de archivo intermedias para guardar un archivo (guardado parcial y archivos temporales), lo que permite que la línea de tiempo de AEM Asset muestre la información correcta de la versión y carga de recursos.
* Cuadro de diálogo proporcionado para realizar un seguimiento del estado de las tareas de carga en segundo plano.

## Lista de cambios {#list-of-changes}

### Punto de montaje en Mac {#mount-point-on-mac}

Desde MacOS 10.12 (Sierra), Apple ha cambiado los permisos de la carpeta /Volúmenes que se usan para montar unidades de red y dispositivos de red a más restrictivos. Crear un nuevo punto de montaje requiere derechos administrativos. Este problema se corrigió en MacOS 10.12.5.

Como la aplicación de escritorio de AEM debe ejecutarse para los usuarios que no tengan derechos de administrador en el equipo local, el punto de montaje del repositorio de AEM Assets se cambió en 1.4 y 1.5 a una subcarpeta DAM en la carpeta local del usuario en MacOS (CQ-104183).

Dado que la carpeta /Volúmenes ya no requiere derechos administrativos, este cambio se ha revertido en 1.5.1. Esto también permite compartir documentos de InDesign que han colocado AEM assets entre usuarios de Mac OS.

### Cambio de protocolo (desde v1.3) {#protocol-change-since}

* Mac OS X:
   * El protocolo de unidad de red local para la integración de escritorio de OS X cambió a SMB1 desde WebDAV.
   * El repositorio de AEM montado con la aplicación de escritorio será visible como una unidad de red &quot;smb&quot; en Finder, en lugar de como una unidad WebDAV.
* Windows:
   * El protocolo de unidad de red local para las integraciones de escritorio de Windows permanece; AEM se montará como un recurso compartido WebDAV.
* Para ambas plataformas (Windows y Mac):
   * El protocolo para acceder o descargar recursos y cargar cambios en AEM se ha cambiado al protocolo AEM nativo, que es un protocolo RESTful basado en HTTP. Proporciona un mayor control sobre las operaciones de red y es más compatible con la infraestructura de red.

>[!NOTE]
>
>En Mac OS X, el cambio del protocolo de unidad de red local de WebDAV a SMB1 da como resultado una ruta local diferente al mismo recurso en el repositorio. Esto puede afectar a los vínculos a archivos colocados en las aplicaciones de Adobe Creative Cloud mediante el comando &quot;Colocar&quot;. Consulte [Usar la aplicación de escritorio de AEM](use-app-v1.md) para obtener más información.

### Administración de archivos (desde 1.3) {#file-handling-since}

* Las carpetas se actualizan automáticamente después de un retraso predefinido (actualmente de 30 segundos).
* Los archivos extraídos por otros usuarios están marcados como de solo lectura.
* Los archivos se guardan en una ubicación de unidad de red montada mediante la aplicación de escritorio en dos fases.
* En la primera fase, un archivo se guarda localmente. De este modo, el usuario que guarda el archivo no tiene que esperar hasta que se transfiera completamente a AEM y puede reanudar el trabajo en cuanto se guarde el archivo.
* En la segunda fase, la aplicación de escritorio carga un archivo actualizado en el servidor de AEM después de un retraso predefinido (por ejemplo, 30 segundos ). Esta operación se produce en segundo plano. Utilice la opción **Mostrar estado de sincronización de archivos de fondo** para ver el estado de la operación de carga.

## Avisos importantes {#important-notices}

**Carga de carpetas.** Se recomienda utilizar la nueva función de carga de carpetas para cargar carpetas jerárquicas más grandes en AEM, en lugar de usar una función de copiar/arrastrar y soltar en un repositorio de AEM montado desde el nivel de Buscador/Explorador. Al utilizar la función de carga de carpetas, la aplicación de escritorio se comunica con AEM directamente y, por lo tanto, tiene un control mucho mejor sobre el proceso general.

**Mantenga la sesión de AEM disponible.** La aplicación de escritorio de AEM depende de una sesión abierta al servidor de AEM Assets para garantizar el correcto funcionamiento. Para los usuarios que trabajan con la aplicación de escritorio todos los días, se recomienda desmontar AEM Assets al final del día para forzar el cierre de sesión y, a continuación, &quot;Montar AEM Assets&quot; por la mañana para garantizar que hayan iniciado sesión y que el recurso compartido de red esté en funcionamiento.

**Desactive &quot;Vista previa de iconos&quot; en Finder.** Para navegar con rendimiento en carpetas grandes con Finder, especialmente con mala conectividad de red, asegúrese de que tanto &quot;Icono&quot; como &quot;Vista previa del Icono&quot; estén desactivados. De lo contrario, Finder empezará a descargar cada recurso en una carpeta para generar una vista previa pequeña, lo que puede provocar un rendimiento deficiente y una utilización de ancho de banda elevado (CQ-4219779)

* En Finder, vaya a la carpeta de red compartida de AEM Assets
* Haga clic con el botón derecho en el punto de montaje DAM
* Seleccionar Mostrar opciones de vista
* Anule la selección de &quot;Mostrar vista previa del icono&quot;
* Haga clic en Usar como predeterminados

**Limpie la caché al conectarse a un nuevo servidor AEM.** Si la aplicación de escritorio se conecta a otro servidor de AEM con la misma dirección URL, la caché no se borra automáticamente. Borre la caché manualmente para garantizar las operaciones correctas. Tenga en cuenta que esto generalmente sucede en las pruebas, cuando las instalaciones de AEM se pueden reemplazar mientras se ejecutan en la misma dirección URL (CQ-4216982)

**Utilice certificados SSL firmados por CA.** Tenga en cuenta que la aplicación de escritorio de AEM no admite certificados SSL autofirmados al conectarse a AEM mediante una conexión segura HTTPS. Se requiere un certificado firmado por CA en el servidor para estas conexiones. (CQ-87941)

## Problemas conocidos {#known-issues}

* General:
   * Las direcciones URL del servidor son necesarias para apuntar al servidor sin una ruta (p. ej. `http://server`, `https://server`, `http://server:port` o `https://server:port`). Las rutas de contexto y las subcarpetas que no sean /content/dam no son compatibles (CQ-89343, CQ-87272)
* Nombres de archivos/localización:
   * Los nombres de archivos y carpetas con caracteres reservados no se gestionan correctamente. Asegúrese de utilizar nombres de archivo y carpeta que se ajusten a los requisitos de AEM (CQ-93361, CQ-93308, CQ-89276, CQ-4217183)
   * Algunas aplicaciones como Adobe Illustrator pueden crear archivos con nombres no compatibles con AEM. Por ejemplo, agregar `Converted` después de convertir un archivo, lo que impide que se cargue (CQ-4216985)
   * Los activos con nombres internacionales pueden aparecer y desaparecer cada pocos segundos
* Registro de entrada y salida:
   * Un recurso extraído por un usuario no se puede abrir para otro usuario, ya sea mediante la acción Abrir de la IU táctil o directamente en el escritorio. Algunas aplicaciones pueden reportarlo como bloqueadas, pero también como dañadas o incluso bloqueadas al intentar abrir. (CQ-4199234)
   * Cambiar archivos simultáneamente por varios usuarios puede causar que se pierdan algunas modificaciones. La solución es utilizar la funcionalidad de protección y desprotección para evitar que varios usuarios cambien el mismo archivo (CQ-97035)
   * Algunas aplicaciones no admiten el indicador de solo lectura correctamente, lo que permite al usuario guardar un archivo que ha sido extraído por otro usuario. El archivo modificado no se transfiere hasta que el otro usuario compruebe en el archivo. Ambas modificaciones están disponibles en AEM como versiones diferentes del recurso (CQ-89551, CQ-87572, CQ-89615)
   * El estado de retirada y de solo lectura se informa de forma independiente en Finder. Esto resulta en dos iconos de bloqueo cuando un usuario cierra la compra de un recurso (CQ-89507)
* Integración del Buscador:
   * Al arrastrar y soltar archivos de gran tamaño, es posible que se agote el tiempo de espera del Buscador mientras los archivos se transfieren en segundo plano. Esto resulta en un `Error - 36`. La solución es arrastrar, soltar o volver a abrir el recurso (CQ-4219628)
   * La recarga manual de carpetas no siempre funciona. Solución alternativa:  wait   30 segundos para que la carpeta se actualice automáticamente. (CQ-97389)
   * Más información de recursos... está limitada a selecciones de archivos únicos (CQ-89542, CQ-87656)
   * Abrir en AEM Assets... está limitado a selecciones de un solo archivo y carpeta (CQ-83382)
   * Error al cambiar el nombre de recursos que no tienen extensión (CQ-4218971)
* Funcionalidad de copiar/pegar: Pegar está disponible cuando no se ha copiado ningún recurso en el portapapeles
* Windows:
   * Los archivos con flujos de datos alternativos (ADS) solo son totalmente compatibles con NTFS. Si se copian estos archivos en el recurso compartido WebDAV proporcionado por la aplicación de escritorio, se mostrará un cuadro de diálogo de precaución en el que se avisará al usuario de que el archivo tiene propiedades que no se pueden copiar en la nueva ubicación. Esto suele estar bien, ya que las propiedades solo son relevantes para una aplicación en particular en el escritorio del usuario y no tienen nada que ver con el contenido real del archivo (CQ-103770) (Win)
   * la aplicación de escritorio en Windows debe instalarla el usuario que la va a usar (CQ-4216389) (win)
   * La aplicación se puede bloquear al seleccionar la opción [!UICONTROL Retry] en una carga fallida en determinadas circunstancias después de haber reanudado la carga por lotes cuando se desconecta (CQ-4251884) (Win)

## Recursos útiles {#helpful-resources}

* [Documentación de AEM](https://experienceleague.adobe.com/docs/)
* [Uso de la aplicación de escritorio de AEM v1.x](use-app-v1.md)
* [Prácticas recomendadas de la aplicación de escritorio v1.x de AEM](best-practices-for-v1.md)

## Matriz de compatibilidad y requisitos previos {#compatibilitymatrix}

La aplicación de escritorio de AEM funciona con varias versiones de AEM. Consulte la matriz de compatibilidad para las versiones compatibles.

| Versión | Revisión | Fecha de la versión | Compatibilidad |
|--- |--- |--- |--- |
| 1,10 | 1.10.0.3 (Mac y Win) | 31 de agosto de 2018 | AEM 6.5; AEM 6.4 SP1; AEM 6.3 SP2; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
| 1,9 | 1.9.1.1 (Mac y Win) | 21 de junio de 2018 | AEM 6.4; AEM 6.3 SP1; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
| 1,8 | 1.8.1.0 (Mac y Win) | 28 de marzo de 2018 | AEM 6.4; AEM 6.3 SP1; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
| 1,7 | 1.7.0.3 (Mac y Win) | 10 de enero de 2018 | AEM 6.3 SP1; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
