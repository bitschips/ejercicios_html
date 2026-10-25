[English](README.md) | **Español**

# 🔬🔋 Experimentos de carga y autonomía de baterías

**Versión:** 1.4.4  
**Fecha:** 25/10/2026  
**Tipo:** aplicación web progresiva (PWA), pensada para Android.

## Descripción
Cuaderno digital para registrar experimentos de carga de pilas y baterías. Permite crear, consultar, editar, finalizar y eliminar experimentos desde el móvil, sin cuenta ni servidor de datos.

## Pestañas de carga y autonomía
La aplicación muestra dos pestañas independientes: **Charging** y **Autonomy**. Los registros anteriores se consideran experimentos de carga y se mantienen en el mismo almacenamiento local. En autonomía se introduce el dispositivo o lámpara, la tensión inicial, la hora de inicio, la hora de fin y la tensión final. La duración se calcula automáticamente, sin estimar capacidad ni registrar aporte solar. Ambas categorías se incluyen en exportación e importación XML mediante el campo `clase`; los XML antiguos siguen siendo compatibles.

## Uso
1. Abre la aplicación y pulsa **+** para crear un experimento.
2. Introduce el tipo de pila (química), formato físico y capacidad nominal (mAh), tensión inicial (V), tensión de carga (V), intensidad de carga (mA) y fecha y hora de inicio.
3. Pulsa **Guardar**. El experimento aparece como **En curso**, destacado en rojo.
4. Para terminarlo, pulsa **Editar / finalizar**, indica fecha y hora de fin y tensión final, y guarda. Pasará a **Finalizado**.
5. Puedes añadir observaciones o eliminar una ficha (con confirmación).

Las tarjetas muestran la fecha de inicio en formato **dd/mm/aa** y una etiqueta roja (**In progress**) o verde (**Completed**), según el estado. Si se introduce una hora de fin y una corriente de carga, se calculan la duración y una **carga estimada en mAh**, suponiendo corriente constante: mAh = mA × horas. No es una medición real de capacidad ni de eficiencia de carga.

## Tarjetas desplegables y fotografías
Cada experimento se presenta como una tarjeta desplegable. La vista compacta muestra el número, la identificación, una fotografía (si existe), el estado, la fecha y la duración cuando está finalizado. Al tocar la tarjeta se despliegan los valores eléctricos, la carga estimada cuando procede, las observaciones y los botones para editar, finalizar o eliminar.

En **Charging**, bajo el número del experimento aparece la identificación de la batería (o su química, formato y capacidad si no tiene identificación). En **Autonomy**, aparece **Dispositivo @ Batería** para identificar el montaje de descarga.

Cada experimento admite **una fotografía**. Desde el formulario, pulsa **Experiment photo**, toma una foto con la cámara o selecciona una imagen; se muestra una vista previa y puedes quitarla con **Remove photo**. La imagen se reduce automáticamente a un máximo de **800 píxeles en su lado más largo** y se comprime como **JPEG al 55 % de calidad**. La fotografía permanece visible incluso con la tarjeta contraída.

La foto se almacena junto con el experimento en el navegador y se incluye en el XML como datos JPEG codificados en Base64. **Export XML** permite respaldar también las fotos e **Import XML** las restaura. Los XML antiguos sin fotografías siguen siendo compatibles. Las imágenes aumentan el tamaño de los datos y pueden agotar el espacio disponible en localStorage; conviene exportar copias periódicamente.

## Formato de pila
El formulario permite elegir **AAA, AA, A, Sub-C, C, D, 9 V (PP3), 18650, 21700, 26650, botón genérica (Button cell), botón recargable (Rechargeable button cell), CR2032, prismática, bolsa (pouch) u otro**. El formato es independiente de la química y de la capacidad. Se muestra en el título de cada experimento y se incluye en las exportaciones e importaciones XML. Los registros antiguos siguen siendo compatibles y muestran el formato vacío hasta que se editen.

El campo **Identificación de batería** permite distinguir baterías de igual capacidad, por ejemplo «taladro antiguo» o «comprada en MediaMarkt».

## Idioma de la aplicación
La interfaz está disponible en **inglés**. Los datos almacenados y el XML no cambian por el idioma de la interfaz. Las fechas siguen en formato día/mes/año.

## Almacenamiento y copias
**Aviso visible al pie:** los experimentos deben exportarse a XML y guardarse fuera del navegador para conservarlos al cambiar de móvil. Borrar únicamente archivos e imágenes en caché normalmente no elimina localStorage, pero borrar datos del sitio sí puede hacerlo.

Los registros se guardan en **localStorage** del navegador del dispositivo. Persisten al cerrar la pestaña, pero pueden perderse al borrar los datos del sitio, desinstalar el navegador o restablecer el móvil. No se sincronizan automáticamente entre dispositivos ni se publican en GitHub.

