# ESP32 IoT Development Board

## Project scope

This is a KiCad 9 project for an ESP32-C3 IoT development board. The intended
core features are an ESP32-C3 module, microSD storage, external flash, a BME280
environment sensor, and battery-management circuitry.

## Source files

- `esp_iot_devboard.kicad_pro` is the KiCad project file.
- `esp_iot_devboard.kicad_sch` is the source schematic.
- `esp_iot_devboard.kicad_pcb` is the source PCB layout.
- `esp_iot_devboard-backups/` contains KiCad recovery material; do not edit it
  as a source file.

Use KiCad's editors for schematic and layout changes. Keep the schematic,
assigned footprints, PCB, and 3D models consistent. Before manufacturing,
run ERC in Schematic Editor and DRC in PCB Editor, review all remaining
violations, and inspect the 3D viewer.

## Local reference material

The following files were copied from the `main` branch of
[`futureshocked/KLP-5e-ESP32-sensor-board`](https://github.com/futureshocked/KLP-5e-ESP32-sensor-board)
on 2026-09-14:

- `datasheets/` contains component PDFs. Consult the matching datasheet before
  selecting pins, voltage limits, layout constraints, or a footprint.
- `libraries/symbols/` contains one `.kicad_sym` file per part.
- `libraries/footprints/` contains matching `.kicad_mod` footprints.
- `libraries/3d_models/` contains STEP models.

These folders are a local component library, not yet a configured KiCad
library table. Add only the symbols and footprints actually used by this
board to project-local library tables, and set every footprint's 3D model path
relative to the project where possible.

## Hardware rules

- Preserve a continuous ground reference under high-speed or sensitive traces
  where the relevant datasheet recommends it.
- Keep the ESP32-C3 antenna keepout free of copper, traces, components, and
  enclosure metal according to Espressif's module guidance.
- Treat USB, battery input, charger, and regulator circuits as separate power
  domains until their intended connections and protection parts are confirmed.
- Confirm decoupling values and placement, pull-ups, boot/reset strapping,
  flash wiring, and microSD routing against the applicable datasheets.
- Do not copy a third-party footprint or 3D model into a fabrication release
  without checking its dimensions, pin 1 orientation, and datasheet land
  pattern.

## Repository hygiene

- Keep generated fabrication output, plots, exports, and backups out of the
  source tree unless they are intentionally requested release artifacts.
- Do not replace or discard existing KiCad source files without explicit
  approval.
- Summarize schematic, footprint, routing, and rule-check changes in commits.
