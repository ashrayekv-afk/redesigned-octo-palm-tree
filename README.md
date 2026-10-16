# NKPI bilateral calculator — 9.0.7

The 3D viewer now opens with **Surface shape**, using solid shading to make the reconstructed corneal geometry easier to inspect. **Close-up** frames the available corneal area, and **Shape profile** turns toward a supported anterior-elevation feature. **Natural eye**, the map overlays, tissue cutaway, regional comparison and cone evolution tracker remain available.

## Install / update

Use **NKPI_v907_GitHub_Upload.zip**. It contains four top-level files and one configuration file:

- `kcn_dual_calculator_app.py` — launcher; keep this exact filename as the Streamlit main file.
- `nkpi_runtime.zip` — complete app source, trained-model JSON files, viewer, importer, OCR assets, and retained tests/documentation. Upload this inner ZIP intact.
- `requirements.txt` — retained Python dependency declarations.
- `README.md` — installation steps.
- `.streamlit/config.toml` — retained theme and app settings; preserve this path.

1. Download **NKPI_v907_GitHub_Upload.zip** and use Windows **Extract All** once.
2. Upload the extracted release files to the same GitHub repository, replacing the matching files. The four top-level files belong at the repository root; `config.toml` belongs inside `.streamlit`. Keep `nkpi_runtime.zip` zipped. Do not put the release inside an extra enclosing folder.
3. Keep **kcn_dual_calculator_app.py** as Streamlit's main file, using the updated repository and branch. Python **3.12** remains the target runtime; see `docs/TEST_REPORT.md` inside the runtime archive for release verification.
4. Reboot the app and refresh the browser. Confirm **9.0.7-anatomical-eye** in the footer, then reimport the original Pentacam ZIPs, verify the measurements and calculate.
5. Open **Regional change & 3D corneal view → Current case → OD/OS → 3D corneal view**. The **Cone evolution tracker** uses two visits.

The launcher verifies the version-matched runtime and unpacks it automatically on the server. You do not need to re-upload the `nkpi`, `components`, `models` or `research` folders. Older copies of those folders may remain in the repository; the launcher selects the bundled release. No new API key is needed. The existing browser OCR/PDF libraries still need their normal network access.

Local launch: `python -m pip install -r requirements.txt`, then `python -m streamlit run kcn_dual_calculator_app.py`. For source inspection, extract a separate copy of `nkpi_runtime.zip`; it contains the complete ordinary source tree.

## What changed in 9.0.7

- **Surface shape:** solid shading makes the source-derived shape visible without a map texture covering it. Switch to **Natural eye** for the anatomical appearance or select a curvature, elevation or thickness overlay.
- **Close-up:** the camera frames the available source radius instead of the surrounding reference eyeball.
- **Shape profile:** the inspection meridian follows a supported positive anterior-elevation feature when available. This feature is an inspection location, not a validated cone apex.
- **True scale / 3× / 6× relief:** true scale preserves the existing geometry. For report-image estimates, the optional relief settings amplify deviation from the assumed reference sphere and remain visibly labeled. They do not change source measurements, thickness values or calculator results. Native numerical surface imports retain true-scale geometry.
- **Consistent contours:** thickness contours follow the geometry currently displayed, including an emphasized report-image view.
- **Retained workflow:** natural eye, rotation, overlays, cutaway, source inspection, OD/OS and visit selection, regional maps and the cone evolution tracker remain available. Both NKPI models and their calculation behavior are retained.

## What the reports support

The automatic image route uses the standard anterior-elevation map, printed anterior BFS and thickness map from a supported Belin–Ambrósio report. It estimates an anterior surface using the existing reference-position assumptions and infers the inner surface from pachymetry. This is approximate geometry, not an independently measured posterior surface or an exact 1:1 replica. Solid shading and optional relief do not remove those limits. No patient cone is fabricated from Kmax, NKPI or map color alone.

Gap completion and the smooth peripheral transition remain presentation features. Original missing values, source coverage, NKPI, biological domains, regional measurements and cone tracking retain their existing meaning. Filled geometry does not receive measured patient readouts. The globe, iris and peripheral transition are illustrative.

The existing numerical import accepts anterior/posterior x/y/z grids and device pachymetry with documented units, laterality and a shared coordinate system. Native heights remain at supported source nodes; display interpolation stays separate. The viewer is not a surgical planning model.

Keep complete original report ZIPs. Supported automatic layouts are the original 1200-pixel-wide exports and proportional scaling, with complete titles and legends. Phone photographs, mirrored/rotated pages, cropped legends and undocumented layouts are not automatically calibrated. Regional comparison still uses Topometric/KC-Staging anterior/posterior axial curvature and Belin–Ambrósio thickness; posterior elevation is not substituted for posterior curvature.

## If the app reports a missing or mismatched bundle

Upload `kcn_dual_calculator_app.py` and `nkpi_runtime.zip` together from the same release download, at the same repository level, and reboot. Keep both filenames unchanged. The launcher does not substitute a fallback score when installation or calculation fails.

See **docs/SURFACE_DATA.md** for the retained reconstruction method and **docs/TEST_REPORT.md** for current verification and limits. Patient scans and private QA files are not included in the release.
