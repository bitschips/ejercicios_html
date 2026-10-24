# 🔬🔋 Battery Charging Experiments

**Versión:** 1.3.0  
**Fecha:** 24/10/2026  
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

Las tarjetas muestran la fecha en formato **dd/mm/aaaa hh:mm**. Si se introduce una hora de fin y una corriente de carga, se calculan la duración y una **carga estimada en mAh**, suponiendo corriente constante: mAh = mA × horas. No es una medición real de capacidad ni de eficiencia de carga.

## Formato de pila
El formulario permite elegir **AAA, AA, A, Sub-C, C, D, 9 V (PP3), 18650, 21700, 26650, CR2032, prismática, bolsa (pouch) u otro**. El formato es independiente de la química y de la capacidad. Se muestra en el título de cada experimento y se incluye en las exportaciones e importaciones XML. Los registros antiguos siguen siendo compatibles y muestran el formato vacío hasta que se editen.

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
