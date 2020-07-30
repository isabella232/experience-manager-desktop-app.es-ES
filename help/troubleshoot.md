---
title: Prácticas recomendadas para la aplicación de escritorio de Adobe Experience Manager y solución de problemas
description: Siga las optimizaciones y solucione los problemas ocasionales relacionados con la instalación, actualización, configuración, etc.
uuid: ce98a3e7-5454-41be-aaaa-4252b3e0f8dd
contentOwner: AG
products: SG_EXPERIENCEMANAGER/6.3/ASSETS
discoiquuid: f5eb222a-6cdf-4ae3-9cf2-755c873f397c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3eb9ab89ff6338fb29cfad1a031944119908d0a2
workflow-type: tm+mt
source-wordcount: '1242'
ht-degree: 1%

---


# Troubleshoot Adobe Experience Manager desktop app {#troubleshoot-v2}

La aplicación de escritorio de Adobe Experience Manager (AEM) se conecta al repositorio de administración de recursos digitales (DAM) de una implementación de Experience Manager remoto. La aplicación obtiene información del repositorio y resultados de búsqueda en el equipo, descarga y carga archivos y carpetas, e incluye funciones para gestionar conflictos con la interfaz de usuario de AEM Assets.

Siga leyendo para solucionar problemas de la aplicación, conozca las prácticas recomendadas y descubra las limitaciones.

## Best practices {#best-practices-to-prevent-troubles}

Siga las siguientes optimizaciones para evitar problemas comunes y solucionar problemas.

