# 🔬🔋 Experiments de càrrega i autonomia de bateries

[🇬🇧 English](README.md) | [🇪🇸 Español](README.es.md) | [🇺🇦 Українська](README.uk.md) | **🇦🇩 Català** | [🇯🇵 日本語](README.ja.md)

**Versió:** 1.4.6  
**Data:** 11/11/2026  
**Tipus:** aplicació web progressiva (PWA) per a Android.

## Descripció
Quadern de laboratori al navegador per registrar experiments de càrrega de bateries i autonomia de dispositius. Permet crear, consultar, editar, completar i eliminar experiments sense compte ni servidor.

[Obre l'aplicació](https://bitschips.github.io/ejercicios_html/experimentos/).

**Idioma de la interfície:** els botons de l'aplicació estan en anglès; aquest manual és en català. Canviar l'idioma del manual no modifica les dades ni els fitxers XML.

## Càrrega i autonomia
- **Charging (Càrrega):** registra la química, el format, la capacitat nominal (mAh), la identificació de la bateria, la tensió inicial, la tensió i el corrent de càrrega, les dates i hores d'inici i final, la tensió final i les observacions.
- **Autonomy (Autonomia):** registra el dispositiu o llum, la bateria, la tensió inicial i final i les hores d'inici i final. La durada es calcula automàticament.

Els registres antics es consideren experiments de càrrega. Ambdós tipus es conserven a les còpies XML.

## Com s'utilitza
1. Obre l'aplicació i selecciona **Charging** o **Autonomy**.
2. Prem **+** per crear un experiment.
3. Introdueix les dades i prem **Save**.
4. Per acabar-lo, obre la targeta, prem **Edit / finish**, introdueix l'hora de finalització i la tensió final i desa els canvis.
5. Desplega les targetes per veure les mesures, les observacions i les opcions d'edició i eliminació.

**In progress** es mostra en vermell i **Completed** en verd. Les dates de les targetes segueixen el format dia/mes/any.

## Càlculs i targetes
En completar un experiment es mostra la durada. En la càrrega, si es registra el corrent, la càrrega estimada és **mAh = mA × hores**, suposant un corrent constant. No representa la capacitat real mesurada ni l'eficiència de càrrega.

Les targetes plegades mostren el número, la identificació, una foto opcional, l'estat, la data i, si escau, la durada. En desplegar-les es mostren els valors elèctrics i les accions. A **Charging** es mostra la identificació de la bateria o les seves característiques; a **Autonomy**, **Dispositiu @ Bateria**.

## Fotografies
Cada experiment admet **una fotografia**. A **Experiment photo**, fes una foto o tria'n una d'existent; **Remove photo** l'elimina. Es redimensiona automàticament a un màxim de **800 píxels** pel costat més llarg i es comprimeix en JPEG amb qualitat del **55 %**. Les fotos es guarden localment i s'inclouen a l'XML en Base64. Els XML antics sense fotos continuen sent compatibles.

## Formats de bateria
Formats disponibles: AAA, AA, A, Sub-C, C, D, 9 V (PP3), 18650, 21700, 26650, pila de botó genèrica, pila de botó recarregable, CR2032, prismàtica, pouch i altres. El format és independent de la química i la capacitat. **Battery identification** permet distingir bateries concretes.

## Vincular autonomia amb una càrrega completada
En crear o editar un experiment **Autonomy**, pots seleccionar una càrrega finalitzada. Només es mostren les càrregues completades, de més recent a més antiga. Es copien la química, el format, la capacitat i la identificació, i la tensió final de càrrega esdevé la tensió inicial d'autonomia. Tots els valors són editables. Amb **None — Enter details manually** pots introduir-los manualment. L'enllaç es conserva en exportar i importar XML.

## Emmagatzematge i còpies de seguretat
Les dades i les fotos es guarden al **localStorage** del navegador, no a GitHub ni a cap servidor. Poden perdre's si esborres les dades del lloc web, desinstal·les el navegador o restableixes el mòbil. Borrar només la memòria cau normalment no esborra localStorage.

- **Export XML:** descarrega tots els experiments i les fotos.
- **Import XML:** **MERGE** combina registres sense duplicar identificadors; **REPLACE** substitueix les dades locals.

**Exporta una còpia abans d'utilitzar REPLACE.** Guarda l'XML en un altre dispositiu o al núvol. Les dades no se sincronitzen automàticament entre mòbils.

## Instal·lació i ús sense connexió
Obre https://bitschips.github.io/ejercicios_html/experimentos/ a Chrome i afegeix la PWA a la pantalla d'inici. Després de la primera visita, el service worker emmagatzema recursos per a l'ús sense connexió. La memòria cau pot retardar les actualitzacions. Per obrir aquest manual a GitHub cal connexió a Internet.

## Fitxers del projecte
- `index.html`: interfície, formularis i estils.
- `app.js`: lògica, càlculs, emmagatzematge i XML.
- `manifest.webmanifest`: instal·lació PWA.
- `sw.js`: memòria cau per a ús sense connexió.
- `icon.svg` i `brand-icon.svg`: icones.
- `README.md`, `README.es.md`, `README.uk.md`, `README.ca.md` i `README.ja.md`: manuals en cinc idiomes.

## Autor
**Luis T Escolar** · [Canal Bits Chips a YouTube](https://www.youtube.com/BitsChips).

## Historial de versions
**1.4.6 (11/11/2026):** documentació en cinc idiomes, amb banderes i enllaços de navegació; enllaços al peu de l'aplicació.

**1.4.5:** versió mostrada anteriorment al peu de l'aplicació.

**1.4.4 (25/10/2026):** formats de pila de botó genèrica i recarregable diferenciats, amb CR2032.

## Seguretat
L'aplicació és un quadern de registre, **no un controlador de càrrega**. Utilitza carregadors adequats i respecta els límits de tensió i corrent de cada química de bateria.

## Diagrama de funcionament
[Obre el diagrama interactiu](diagram.html). Mostra el procés de càrrega i autonomia, la vinculació entre experiments i les còpies XML.