- **Exportar XML:** descarga todos los experimentos en un archivo XML que puedes conservar o compartir como copia de seguridad.
- **Importar XML:** permite **COMBINAR** registros (sin duplicar identificadores) o **SUSTITUIR** los registros existentes. Exporta una copia antes de sustituir.

## Instalación y uso sin conexión
Abre https://bitschips.github.io/ejercicios_html/experimentos/ en Chrome. Con GitHub Pages (HTTPS), la PWA puede añadirse a la pantalla de inicio. Un service worker almacena recursos para facilitar el uso sin conexión después de la primera carga; las actualizaciones pueden tardar en aparecer por la caché.

## Archivos
- `index.html`: interfaz, formulario y estilos.
- `app.js`: lógica de registros, cálculos, localStorage e importación/exportación XML.
- `manifest.webmanifest`: nombre y configuración de instalación PWA.
- `sw.js`: almacenamiento en caché para uso sin conexión.
- `icon.svg`: icono de instalación.
- `brand-icon.svg`: imagen única de la cabecera.

## Autor y canal
**Luis T Escolar** · [Canal de YouTube Bits Chips](https://www.youtube.com/BitsChips). El nombre y el enlace aparecen en el pie de la aplicación, encima de la versión.

## Manual desde la aplicación
En el pie de la aplicación hay un enlace **User manual (README)** que abre este manual Markdown en GitHub en una nueva pestaña. Se requiere conexión para consultar GitHub.

## Iconos del título
La cabecera presenta una imagen SVG única (batería, matraz y rayo sobre fondo rojo) a la izquierda y, a la derecha, el título y subtítulo alineados. El diseño usa Flexbox y se adapta a pantallas pequeñas. El título de la pestaña conserva los iconos.

## Versionado
**1.4.4 (25/10/2026):** diferenciadas las pilas de botón genéricas y recargables, conservando CR2032.

**1.4.2 (25/10/2026):** añadido el formato genérico de pila de botón (Button cell) al selector, manteniendo CR2032 como opción específica.

**1.4.1 (25/10/2026):** tarjetas desplegables con fotografía, identificación, estado, fecha y duración en la vista compacta; detalles y acciones al expandir.

**1.4.0 (25/10/2026):** una fotografía comprimida por experimento (JPEG, 800 px máximo, calidad 55 %), guardada localmente e incluida en exportación e importación XML; compatibilidad con copias antiguas.

**1.3.1 (25/10/2026):** indicadores rojo/verde según el estado, fecha dd/mm/aa, identificación de batería en carga y «Dispositivo @ Batería» en autonomía.

**1.3.0 (24/10/2026):** pestañas Charging y Autonomy, registro de dispositivo y duración de descarga, XML compatible con registros anteriores y actualización de caché PWA.

**1.2.4 (23/10/2026):** sustituido el par de emojis de la cabecera por un icono SVG único y adaptable; manual y caché actualizados.

**1.2.3 (23/10/2026):** cabecera responsive con iconos en un bloque independiente y título/subtítulo alineados a la derecha; manual actualizado.

**1.2.2 (23/10/2026):** añadidos iconos de microscopio y batería al título de la aplicación y de la pestaña; versión y manual actualizados.

**1.2.1 (23/10/2026):** enlace directo al manual Markdown en el pie de la aplicación; documentación actualizada.

**1.2.0 (23/10/2026):** interfaz y mensajes en inglés, inglés como idioma predeterminado, aviso visible de conservación de datos y copias XML antes del autor, documentación actualizada.


**1.1.1 (23/10/2026):** añadido nombre del autor y enlace al canal de YouTube en el pie de página; manual actualizado.

**1.1.0 (23/10/2026):** añadido formato físico de pila, visible en la tarjeta y conservado en XML; documentación actualizada.\n\n**1.0.0 (23/10/2026):** versión documentada inicial. Registro de experimentos, estados en curso/finalizado, fechas en formato español, cálculos orientativos, importación/exportación XML, instalación PWA y visualización del número de versión en el pie.

El número de versión visible está en el pie de la aplicación. En futuras actualizaciones conviene modificar también este archivo y la versión mostrada.

## Aviso
La aplicación es un cuaderno de registro, no un controlador de carga. Usa siempre un cargador y límites de tensión/corriente apropiados para la química de cada batería.

## Vincular autonomía con una carga completada (v1.4.4)
Al crear o editar un experimento de autonomía, puedes seleccionar opcionalmente una carga completada. Solo aparecen cargas finalizadas, de más reciente a más antigua. Se copian la química, el formato, la capacidad y la identificación de la batería; el voltaje final de carga pasa a ser el voltaje inicial de autonomía. Todos los valores se pueden modificar. Con **None — Enter details manually** puedes introducirlos manualmente. El vínculo se conserva al exportar e importar XML; los experimentos anteriores siguen siendo compatibles.
