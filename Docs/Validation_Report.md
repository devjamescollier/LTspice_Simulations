# Validation Report

This report records the checks performed while organizing and documenting the repository on 2026-10-14, and the evidence gaps that remain.

## Simulation Execution Status

**LTspice was not run during this task.** All results in the READMEs come from the existing saved captures, the saved `.asc` sources, the existing generated `.meas` log, and hand calculations. Source inspection, screenshot review, and link checks are documentation checks. They are not a fresh simulation run.

LTspice 17.2.4 is installed in this macOS environment (read from the application bundle). It was used only to confirm that the referenced symbols and models exist in its library.

## Asset Accounting

| Item | Count | Result |
| --- | --- | --- |
| Supplied original assets | 29 | All 29 found before migration and listed in [File_Rename_Manifest.csv](File_Rename_Manifest.csv) exactly once |
| Native `.asc` sources | 5 | Moved to `Simulation/LTspice_Files/` |
| Schematic PNGs | 5 | Moved to `Docs/Images/Schematics/` |
| Public plot PNGs | 17 | Moved to `Docs/Images/Plots/` |
| Excluded plot | 1 | `Instrumentation_Amplifier/Local_Archive/Excluded_Plots/` |
| Generated data file | 1 | `Monte_Carlo_RC_Band_Pass_Filter/Local_Archive/Generated_Outputs/` |
| Additional project assets found | 0 | No `.plt`, `.lib`, `.sub`, `.asy`, notes, LICENSE, COPYING, or NOTICE files were present |

Other files present: Finder `.DS_Store` metadata in the root and each original project folder. These are Git-ignored. The two folders that were renamed away (`Buck_Converter_Closed_Loop_Control/` and `Monte_Carlo_Simulation/`) contained only a `.DS_Store` after their assets moved, so they were removed. No other file was deleted.

## Preservation Checks

- **Hashes:** SHA-256 values were recorded for all 29 files before any move and recomputed at each destination. All 29 match (`SHA256_Before` = `SHA256_After` in the manifest). Files were moved with same-filesystem renames, and no file content was edited, converted, or recompressed.
- **Native sources:** No `.asc` file was modified, including path references. None of the sources uses `.include`, `.lib`, or custom symbol paths, so no reference repair was needed.
- **Encodings:** `Closed_Loop_Buck_Converter_Simulation.asc` and `Instrumentation_Amplifier_Simulation.asc` are UTF-16LE without a byte-order mark. The other three are ASCII. All five were decoded read-only and still contain their components and active directives.
- **Generated data:** The `.log.raw` file keeps its compound extension. It is a UTF-16LE ASCII-format LTspice raw file holding the 500-step `.meas` results (`gain_peak`, `peak_gain_db`, `center_frequency`) and was only read.
- **Idempotency:** The migration script was run a second time after completion. It recognized every destination as already migrated with a matching hash and made no changes.

## Image Interpretation Checks

Every image was viewed and compared with its intended name and with the source circuit. No naming correction was required. Notes:

| Asset | Check | Outcome |
| --- | --- | --- |
| Buck combined response | Trace labels and load step | `V(vout)`, `V(sw)`, `I(R1)`, `-I(L1)` over 0-10 ms; step at 5 ms visible. `-I(L1)` is positive from `SW` to `Vout` given the inductor's pin orientation. |
| Buck switching zoom | Window and signal | `V(sw)` (switching node, not gate) from 9.90 to 9.95 ms |
| Mixer `Output_Spectrum.png` | Horizontal axis | Spans 0-100 MHz, so the 100 MHz name is retained. The 0-40 MHz view is a separate span, and both are kept. |
| Amplifier common-mode test | Input conditions and residual scale | Shows `V(va)` at 1 V peak and `V(out)` at about ±0.6 µV. `V(vb)` is **not displayed**, so the identical-input condition is documented as a temporary test setting and not shown by the image. |
| Amplifier noise plot | Quantity type | `V(onoise)` and `V(inoise)` spectral densities in nV/√Hz. Not described as RMS noise. |
| Amplifier `Frequency_Response_Inverted_Ratio.png` | Trace expression | Confirmed `V(Va,Vb)/V(OUT)` (reciprocal of gain). Archived and excluded. |
| Inverter three-phase currents | Branch identity | Traces are `I(R5)`, `I(R1)`, `I(R4)`, not `I(L1..L3)`. Each resistor is in series with `L3`, `L1`, and `L2` respectively in the star branches, so the "star-connected load phase currents" name is accurate. These are not total terminal currents. |
| Monte Carlo per-run plots | Consistency with log | Extremes in the plots match the log: peak gain −7.356 dB at run 96 and −5.645 dB at run 348; center frequency 4.106 Hz at run 191 and 6.448 Hz at run 347. |

