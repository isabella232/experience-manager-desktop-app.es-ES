---
title: Notas de la versión de la aplicación de escritorio de AEM para la versión 1.x
description: Detalles de la versión, mejoras, nuevas funciones, compatibilidad y vínculos de descarga para la versión 1.x de la aplicación de escritorio de AEM.
uuid: b783c3f8-aa1e-4c05-b687-5894909769f5
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: 3052549b-fe75-44fb-a55e-5cc612868f54
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b92e47456f9e16c24eac43d1c5fef9a582f143b5

---


# Notas de la versión de la aplicación de escritorio de AEM v1.x {#aem-desktop-app-release-notes}

Para la versión v1.x de la aplicación de escritorio, los vínculos de descarga y la información de compatibilidad de AEM son los siguientes.

| Productos | Aplicación de escritorio de Adobe Experience Manager (AEM) |
|---------------|--------------------------------------------------------------------|
| Versión | 1.10 (1.10.0.6 en Mac y 1.10.0.3 en Windows) |
| Tipo | Versión menor |
| Fecha | 1.10.0.6 (Mac): 15 de abril de 2020; 1.10.0.3 (Win): 31 de agosto de 2018 |
| Direcciones URL de descarga | [Mac OS X 64 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-osx-1.10.0.6.dmg); [Windows de 32 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win32-1.10.0.3.exe); [Windows de 64 bits](https://download.macromedia.com/aem-assets-companion-app/aem-desktop-win64-1.10.0.3.exe) |
| Compatibilidad | AEM 6.5.x; AEM 6.4.x; AEM 6.3 SP2; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |

>[!NOTE]
>
>No se aplica el límite de tamaño de caché. Cuando la aplicación de escritorio inicio, el tamaño de la caché se calcula una vez y se muestra una notificación si el tamaño está cerca del límite predefinido.

## Requisitos y requisitos previos del sistema {#system-requirements-and-prerequisites}

AEM Desktop es compatible con los siguientes sistemas operativos:

* Mac OS X 10.10 o posterior, con las últimas correcciones de errores.
* Windows 7 y Windows 10 con los paquetes de servicios y las correcciones de errores más recientes.

Adobe recomienda encarecidamente utilizar la versión más reciente de la aplicación de escritorio de AEM para aprovechar la funcionalidad más reciente, las correcciones de errores más recientes y el mejor rendimiento posible.

La versión de la aplicación de escritorio de AEM que tiene previsto instalar en su equipo local requiere una versión específica del servidor de AEM o componentes adicionales del servidor (paquetes de servicios, correcciones rápidas o paquetes de funciones). Asegúrese de que el servidor AEM está configurado correctamente antes de conectarse a él por primera vez. Si necesita ayuda, póngase en contacto con el administrador de AEM.

Consulte la matriz [de compatibilidad](#compatibilitymatrix) detallada al final de este documento para evaluar los requisitos previos de la configuración.

## What&#39;s New in AEM desktop app 1.10 {#what-s-new-in-aem-desktop-app}

La aplicación de escritorio AEM 1.10 se centra en mejorar la experiencia del usuario en cuanto a las cargas grandes, la información sobre las operaciones en segundo plano y la experiencia optimizada al abrir recursos con archivos vinculados (como InDesign).

>[!NOTE]
>
>Si utiliza macOS 10.15.4 o posterior, utilice al menos la versión 1.10.0.6 de la aplicación. Esta versión de parche cumple con los requisitos [de notarización de](https://developer.apple.com/news/?id=04102019a)Apple.

**Edición/salida** local: Las cargas automáticas de los cambios guardados en los recursos se pueden desactivar en la ventana de estado. De este modo, el usuario puede seguir trabajando en los archivos y guardando los cambios y, cuando esté listo, decidir cargar todos los cambios.

**Ventana** Estado del recurso simplificado: La ventana de estado se ha simplificado * La ficha Cargas ahora muestra los recursos individuales, así como las cargas masivas o de carpetas. Se ha eliminado la ficha Cargas masivas anterior.

**Icono de aplicación para indicar cargas** masivas: El icono de la aplicación indicará que se está realizando una carga masiva mostrando una superposición de &quot;transferencia&quot;.

**Notificaciones para conflictos** de actualización: Cuando la aplicación detecta un conflicto al intentar actualizar un recurso, muestra una notificación para que el usuario pueda revisarla sin necesidad de supervisar la ventana de estado. Cuando la aplicación inicio, comprobará si hay todos los conflictos para que el usuario pueda resolverlos.

**Mejor manejo de las pérdidas** de conexión: Las cargas masivas se pausarán si se produce una pérdida de conexión y el usuario podrá reanudarlas más tarde. Hay disponible un botón Reintentar para reintentar una carga fallida de un archivo individual.

## Instrucciones de instalación {#installation-instructions}

Para obtener instrucciones detalladas, consulte [Instalación y configuración de la aplicación](install-configure-app-v1.md)de escritorio AEM.

## Mejoras en las versiones anteriores {#enhancements-in-the-previous-versions}

Esta versión amplía y reemplaza las versiones anteriores de la aplicación de escritorio de Experience Manager, que ofrece las siguientes mejoras clave:

* **Versión 1.9/1.9.1**: cargas reanudables, ventana de estado mejorada, iconos de la aplicación que indican el estado de la aplicación/conexión, recuperación previa de recursos vinculados para archivos de InDesign
* **Versión 1.8**: mejor control del tamaño de caché para el usuario, mejor experiencia de inicio de sesión para SAML/SSO en Windows, compatibilidad con proxy de red .pac en Mac y problemas notificados por el cliente.
* **Versión 1.7**: mejoras en la estabilidad y la lógica de almacenamiento en caché, mejor compatibilidad con proxy de red y capacidad para limpiar archivos internos después de la desinstalación.
* **Versión 1.6**: mejoras en el proceso de inicio de sesión para diversas configuraciones de seguridad de AEM y estabilidad y rendimiento de la aplicación.
* **Versión 1.5**: estabilidad y resiliencia de las aplicaciones frente a diversos problemas de red, mejor soporte.
* **Versión 1.4**: la capacidad de cargar carpetas jerárquicas en segundo plano con la supervisión del progreso.
* **Versión 1.3**: mejoras de rendimiento y estabilidad para acceder a los archivos y guardar los cambios en AEM, especialmente desde las aplicaciones de escritorio de Creative Cloud, como InDesign, Illustrator o Photoshop. Su objetivo era ofrecer a los usuarios una experiencia de escritorio más local al trabajar con archivos, mientras se gestionan simultáneamente las operaciones de transferencia de datos de red en segundo plano.

### Mejoras disponibles desde la aplicación de escritorio AEM 1.9 {#Enhancements-Available-Since-AEM-Desktop-App-19x}

La aplicación de escritorio 1.9.1 de Adobe Experience Manager (AEM) ha sido una versión de parche que soluciona algunos problemas clave de los clientes relacionados con la retirada de recursos y la copia de archivos del recurso compartido de red en un directorio local.

* Los recursos desprotegidos por un usuario no deben estar disponibles para su modificación por otros usuarios (CQ-4246009)
* Se puede copiar de una carpeta asignada a una carpeta local cuando la carpeta de usuario está en una partición de disco independiente (CQ-4243978)

La aplicación de escritorio AEM 1.9 se centra en mejorar la experiencia del usuario en cuanto a las cargas grandes, la información sobre las operaciones en segundo plano y la experiencia optimizada al abrir recursos con archivos vinculados (como InDesign).

**Cargas**reanudables Para cargas, especialmente alrededor de archivos grandes, existe una opción para pausarlas o reanudarlas en la nueva ventana Estado del recurso.
**Ventana**Estado de recurso mejoradaUna ventana de estado de recurso mejorada proporciona información sobre los recursos que:
Cambios

* Muestra los cambios en cola actualmente
* Muestra las cargas en curso, incluida una barra de progreso, velocidad de transferencia, tamaño total de archivo y tamaño transferidos hasta ahora
* Cargas completadas mostradas con el total transferido y la tasa final
* Se muestran las cargas fallidas junto con un mensaje de error y la información de transferencia, si está disponible
* Las cargas con errores 3 veces mostrarán un mensaje de error
* Archivos en conflicto mostrados con un icono en el que el usuario puede hacer clic. Al hacer clic en el icono se muestra un cuadro de diálogo con una explicación y dos opciones:
   * &quot;Keep Mine&quot;: carga inmediatamente el archivo en el servidor
   * &quot;Sobrescribir mío&quot;: elimina inmediatamente el archivo local y descarga una nueva copia del servidor

Descargas

* Muestra las descargas en curso, incluyendo una tasa de transferencia y un tamaño transferidos hasta ahora
* Las descargas completadas se muestran con el total transferido, la tasa final y un icono que abrirá el archivo cuando se haga clic en él (solo disponible para archivos individuales)
* Las descargas fallidas se muestran con un mensaje de error y la información de transferencia, si está disponible
* El pie de página muestra el número total de archivos descargados y la tasa media de transferencia.
* Si un usuario decide abrir o editar varios archivos desde la interfaz de usuario web de AEM Assets, se agruparán, por ejemplo, como &quot;myasset.jpeg y 4 archivos más&quot;
* Al descargar Documentos de InDesign, incluidos los recursos vinculados almacenados en Recursos AEM, la aplicación de escritorio descargará primero todos los recursos vinculados antes de abrir el Documento de InDesign e indicará la descarga de recursos vinculados, por ejemplo: (5 de 24)

Cargas masivas: Al cargar jerarquías de carpetas grandes mediante Crear > Cargar carpeta en la interfaz de usuario web de AEM o al copiar y seleccionar &quot;Pegar recursos&quot; en Finder/Explorer en el menú contextual de la aplicación de escritorio, se activará el uso de este cuadro de diálogo:

* Muestra las cargas en curso, incluida una barra de progreso y el nombre del archivo que se está transfiriendo.
* Las cargas en curso incluyen un icono que cancelará la carga cuando se haga clic en ellas. La transferencia se detendrá cuando se complete el archivo que se está transfiriendo.
* Los procesos de transferencia fallidos se muestran con un mensaje de error (sólo si falla toda la transferencia)
* Si un archivo individual no se transfiere, se mostrará en la ficha como un error. De lo contrario, los archivos individuales no se mostrarán en la ficha * solo una entrada para toda la carga.

**Iconos para indicar el estado de las operaciones** en segundo plano El icono de la aplicación indicará el estado de las operaciones en segundo plano para proporcionar una mejor indicación visual a los usuarios. Por ejemplo, cuando la aplicación no está conectada a AEM, el icono aparecerá atenuado, cuando haya una carga activa, se mostrará una superposición &quot;sinc&quot;, etc.

**Recuperación previa de recursos**vinculados Para mejorar la experiencia del usuario al trabajar con documentos de InDesign que incluyen recursos vinculados almacenados en AEM, la aplicación de escritorio intentará recuperar previamente estos archivos vinculados en la caché local antes de que se descargue y abra el documento de InDesign. De este modo, el usuario tendrá los archivos vinculados disponibles localmente y no tendrá que esperar más cuando acceda a ellos en InDesign (en el panel Vínculos).
Tenga en cuenta que la recuperación previa solo funciona si AEM reconoce los vínculos en el servidor. Un recurso con vínculos reconocidos tendrá una lista de &quot;Referencias&quot; en la vista Propiedades del recurso de InDesign.

### Mejoras disponibles desde la aplicación de escritorio AEM 1.8.x {#enhancements-available-since-aem-desktop-app-18x}

La aplicación de escritorio AEM 1.8.1 versión de seguimiento rápido ha añadido mejoras al abrir varios archivos a la vez desde la interfaz de usuario de AEM a la versión 1.8 (CQ-4237747, CQ-4238780). Las mejoras en la aplicación de escritorio AEM 1.8 son:

* Almacenamiento en caché: nueva interfaz de usuario para la administración de la caché de la aplicación de escritorio de AEM (CQ-4208690), que incluye:
   * Tamaño de caché actual de vista
   * definir el tamaño máximo de caché antes de enviar una notificación
   * El tamaño de caché se comprueba únicamente en el inicio de la aplicación de escritorio y se muestra una notificación si está alcanzando el límite configurado
   * el botón de borrar caché ya está disponible en la nueva interfaz de usuario
* Inicio de sesión: (Win) Se ha corregido el inicio de sesión en la instancia de AEM configurada para utilizar SAML y SSL (CQ-4216353)
* Red:
   * cuando caduca una sesión de AEM, ahora se notifica al usuario y puede hacer clic en la notificación para volver a iniciar sesión (CQ-4202028)
   * (Mac) Añada la compatibilidad con la conexión a AEM mediante la configuración proxy .pac (CQ-4233430)
   * (Win) corrige problemas con el cuadro de diálogo Avanzadas: URL de inicio de sesión (CQ-4236061)
* Corrección de errores:
   * Cuadro de diálogo Más información de recursos: a veces la barra de acciones no estaba visible (CQ-4208540)
   * (Win) Ahora, el archivo se puede sincronizar después de revertir a una versión anterior desde la interfaz de usuario de AEM Assets (CQ-4216411)

### Mejoras disponibles desde la aplicación de escritorio AEM 1.7 {#Enhancements-Available-Since-AEM-Desktop-App-17}

* Estabilidad:
   * Se ha mejorado la estabilidad cuando la aplicación de escritorio de AEM se conecta a un servidor AEM sobrecargado (CQ-4224803)
   * Se ha mejorado la estabilidad cuando se solicitan muchos archivos (CQ-4224212)
   * Actualización de recursos mejorada con comprobación adicional (CQ-4228291)
* Almacenamiento en caché:
   * Corregir errores de disco y abrir problemas al abrir archivos en Photoshop, InDesign, Finder (CQ-4223993, CQ-4217603, CQ-4223717)
   * Se ha mejorado el almacenamiento en caché para evitar binarios de tamaño cero (CQ-4216599)
* Inicio de sesión: Permitir la conexión con el protocolo de SSL estricto desactivado para configuraciones especiales (como certificados emitidos localmente) (CQ-4223949)
* Redes: Compatibilidad mejorada para la conexión mediante proxy de red (CQ-4223477, CQ-4221280, CQ-4206854)
* Instalación y desinstalación:
   * (Win) Desinstalación del limpiador (CQ-4220906)
   * [El instalador de Windows de 32 bits] no puede intentar instalar Microsoft .NET Framework v. 4.5 (CQ-4218084)
   * (Mac) Secuencia de comandos manual para quitar archivos de aplicaciones de escritorio por completo (CQ-4216489)

>[!NOTE]
>
>Los problemas encontrados en las cargas beta 1.7 de la aplicación de escritorio de AEM (que no estaban presentes en la versión 1.6 no se incluyen en las notas de la versión).

### Mejoras disponibles desde la aplicación de escritorio AEM 1.6 {#Enhancements-Available-Since-AEM-Desktop-App-16}

* Documentación: Nuevas [prácticas recomendadas para la documentación de la aplicación](https://helpx.adobe.com/experience-manager/6-3/assets/using/aem-desktop-app-best-practices.html) v1.x.
* Se ha mejorado el proceso de inicio de sesión en AEM:
   * Mejore el manejo de SAML * relájese las reglas (CQ-4202781).
   * Añada la capacidad de configurar direcciones URL de inicio de sesión independientes en Preferencias (CQ-4214052, CQ-4214051).
* Facilidad de uso: Notificar al usuario cuando aún se esté descargando un recurso para recursos más grandes (CQ-4216284).
* Redes:
   * Caché DNS (CQ-4210176).
   * Conexión de soporte mediante proxy en Windows (CQ-4206854).
* Almacenamiento en caché y acceso al recurso compartido de red en Finder/Explorer:
   * El icono Bloquear ahora está visible para los recursos extraídos en Windows 10 (CQ-90957).
   * El contenido de la carpeta puede desaparecer o reaparecer en el recurso compartido de red (CQ-4209160, CQ-4210180).
   * Error al cargar el archivo debido a un conflicto registrado en el estado de la cola de carga (CQ-4215727).
   * Al abrir varios archivos desde la carpeta de la aplicación de escritorio en PS, es posible que se muestren mensajes truncados o incompletos (CQ-4216276).
* Correcciones en estabilidad y rendimiento:
   * Se ha mejorado el rendimiento al explorar carpetas con muchos recursos (CQ-4214933).
   * la aplicación de escritorio 1.5 puede ralentizar el funcionamiento del equipo de escritorio con el tiempo (CQ-4209159).
   * La función Mostrar estado de cola solo funciona para el usuario que instaló la aplicación (CQ-4212199).
   * (Windows) Asegúrese de que el instalador de 32 bits no contenga código de 64 bits (CQ-4217406).
* Problemas seleccionados encontrados y corregidos en la beta 1.6:
   * Uso elevado de CPU (CQ-4218070).
   * Error al arrastrar y soltar archivos al cargar en AEM (CQ-4217006).

### Mejoras disponibles desde la aplicación de escritorio AEM 1.5 {#Enhancements-Available-Since-AEM-Desktop-App-15}

**Versión 1.5.1.5 para Mac OS X:** La versión 1.5.1.5 ofrece las siguientes ventajas:

* Nuevas funciones y mejoras: Añada la funcionalidad Copiar/Pegar en la integración de Finder para permitir la transferencia directa de Desktop a AEM (CQ-4208158)
* Correcciones de errores:
   * Se ha corregido un problema 43 que se producía a veces durante el cambio de nombre de recursos (CQ-4207900)
   * Al volver a una versión anterior desde la línea de tiempo en AEM, el recurso no se actualiza en Finder (CQ-4205194)
   * la aplicación de escritorio se bloquea al explorar directorios anidados de gran tamaño (CQ-4208539)
   * el punto de montaje de la aplicación de escritorio es ahora /Volumes/DAM, por lo que es coherente para todos los usuarios (CQ-4208159)
   * Al colocar el archivo en InDesign por primera vez se inicia una advertencia de actualización (CQ-4207454)

Nota sobre advertencias de vínculo: Las aplicaciones de Creative Cloud (como InDesign) toman una &quot;instantánea&quot; de la hora de la última modificación del elemento en el momento en que se coloca. Si esa fecha cambia más adelante, la aplicación Adobe Creative Cloud informará de que los vínculos no están actualizados. Esto se informa de dos maneras:

* Cuando se inicie la aplicación de Adobe Creative Cloud, se mostrará un cuadro de diálogo en el que se informará al usuario de que los recursos vinculados no están actualizados y se le pedirá que tome medidas.
* Si la aplicación Adobe Creative Cloud ya se está ejecutando, mostrará un icono de advertencia triangular amarillo en el recurso vinculado.

Este comportamiento es el mismo para los recursos en el disco local y los recursos en un directorio montado en AEM Desktop, con las siguientes excepciones:

* Si otro usuario modifica un recurso colocado, el icono de advertencia aparecerá la primera vez que otros usuarios abran un documento que contenga el recurso colocado. Esto solo ocurrirá si el recurso colocado ya se ha almacenado en la caché local.
* Si un usuario modifica un recurso colocado a través del directorio montado de AEM Desktop y, a continuación, borra su caché local, el recurso colocado se registrará como obsoleto.

Se esperan ambos casos y son efectos secundarios de la arquitectura de &quot;sincronización retrasada&quot; de AEM Desktop.

**Versión 1.5.0.x para Mac OS X y Windows:** Esta versión de la aplicación de escritorio de AEM ofrece las siguientes ventajas:

* Mayor estabilidad y resiliencia frente a problemas de red
   * Asignación más estable de carpetas de Recursos AEM (CQ-103276, CQ-4204669, CQ-4203957)
   * Mejor manejo de archivos en caché (CQ-4204336, CQ-4206263)
   * Se ha mejorado el manejo de la descarga y carga de archivos de gran tamaño de más de 2 GB (CQ-4206438)
   * Se corrigió el error 36 al mover o cambiar el nombre de un número mayor de archivos en Finder (CQ-4204640)
* Optimizaciones en la comunicación en red con AEM Server (CQ-4204974, CQ-100903)
* Se ha mejorado la fiabilidad de abrir, colocar y guardar recursos de AEM en aplicaciones de Creative Cloud (CQ-4203968, CQ-4205511, CQ-103543, CQ-4207141, CQ-90980)
* Compatibilidad mejorada: opción para borrar la caché (CQ-4202541), fácil acceso a los registros (CQ-4202340, CQ-4204673)
* Otras correcciones:
   * Mejor compatibilidad con recursos y carpetas con caracteres japoneses en la configuración de nombre/idioma no inglés (CQ-4195433, CQ-4205793, CQ-4199446)
   * Mejor manejo del inicio de sesión con SSL (CQ-4200217)
   * Montaje compartido más fiable (CQ-4200793)
   * Varias mejoras en la estabilidad (CQ-4207539, CQ-4200378)
   * Mejor gestión de la URL de AEM Assets en Preferencias (CQ-97388)

### Mejoras disponibles desde la aplicación de escritorio AEM 1.4 {#Enhancements-Available-Since-AEM-Desktop-App-14}

* Carga simplificada de carpetas jerárquicas mediante la nueva acción Crear > Cargar carpeta en la IU táctil
   * La acción inicia una operación de carga de carpetas realizada por la aplicación de escritorio
   * La aplicación de escritorio atraviesa la jerarquía de carpetas dada en el escritorio en segundo plano y carga los archivos en Recursos AEM
   * El usuario puede supervisar el progreso en la nueva ventana Estado de la cola de carga con barra de progreso para las operaciones en curso
   * El estado de la cola de carga también proporciona mejor información de resolución de problemas (por ejemplo, sin conexión al servidor)
* Nueva acción Editar en la IU táctil, que combina las operaciones Desproteger y Abrir en una sola
* Agrupación optimizada de acciones relacionadas con el escritorio en la IU táctil (AEM 6.3)
* Compatibilidad mejorada con las últimas versiones del sistema operativo
* Correcciones informadas por el cliente

### Mejoras disponibles desde la aplicación de escritorio AEM 1.3 {#Enhancements-Available-Since-AEM-Desktop-App-13}

* Mayor eficiencia. Los usuarios invierten menos tiempo esperando a que se completen las operaciones de red.
* Se mejoró la integración de Finder, que proporciona más estabilidad y acceso a funciones como, por ejemplo, miniaturas.
* Mejoras en el almacenamiento en caché y el rendimiento.
* Mejor compatibilidad para guardar directamente desde aplicaciones de escritorio (PS, ID, AI, etc.).
* Integración mejorada con Mac OS (el protocolo de unidad de red local cambió de WebDAV a SMB1 más estable).
* La aplicación de escritorio se conecta con el servidor AEM mediante el protocolo HTTP RESTful nativo de AEM.
* Los archivos se guardan localmente primero y luego se cargan de nuevo en AEM en segundo plano después de un tiempo predefinido (30 segundos). Esto reduce el tiempo para guardar archivos.
* Mejor gestión de las aplicaciones de escritorio que utilizan operaciones de archivos intermedios para guardar un archivo (almacenamiento parcial y archivos temporales), lo que permite que la línea de tiempo de Recursos AEM muestre la información correcta de la versión y la carga de recursos.
* Cuadro de diálogo proporcionado para rastrear el estado de las tareas de carga en segundo plano.

## Lista de cambios {#list-of-changes}

### Punto de montaje en Mac {#mount-point-on-mac}

Desde MacOS 10.12 (Sierra), Apple ha cambiado los permisos de la carpeta /Volumes utilizados para montar unidades de red y dispositivos a otros más restrictivos. La creación de un nuevo punto de montaje requería derechos administrativos. Este problema se ha corregido en MacOS 10.12.5.

Dado que la aplicación de escritorio de AEM debería ejecutarse para los usuarios que no tienen derechos de administrador en el equipo local, el punto de montaje del repositorio de AEM Assets se cambió en 1.4 y 1.5 a una subcarpeta DAM en la carpeta local del usuario en MacOS (CQ-104183).

Dado que la carpeta /Volumes ya no requiere derechos administrativos, este cambio se ha revertido en 1.5.1. Esto también permite compartir documentos de InDesign que han colocado recursos de AEM entre usuarios de MacOS.

### Cambio de protocolo (desde v1.3) {#protocol-change-since}

* Mac OS X:
   * El protocolo de unidad de red local para la integración de escritorio de OS X cambió a SMB1 desde WebDAV.
   * El repositorio de AEM montado con la aplicación de escritorio será visible como una unidad de red &quot;smb&quot; en Finder, en lugar de una unidad WebDAV.
* Windows:
   * El protocolo de unidad de red local para las integraciones de escritorio de Windows permanece; AEM se montará como un recurso compartido WebDAV.
* Para ambas plataformas (Windows y Mac):
   * El protocolo para acceder/descargar recursos y cargar cambios en AEM se ha cambiado al protocolo AEM nativo, que es un protocolo RESTful basado en HTTP. Proporciona bueno control sobre las operaciones de red y es más compatible con la infraestructura de red.

>[!NOTE]
>
>En Mac OS X, el cambio del protocolo de unidad de red local de WebDAV a SMB1 da como resultado una ruta local diferente al mismo recurso en el repositorio. Esto podría afectar a los vínculos a archivos colocados en aplicaciones de Adobe Creative Cloud mediante el comando &quot;Colocar&quot;. Consulte la sección [Uso de la aplicación](use-app-v1.md) AEM Desktop para obtener más información.

### Gestión de archivos (desde 1.3) {#file-handling-since}

* Las carpetas se actualizan automáticamente tras un retraso predefinido (actualmente de 30 segundos).
* Los archivos extraídos por otros usuarios se marcan como de solo lectura.
* Los archivos se guardan en una ubicación de unidad de red montada mediante la aplicación de escritorio en dos fases.
* En la primera fase, un archivo se guarda localmente. De este modo, el usuario que guarda el archivo no tendrá que esperar hasta que se transfiera completamente a AEM y podrá reanudar el trabajo en cuanto se guarde el archivo.
* En la segunda fase, la aplicación de escritorio carga un archivo actualizado en el servidor AEM tras un retraso predefinido (por ejemplo, 30 segundos). Esta operación se produce en segundo plano. Utilice la opción **Mostrar estado** de sincronización de archivos de fondo para la vista del estado de la operación de carga.

## Avisos importantes {#important-notices}

**Carga de carpetas.** Se recomienda utilizar la nueva función de carga de carpetas para cargar carpetas jerárquicas más grandes en AEM, en lugar de utilizar la función de copiar/arrastrar y soltar en un repositorio AEM montado desde el nivel Finder/Explorer. Al utilizar la función de carga de carpetas, la aplicación de escritorio se comunica directamente con AEM y, por tanto, tiene un control mucho mayor sobre el proceso en general.

**Mantenga la sesión de AEM disponible.** La aplicación de escritorio de AEM depende de una sesión abierta al servidor de AEM Assets para garantizar el correcto funcionamiento. Para los usuarios que trabajan con aplicaciones de escritorio todos los días, se recomienda desmontar Recursos AEM al final del día para forzar la salida de la sesión y, a continuación, &quot;Montar Recursos AEM&quot; por la mañana para garantizar que inician sesión y que el recurso compartido de red está operativo.

**Desactive &quot;Previsualización de iconos&quot; en Finder.** Para navegar con gran rendimiento por las carpetas grandes con Finder, especialmente con conectividad de red deficiente, asegúrese de que tanto &quot;Icon&quot; como &quot;Icon Previsualización&quot; están desactivados. De lo contrario, Finder inicio la descarga de cada recurso en una carpeta para generar una pequeña previsualización, lo que puede conducir a un bajo rendimiento y a una alta utilización del ancho de banda (CQ-4219779)

* Para buscar, vaya a la carpeta de red compartida de Recursos AEM
* Haga clic con el botón derecho en el punto de montaje DAM
* Seleccionar Mostrar opciones de Vista
* Anule la selección de &quot;Mostrar previsualización de icono&quot;
* Haga clic en &quot;Usar como predeterminados&quot;

**Limpie la caché al conectarse a un nuevo servidor AEM.** Si la aplicación de escritorio se conecta a otro servidor AEM con la misma URL, la caché no se borra automáticamente. Borre la caché manualmente para garantizar las operaciones correctas. Tenga en cuenta que esto suele suceder en las pruebas, cuando las instalaciones de AEM pueden reemplazarse mientras se ejecutan en la misma dirección URL (CQ-4216982)

**Utilice certificados SSL firmados por CA.** Tenga en cuenta que la aplicación de escritorio de AEM no admite certificados SSL con firma automática al conectarse a AEM mediante una conexión segura HTTPS. Se requiere un certificado firmado por CA en el servidor para dichas conexiones. (CQ-87941)

## Problemas conocidos {#known-issues}

* General:
   * Las direcciones URL del servidor son necesarias para apuntar al servidor sin una ruta (p. ej. `http://server`, `https://server`, `http://server:port`o `https://server:port`). No se admiten rutas de contexto ni subcarpetas distintas de /content/dam (CQ-89343, CQ-87272)
* Nombres de archivo/localización:
   * Los nombres de archivos y carpetas con caracteres reservados no se gestionan correctamente. Asegúrese de utilizar nombres de archivos y carpetas que se ajusten a los requisitos de AEM (CQ-93361, CQ-93308, CQ-89276, CQ-4217183)
   * Algunas aplicaciones como Adobe Illustrator pueden crear archivos con nombres no admitidos en AEM. Por ejemplo, agregar `Converted` después de convertir un archivo, lo que impide que se cargue (CQ-4216985)
   * Los recursos con nombres internacionales pueden aparecer y desaparecer cada pocos segundos
* Registro de entrada y salida:
   * Un recurso extraído por un usuario no se puede abrir para otro usuario, ya sea mediante la acción Abrir desde la IU táctil o directamente en el escritorio. Algunas aplicaciones podrían informarlo como bloqueadas, pero también como dañadas o incluso bloqueadas al intentar abrir. (CQ-4199234)
   * Cambiar archivos simultáneamente por varios usuarios puede hacer que se pierdan algunas modificaciones. La solución consiste en utilizar la funcionalidad de protección y cierre de compra para evitar que varios usuarios cambien el mismo archivo (CQ-97035)
   * Ciertas aplicaciones no admiten correctamente el indicador de solo lectura, que permite al usuario guardar un archivo extraído por otro usuario. El archivo modificado no se transfiere hasta que el otro usuario no verifique el archivo. Ambas modificaciones están disponibles en AEM como versiones diferentes del recurso (CQ-89551, CQ-87572, CQ-89615)
   * El estado de retirada y de solo lectura se notifica de forma independiente en Finder. Esto resulta en dos iconos de bloqueo cuando un usuario cierra la compra de un recurso (CQ-89507)
* Integración de Finder:
   * Al arrastrar y soltar archivos de gran tamaño, es posible que Finder agote el tiempo de espera mientras se transfieren los archivos en segundo plano. Esto resulta en un `Error - 36`. La solución consiste en arrastrar/soltar o volver a abrir el recurso (CQ-4219628)
   * La recarga manual de carpetas no siempre funciona. Solución:  espere 30 segundos para que la carpeta se actualice automáticamente. (CQ-97389)
   * Más información de recursos... está limitado a selecciones de un solo archivo (CQ-89542, CQ-87656)
   * Abrir en Recursos AEM... está limitado a selecciones de archivos y carpetas únicos (CQ-83382)
   * Error al cambiar el nombre de recursos que no tienen extensión (CQ-4218971)
* Funcionalidad Copiar/Pegar: Pegar está disponible cuando no se ha copiado ningún recurso en el portapapeles
* Windows:
   * Los archivos con flujos de datos alternativos (ADS) solo son totalmente compatibles con NTFS. Si copia estos archivos al recurso compartido WebDAV proporcionado por la aplicación de escritorio, se mostrará un cuadro de diálogo de advertencia en el que se avisará al usuario de que el archivo tiene propiedades que no se pueden copiar en la nueva ubicación. Esto suele ser correcto, ya que las propiedades solo son relevantes para una aplicación en particular en el escritorio del usuario y no tienen nada que ver con el contenido real del archivo (CQ-103770) (Win)
   * la aplicación de escritorio en Windows debe instalarla el usuario que la va a utilizar (CQ-4216389) (win)
   * La aplicación puede bloquearse al hacer clic en el botón Reintentar en una carga fallida en determinadas circunstancias después de haber reanudado la carga por lotes al desconectarse (CQ-4251884) (Win)

## Recursos útiles {#helpful-resources}

* [Documentación de AEM](https://helpx.adobe.com/support/experience-manager/6-4.html)
* [Uso de la aplicación de escritorio de AEM v1.x](use-app-v1.md)
* [Prácticas recomendadas de la aplicación de escritorio v1.x de AEM](best-practices-for-v1.md)

## Matriz de compatibilidad y requisitos previos {#compatibilitymatrix}

La aplicación de escritorio AEM funciona con varias versiones de AEM. Consulte la matriz de compatibilidad para las versiones compatibles.

| Versión | Revisión | Fecha de lanzamiento | Compatibilidad |
|---------|------------------------|--------------|-------------------------------------------------------------|
| 1.10 | 1.10.0.3 (Mac y Win) | 31 de agosto de 2018 | AEM 6.5; AEM 6.4 SP1; AEM 6.3 SP2; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
| 1.9 | 1.9.1.1 (Mac y Win) | 21 de junio de 2018 | AEM 6.4; AEM 6.3 SP1; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
| 1.8 | 1.8.1.0 (Mac y Win) | 28 de marzo de 2018 | AEM 6.4; AEM 6.3 SP1; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
| 1.7 | 1.7.0.3 (Mac y Win) | 10 de enero de 2018 | AEM 6.3 SP1; AEM 6.2 SP1 CFP2+; AEM 6.1 SP2 CFP7+ |
