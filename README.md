<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="resources/images/td_logo_white.png">
  <img alt="TitanSlicer logo" src="resources/images/td_logo_black.png" width="30%" height="30%">
</picture>

<img width="2560" height="1541" alt="image" src="https://github.com/user-attachments/assets/49c48b38-2a34-4e38-bbd3-4f84923dc1e7" />

**TitanSlicer** — Titan Dynamics' edition of [OrcaSlicer](https://github.com/OrcaSlicer/OrcaSlicer), tuned for a production‑focused, multi‑plate print workflow.

</div>

## About this fork

TitanSlicer tracks upstream [OrcaSlicer](https://github.com/OrcaSlicer/OrcaSlicer) and layers on a set of features built around multi‑plate projects and repeatable production prints. Everything OrcaSlicer offers is still here — the sections below cover only what this fork adds on top.

## What this fork adds

### Per‑plate filament & process presets

Each build plate in a project can store its own filament and process presets, edited from the plate settings dialog:

- Switching plates automatically selects that plate's filament/process presets.
- Preset names are rendered directly on the plate label (orange title with gray subtitles).
- Associations are saved inside the `.3mf` project and tracked through undo/redo.
- Pairing is validated (both presets must be set, or neither), and you're warned when opening a file whose presets are missing.

### Per‑plate bed type

Each plate also remembers its own bed type. Switching plates auto‑selects that plate's bed type in the sidebar **Printer** dropdown — falling back to the project default and skipping unsupported bed types — and changing the dropdown writes the value back to the current plate so it sticks per‑plate. The bed type is serialized to the `.3mf` via the existing `curr_bed_type` key.

### Per‑filament bridge nozzle temperature

A new **Bridge nozzle temperature** filament setting overrides the nozzle temperature when printing bridges and internal bridges. Overhang perimeters keep using the regular nozzle temperature, and a value of `0` disables the override. Useful for cooling down bridge regions on materials that span gaps better at a lower temperature.

### Production Ready project protection

A **Production Ready** toggle in the top bar marks a project as finalized:

- Saves over a production‑ready file are blocked to prevent accidentally overwriting a validated project.
- Removing the production‑ready status requires confirmation.
- The toggle is gated to the relevant tab so it only appears where it applies.

### Titan Dynamics branding & theming

TitanSlicer ships Titan Dynamics branding — TD logo in the GUI, custom splash screen, and an adjusted color theme (including build‑plate label fonts that re‑theme in real time).

### Side‑by‑side install (TD Edition)

The TD Edition uses its own upgrade/config path, so it can be installed and configured independently of a standard OrcaSlicer installation.

## Builds & releases

CI publishes two kinds of builds via GitHub Actions:

- **Pre‑release** — development builds for testing in‑progress changes.
- **Release** — stable builds published when changes land on `main`.

## Building from source

Build commands and toolchain requirements are unchanged from upstream OrcaSlicer. See the [OrcaSlicer build guides](https://github.com/OrcaSlicer/OrcaSlicer/wiki/How-to-build) for Windows, macOS, and Linux instructions.

## Upstream documentation

For the full feature set, calibration tools, and detailed documentation, refer to the upstream project:

- Website: <https://www.orcaslicer.com/>
- Wiki: <https://github.com/OrcaSlicer/OrcaSlicer/wiki>
- Repository: <https://github.com/OrcaSlicer/OrcaSlicer>

TitanSlicer is built on OrcaSlicer, which is itself based on Bambu Studio, PrusaSlicer, and Slic3r. All upstream licenses and credits apply.
