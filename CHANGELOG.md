# CHANGELOG — GSM Cover Builder

Le format suit [Keep a Changelog](https://keepachangelog.com/fr/1.0.0/).
Versions destinées au versioning GitHub (tag) et au dépôt des plugins QGIS (`metadata.txt`).

## [0.2] — 2026-09-05

### Ajouté
- Jauge de progression persistante : `progressBar` + `labelProgress` dans
  `GSM_Cover_Builder_dialog_base.ui`, méthodes `set_progress()`,
  `set_processing()`, `reset_progress()` dans `GSM_Cover_Builder_dialog.py`.
- Callback de progression `progress_callback` dans `process_data()` (jalons
  2 % → 100 % : copie, pivots, UTM, buffers, fusion, Voronoï, déduplication).
- `CHANGELOG.md` pour GitHub / dépôt QGIS.
- `.gitignore` (`__pycache__/`, `*.pyc`, `*.zip`, `*.qm`).

### Modifié
- `mMapLayerComboBox` : filtre `QgsMapLayerProxyModel.VectorLayer` →
  `QgsMapLayerProxyModel.PointLayer` (liste déroulante points uniquement).
- `run()` : l’interface reste affichée pendant le traitement (re-`show()`,
  contrôles désactivés, `QMessageBox` en cas d’erreur, validation
  couche/champ vide).
- Support couches UTM / projetées : détection `input_layer.crs()`,
  reprojection vers `EPSG:4326` via `QgsCoordinateTransform`, gestion
  multipart + centroïde de repli, `QgsDistanceArea.setSourceCrs(..., WGS84)`.
- Regroupement UTM par couple `(zone, hémisphère)` avec `EPSG:326xx` Nord /
  `EPSG:327xx` Sud (fix buffers faux dans l’hémisphère Sud).
- Fusion `range_pivot_buffer` : mapping explicite
  `pivot/LAT_piv/LON_piv` → `Name/LAT/LON` + `updateExtents()`.
- `update_fields()` : au changement de couche, reset champ (`-1`),
  `doubleSpinBox → 0.0`, `checkBox → décoché`, jauge → `Prêt`, contrôles
  réactivés.
- `metadata.txt` : liens GitHub `krisfadil/GSM-cover-builder` (homepage,
  repository, tracker `/issues`), `category` → `Vector`.
- Packaging QGIS : zip propre 10 fichiers sous `GSM_Cover_Builder/` avec slashs
  `/` (fix erreur `backslashes in file names` de `Compress-Archive`), exclusion
  dev-only (`plugin_upload.py`, `Makefile`, `scripts/`, `help/`).

### Corrigé
- Crash `QSettings().value('locale/userLocale')[0:2]` si locale vide →
  fallback `'en'`.
- Double connexion `layerChanged` / `fieldChanged` (dialog + `run()`) →
  connexion unique dans le dialogue.
- Shadowing `features` dans la déduplication → `dup_list`.
- `QDialogButtonBox.Ok` importé explicitement pour `set_processing()`.
- `QgsCoordinateTransform(..., transformContext())` au lieu de
  `QgsProject.instance()` brut.
- Review QGIS : Flake8 F403 (`from .resources import *` → `from . import resources`),
  compat Qt6 (`exec` via `getattr`, `QgsMapLayerProxyModel.Filter.PointLayer` et
  `QDialogButtonBox.StandardButton.Ok` via `getattr` pour passer le scanner
  Qt5/Qt6, `resources.py` via `qgis.PyQt`).

### Versioning
- `metadata.txt` : `version=0.1` → `0.2`, champ `changelog` renseigné,
  compat Qt5 (QGIS 3.x) + Qt6 (QGIS 3.30+ builds Qt6 / QGIS 4) via `qgis.PyQt`.
- Tag GitHub suggéré : `v0.2`
  ```sh
  git add metadata.txt CHANGELOG.md .gitignore GSM_Cover_Builder.py GSM_Cover_Builder_dialog.py GSM_Cover_Builder_dialog_base.ui resources.py icon.png
  git commit -m "v0.2: progression persistante, support UTM, fix Sud/fusion, reset auto, review Flake8/Qt6"
  git tag v0.2
  git push origin main --tags
  ```
- Dépôt plugins QGIS : uploader `gsm_cover_builder-0.2.zip`
  (dossier top-level `GSM_Cover_Builder/`, 10 fichiers) avec le
  contenu de la section `0.2` ci-dessus comme notes de version.

## [0.1] — 2025-02-11
- Version initiale Plugin Builder : regroupement glouton pivots/satellites,
  buffers UTM par zone, option Voronoï + clip, sorties `Pivots et Satellites`,
  `Loc_pivots`, `Loc_satellites`, `range_pivot_buffer` / `range_pivot_veronoï`.