## Source and Capture Discrepancies

- **Instrumentation amplifier schematic:** The PNG shows annotations (title block, stage labels, ideal-gain equations, supply note) that are **not** in the saved `.asc`. The `.asc` still has older comment text, including a gain note using duplicate "blue" resistor aliases. Components, values, net labels, and directives agree. The README notes this.
- **Monte Carlo schematic:** The PNG shows an annotated revision that includes the K6JCA reference line. The saved `.asc` has older comments ("Monte Carlo analysis in LTSpiceIV") and no K6JCA credit. Electrical content agrees. The credit is preserved in the README and the root README.
- **Inverter DC link:** `R2` and `R3` (1 Ω each) connect each rail to the capacitor midpoint. This is preserved unchanged and noted in the README as a simulation convenience (about 36 kW each in calculation with an ideal 380 V source).

## Dependency Inspection

| Project | Dependencies | Status |
| --- | --- | --- |
| Closed-Loop Buck Converter | `BSB012N03LX3` (`standard.mos`), `1N5819` (`standard.dio`) | Present in the installed LTspice library |
| Diode Ring Mixer | `1N5819` (`standard.dio`) | Present |
| Instrumentation Amplifier | `LT1007` symbol and `LTC.lib` macromodel | Present |
| Monte Carlo RC Band-Pass Filter | Primitives only | None needed |
| Three-Phase Full-Bridge Inverter | Inline `.model SW`; default diode | Default `sw` symbol value is `SW`, matching the inline model |

## Documentation Checks

- Every relative Markdown link (images, sources, cross-project links, and table-of-contents anchors) in all eight Markdown files was resolved against the filesystem with **case-sensitive** matching. All resolve.
- `Portfolio_Asset_Index.md` links were resolved relative to `Docs/`.
- No published page links to a `Local_Archive` path, an old filename, a PDF, or the missing forward-gain image.
- All asset basenames use ASCII letters, digits, and underscores with lowercase extensions. The longest is 142 bytes. There are no case-insensitive path collisions and no nested `LTspice_Simulations/` directory.
- Code fences are balanced in every Markdown file.
- The `.gitignore` rules were tested in a disposable Git repository containing zero-byte copies of the same paths. Both `Local_Archive` items and the `.DS_Store` files are ignored, while all `.asc` sources, the 22 public PNGs, the READMEs, and the `Docs/` files remain trackable.
- External badge images and GitHub rendering were **not** checked, because no remote repository exists.

## Repository State

The directory is not a Git repository. No `git init`, commit, push, or remote publication was performed.

## Missing Evidence and Open Items

1. **Instrumentation amplifier forward-gain plot: not available.** No `V(OUT)/V(Va,Vb)` capture exists anywhere in the working directory. The reciprocal-ratio plot was archived locally, and no replacement was fabricated. The README documents how to produce the correct plot from the saved `.ac` directive.
2. **Historical analysis settings:** The instrumentation amplifier's transient, common-mode, and noise captures used temporary directives and source values that were not saved. Example directives are documented as examples only.
3. **FFT settings for the mixer captures** (window, points, time range) were not recorded.
4. **No `.plt` plot-settings files** were saved for any project.
5. **Licensing:** No LICENSE, COPYING, or NOTICE file and no upstream URL for the source collection were found. The READMEs state that no repository-wide license is declared. The owner should confirm the terms of the upstream circuit collection before publishing.
6. **Simulator version for the original captures** was not recorded. The `.meas` log identifies "LTspice XVII" only.
