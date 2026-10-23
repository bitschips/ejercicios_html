# Carga de baterías

**Versión:** 1.1.1  
**Fecha:** 23/10/2026  
**Tipo:** aplicación web progresiva (PWA), pensada para Android.

## Descripción
Cuaderno digital para registrar experimentos de carga de pilas y baterías. Permite crear, consultar, editar, finalizar y eliminar experimentos desde el móvil, sin cuenta ni servidor de datos.

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

## Almacenamiento y copias
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
- `icon.svg`: icono.

## Autor y canal
**Luis T Escolar** · [Canal de YouTube Bits Chips](https://www.youtube.com/BitsChips). El nombre y el enlace aparecen en el pie de la aplicación, encima de la versión.

## Versionado
**1.1.1 (23/10/2026):** añadido nombre del autor y enlace al canal de YouTube en el pie de página; manual actualizado.

**1.1.0 (23/10/2026):** añadido formato físico de pila, visible en la tarjeta y conservado en XML; documentación actualizada.\n\n**1.0.0 (23/10/2026):** versión documentada inicial. Registro de experimentos, estados en curso/finalizado, fechas en formato español, cálculos orientativos, importación/exportación XML, instalación PWA y visualización del número de versión en el pie.

El número de versión visible está en el pie de la aplicación. En futuras actualizaciones conviene modificar también este archivo y la versión mostrada.

## Aviso
La aplicación es un cuaderno de registro, no un controlador de carga. Usa siempre un cargador y límites de tensión/corriente apropiados para la química de cada batería.
