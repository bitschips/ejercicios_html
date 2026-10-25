# 🔬🔋 Battery Charging and Autonomy Experiments

**English** | [Español](README.es.md)

**Version:** 1.4.4  
**Date:** 25/10/2026  
**Type:** Progressive Web App (PWA), designed for Android.

## Overview
A browser-based lab notebook for battery charging and device runtime experiments. Create, view, edit, complete and delete experiments without an account or backend.

## Charging and autonomy
Use the **Charging** tab to track a battery's charging process: chemistry, size, nominal capacity, battery identification, initial voltage, charging voltage, charging current, start/end timestamps, final voltage and notes.

Use **Autonomy** to record how long a device or lamp runs on a battery: device, battery details, initial/final voltage and start/end timestamps. Runtime is calculated from the timestamps. Previous records are treated as charging experiments. Both types are preserved in XML backups.

## Getting started
1. Open [Battery Experiments](https://bitschips.github.io/ejercicios_html/experimentos/).
2. Select **Charging** or **Autonomy** and tap **+**.
3. Enter the battery and experiment details and tap **Save**.
4. To finish, open the card and select **Edit / finish**, enter the end time and final voltage, then save.
5. Use the expanded card to review values, notes, and edit/delete actions.

**In progress** is shown in red; **Completed** in green. Dates on cards use **dd/mm/yy**. Completed experiments show their duration. For charging experiments with a recorded current, estimated charge is calculated as **mAh = mA × hours**, assuming constant current. This is not a measured battery capacity or charging efficiency.

## Expandable cards
Cards show experiment number, identification, optional photo, status, date and (when available) duration while collapsed. Tap a card to expand voltage and current readings, estimated charge (if applicable), notes and action buttons.

Under the experiment number, **Charging** shows battery identification, falling back to chemistry, size and capacity. **Autonomy** shows **Device @ Battery**.

## Experiment photos
Each experiment supports **one photo**, visible even when its card is collapsed. In the edit form, choose **Experiment photo** to take a picture or select an existing image; use **Remove photo** to clear it. Images are automatically resized to a maximum of **800 pixels on the longest side** and compressed to **JPEG quality 55%**.

Photos are stored locally with the records and included in exported XML as Base64-encoded JPEG data. XML import restores them; older XML backups without photos remain compatible. Photos consume browser storage, so export backups regularly.

## Battery details
Supported battery formats include AAA, AA, A, Sub-C, C, D, 9 V (PP3), 18650, 21700, 26650, Button cell (generic), Rechargeable button cell, CR2032, prismatic, pouch and other. Size is separate from chemistry and capacity. The **Battery identification** field distinguishes individual batteries (for example, “old drill battery”).

## Language
The app interface is in English. The documentation is available in English and Spanish. Switching documentation language does not change stored data or XML.

## Local storage and XML backups
Records and photos are saved in your browser's **localStorage**, not on GitHub or a server. They persist across normal browser restarts but may be lost if site data is cleared, the browser is uninstalled, or the phone is reset. Clearing cached files alone does not normally remove localStorage.

- **Export XML** downloads all experiments, including photos, as a backup.
- **Import XML** supports **MERGE** (skip existing IDs) or **REPLACE** (overwrite local records). Export a backup before replacing.

Back up the XML outside your browser, such as to another device or cloud storage. Data does not automatically sync between phones.

## Installation and offline use
Open https://bitschips.github.io/ejercicios_html/experimentos/ in Chrome. You can add the PWA to your home screen. A service worker caches application resources for offline use after the first visit; updates may take time to appear because of caching. The footer's **User manual (README)** link opens this GitHub documentation and requires internet access.

## Project files
- `index.html`: user interface, form and styling.
- `app.js`: experiment logic, calculations, localStorage and XML import/export.
- `manifest.webmanifest`: PWA installation metadata.
- `sw.js`: offline cache.
- `icon.svg`: installation icon.
- `brand-icon.svg`: header illustration.
- `README.md`: English manual.
- `README.es.md`: Spanish manual.

## Author
**Luis T Escolar** · [Bits Chips YouTube channel](https://www.youtube.com/BitsChips).

## Version history
**1.4.4 (25/10/2026):** Separate generic and rechargeable button-cell formats; CR2032 remains available.

**1.4.2 (25/10/2026):** Added generic Button cell to the battery size selector while retaining CR2032 as a specific option.

**1.4.1 (25/10/2026):** Expandable experiment cards with photo, identification, status, date and duration in the collapsed view; detailed measurements and actions when expanded.

**1.4.0 (25/10/2026):** One automatically compressed JPEG photo per experiment (800 px maximum, 55% quality), stored locally and included in XML import/export, compatible with older backups.

**1.3.1 (25/10/2026):** Red/green status indicators, dd/mm/yy dates, battery identification for charging and “Device @ Battery” for autonomy.

**1.3.0 (24/10/2026):** Charging and Autonomy tabs, device runtime, backwards-compatible XML and PWA cache update.

**1.2.4 (23/10/2026):** Unified SVG header icon; manual and cache updated.

**1.2.3 (23/10/2026):** Responsive header layout.

**1.2.2 (23/10/2026):** Microscope and battery icons added to app title.

**1.2.1 (23/10/2026):** README manual link in footer.

**1.2.0 (23/10/2026):** English interface and backup reminder.

**1.1.1 (23/10/2026):** Author and YouTube channel in footer.

**1.1.0 (23/10/2026):** Physical battery format added to records and XML.

**1.0.0 (23/10/2026):** Initial documented release.

When changing the application, update both manuals and the version history.

## Safety
This app is a record-keeping notebook, **not a charging controller**. Always use appropriate charging hardware and voltage/current limits for each battery chemistry.

## Linking autonomy to a completed charge (v1.4.4)
When creating or editing an autonomy experiment, optionally select a completed charging experiment. Only completed charges appear, newest first. The battery chemistry, format, capacity and identification are copied, and the charging experiment's final voltage becomes the autonomy initial voltage. You may edit any copied value. Choose **None — Enter details manually** to enter all fields yourself. The link is saved and included in XML export/import; existing experiments remain compatible.