* **Comprenda cómo funciona** la aplicación de escritorio: Antes de empezar a usar la aplicación, dedique unos minutos a saber cómo funciona. Obtenga información sobre la vinculación entre la interfaz web Experience Manager y el escritorio, la asignación de repositorios, el almacenamiento en caché de recursos, el almacenamiento local y la carga en segundo plano. Vea [cómo funciona](release-notes.md#how-app-works).

* **Evite los caracteres no admitidos en los nombres** de carpetas: No utilice espacios en blanco ni caracteres no válidos al crear o cargar carpetas. Consulte una lista de caracteres en [Creación de carpetas en Recursos](https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/managing-assets-touch-ui.html#Creatingfolders)Experience Manager. Algunos casos de uso de Adobe Experience Manager pueden verse afectados por caracteres no admitidos en el nombre de la carpeta.

* **Prácticas recomendadas para evitar conflictos**: Para evitar conflictos potenciales al colaborar en varios recursos, consulte [Evitar conflictos](using.md#adv-workflow-collaborate-avoid-conflicts)de edición.

* **Utilice la carga de carpetas para carpetas** grandes y jerárquicas: En lugar de utilizar la interfaz web de Recursos u otros métodos, utilice la aplicación de escritorio de Experience Manager para cargar carpetas grandes. La aplicación carga los recursos en segundo plano con el registro y la supervisión. Consulte Carga [masiva de recursos](using.md#bulk-upload-assets).

* **Utilice la versión** más reciente: Utilice la versión más reciente de la aplicación y compruebe siempre la compatibilidad antes de instalar una nueva versión de la aplicación o antes de actualizar a una versión más reciente de Adobe Experience Manager. See [release notes](release-notes.md).

* **Utilice la misma letra** de unidad: Utilice la misma letra de unidad en una organización para asignarla a DAM de Adobe Experience Manager. Para ver los recursos colocados por otros usuarios, las rutas deben ser las mismas. El uso de la misma letra de unidad garantiza una ruta constante a los recursos DAM. Los recursos permanecen colocados y no se eliminan incluso si distintos usuarios utilizan distintas letras de unidad.

* **Tenga en cuenta la red**: El rendimiento de la red es fundamental para el rendimiento de la aplicación de escritorio Experience Manager. Si se enfrenta a una respuesta lenta a las transferencias de archivos o a las operaciones masivas, desactive las funciones o aplicaciones que pueden causar mucho tráfico en la red.

* **Casos de uso no admitidos para la aplicación** de escritorio: No utilice la aplicación para la migración de recursos (necesita planificación y otras herramientas); para operaciones DAM de gran capacidad (como mover carpetas grandes, cargas grandes, buscar archivos mediante búsquedas avanzadas de metadatos); y como cliente de sincronización (los principios de diseño y los patrones de uso son diferentes de los clientes en sincronización, como Microsoft OneDrive o la sincronización de escritorio de Adobe Creative Cloud).

* **Tiempo de espera**: Actualmente, la aplicación de escritorio no tiene un valor de tiempo de espera configurable que desconecte la conexión entre el servidor Experience Manager y la aplicación de escritorio después de un intervalo de tiempo fijo. Cuando se cargan recursos de gran tamaño, si la conexión se agota después de un tiempo, la aplicación tiene el reintentos de cargar el recurso varias veces aumentando el tiempo de espera de carga. No se recomienda cambiar la configuración de tiempo de espera predeterminada.

## Cómo solucionar problemas {#troubleshooting-prep}

Para solucionar problemas de aplicaciones de escritorio, tenga en cuenta la siguiente información. Además, le prepara para transmitir mejor los problemas al Servicio de atención al cliente de Adobe si decide solicitar asistencia.

### Habilitar modo de depuración {#enable-debug-mode}

Para solucionar problemas, puede habilitar el modo de depuración y obtener más información en los registros. Para utilizar la aplicación en modo de depuración en Mac, utilice las siguientes opciones de línea de comandos en un terminal o en el símbolo del sistema: `AEM_DESKTOP_LOG_LEVEL=DEBUG open /Applications/Adobe\ Experience\ Manager\ Desktop.app`.

Para habilitar el modo de depuración en Windows, siga estos pasos:

1. Busque `Adobe Experience Manager Desktop.exe.config` el archivo en la carpeta de instalación de la aplicación de escritorio. By default, the folder is `C:\Program Files\Adobe\Adobe Experience Manager Desktop`.

1. Localice `<level value="INFO"/>` hacia el final del archivo. Cambie el valor de `INFO` a `DEBUG`, que es `<level value="DEBUG"/>`. Guarde y cierre el archivo.

1. Busque `logging.json` el archivo en la carpeta de instalación de la aplicación de escritorio. By default, the folder is `C:\Program Files\Adobe\Adobe Experience Manager Desktop\javascript\`.

1. En `logging.json` archivo, busque todas las instancias de `"level": "info"`. Cambie los valores de `info` a `debug`, que es `"level": "debug"`. Guarde y cierre el archivo.

1. Borre los directorios en caché que se encuentran en la ubicación establecida en las [preferencias](/help/install-upgrade.md#set-preferences)de la aplicación.

1. Reinicie la aplicación de escritorio.

<!-- The Windows command doesn't work for now.
* On Windows: `SET AEM_DESKTOP_LOG_LEVEL=DEBUG & "C:\Program Files\Adobe\Adobe Experience Manager Desktop\Adobe Experience Manager Desktop.exe"`
-->

### Ubicación de los archivos de registro {#check-log-files-v2}

Puede encontrar los archivos de registro de AEM aplicación de escritorio en las siguientes ubicaciones. Al cargar muchos recursos, si algunos archivos no se pueden cargar, consulte `backend.log` el archivo para identificar las cargas fallidas.

* Ruta en Windows: `%LocalAppData%\Adobe\AssetsCompanion\Logs`

* Ruta en Mac: `~/Library/Logs/Adobe\ Experience\ Manager\ Desktop`

>[!NOTE]
>
>Cuando trabaje con el Servicio de atención al cliente de Adobe en una solicitud o entrada de asistencia, puede que se le pida que comparta los archivos de registro para ayudar al equipo de atención al cliente a comprender el problema. Archive toda la `Logs` carpeta y compártala con el contacto del Servicio de atención al cliente.

### Borrar caché {#clear-cache-v2}

La eliminación de la caché de AEM aplicación de escritorio es una tarea preliminar para solucionar problemas que puede resolver varios problemas. Borre la caché de las preferencias de la aplicación. Consulte [Configuración de preferencias](install-upgrade.md#set-preferences). La ubicación predeterminada de la carpeta de caché es:

* En Windows: `%LocalAppData%\Adobe\AssetsCompanion\Cache\`

* En Mac: `~/Library/Group/Containers/group.com.adobe.aem.desktop/cache/`

Sin embargo, la ubicación puede cambiar en función del extremo de AEM configurado AEM escritorio. El valor es una versión codificada de la dirección URL de destino. Por ejemplo, si la aplicación está segmentada `http://localhost:4502`, el nombre del directorio es `http%3A%2F%2Flocalhost%3A4502%2F`. Para borrar la caché, elimine la carpeta adecuada. Otra razón para borrar la caché es liberar espacio en disco cuando se está ejecutando con poco espacio en disco.

>[!CAUTION]
>
>Si borra AEM caché de escritorio, las modificaciones de recursos locales que no se sincronizan con AEM servidor se pierden irrevocablemente.

### Conozca la versión de la aplicación de escritorio AEM {#know-app-version-v2}

Haga clic en el menú ![](assets/do-not-localize/more_options_da2.png) Aplicación para abrir el menú de la aplicación y haga clic en **[!UICONTROL Help]** > **[!UICONTROL About]**.

## No se pueden ver los recursos colocados {#placed-assets-missing}

Si no puede ver los recursos que usted u otros profesionales creativos colocaron en los archivos de soporte (por ejemplo, archivos INDD), compruebe lo siguiente:

* Conexión al servidor. La conectividad de red deficiente puede detener las descargas de recursos.
* Tamaño de archivo. Los recursos grandes tardan más en descargarse y mostrarse.
* Consistencia de la letra de unidad. Si usted u otro colaborador colocó los recursos mientras asignaba el DAM AEM a una letra de unidad diferente, no se muestran los recursos colocados.
* Permisos. Para comprobar si tiene permisos para recuperar los recursos colocados, póngase en contacto con el administrador de AEM.

## Problemas al actualizar en macOS {#issues-when-upgrading-on-macos}

En ocasiones pueden producirse problemas al actualizar AEM aplicación de escritorio en macOS. Esto se debe a que la carpeta del sistema heredada de AEM aplicación de escritorio impide que las nuevas versiones de AEM aplicación de escritorio se carguen correctamente. Para solucionar este problema, se pueden quitar manualmente las siguientes carpetas y archivos.

Antes de ejecutar los siguientes pasos, arrastre la `Adobe Experience Manager Desktop` aplicación de la carpeta Aplicaciones macOS a la papelera. A continuación, abra terminal, ejecute el siguiente comando y proporcione su contraseña cuando se le solicite.

```shell
sudo rm -rf ~/Library/Application\ Support/com.adobe.aem.desktop
sudo rm -rf ~/Library/Preferences/com.adobe.aem.desktop.plist
sudo rm -rf ~/Library/Logs/Adobe\ Experience\ Manager\ Desktop

sudo find /var/folders -type d -name "com.adobe.aem.desktop" | xargs rm -rf
sudo find /var/folders -type d -name "com.adobe.aem.desktop.finderintegration-plugin" | xargs rm -rf
```

## No se pueden cargar archivos {#upload-fails}

Si utiliza una aplicación de escritorio con AEM 6.5.1 o posterior, actualice el conector S3 o Azure a la versión 1.10.4 o posterior. Resuelve el problema de error de carga de archivos relacionado con [OAK-8599](https://issues.apache.org/jira/browse/OAK-8599). Consulte las instrucciones [de instalación](install-upgrade.md#install-v2).

## Problema de configuración de SSL {#ssl-config-v2}

Las bibliotecas que AEM aplicación de escritorio utiliza para la comunicación HTTP utilizan una estricta aplicación SSL. A veces, una conexión puede funcionar correctamente con un navegador, pero falla al usar AEM aplicación de escritorio. Para configurar SSL correctamente, instale el certificado intermedio que falta en Apache. Consulte [Cómo instalar un certificado de CA intermedio en Apache](https://access.redhat.com/solutions/43575).

## La aplicación no responde {#unresponsive}

Raramente la aplicación puede no responder, mostrar solo una pantalla en blanco o mostrar un error en la parte inferior de la interfaz sin ninguna opción en la interfaz. Pruebe lo siguiente en el orden:

* Haga clic con el botón derecho en la interfaz de la aplicación y haga clic en **[!UICONTROL Refresh]**.
* Salga de la aplicación y ábrala de nuevo.

En ambos métodos, la aplicación inicio en la carpeta DAM raíz.

>[!MORELIKETHIS]
>
>* [Problemas conocidos](release-notes.md#known-issues-v2)
>* [Evitar conflictos de edición](using.md#adv-workflow-collaborate-avoid-conflicts)

