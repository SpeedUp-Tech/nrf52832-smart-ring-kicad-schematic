# nRF52832 Smart Ring KiCad Schematic

> Schematic-stage draft for engineering review. This repository does not claim electrical validation, safety, compliance, manufacturability, or production readiness.

Editable four-sheet KiCad schematic for a compact nRF52832 smart ring with optical PPG sensing, motion sensing, battery charging, and a low-noise 1.8 V rail, generated with SpeedUp for engineering review.

SpeedUp is an AI schematic generator that turns product requirements into structured schematic sheets and an editable KiCad project for engineering review.

![Smart ring architecture with power, BLE compute, and biometric sensing](evidence/block-diagram.png)

## Project snapshot

| Field | Project evidence |
|---|---|
| Product concept | Compact smart ring for sleep and heart-rate monitoring |
| Schematic structure | Top-level sheet plus `POWER`, `CORE`, and `SENSORS` hierarchical sheets |
| Main components | nRF52832 BLE SoC, MAX30101 PPG sensor, LIS2DW12 accelerometer, MCP73831 charger, TPS7A0218 1.8 V LDO |
| BOM | 25 line items and 50 placed quantities |
| Included output | Editable KiCad project, module schematics, BOM, architecture image, and schematic evidence |
| Not included | PCB layout, firmware, mechanical CAD, optical validation, RF tuning, manufacturing files, or test results |
| Status | First schematic draft for qualified engineering review |

## Original product requirement

> design a smart ring mainly used for sleep and heart rate monitoring

The complete public requirement is preserved in [PRODUCT_REQUIREMENT.md](PRODUCT_REQUIREMENT.md).

## What SpeedUp produced

SpeedUp converted the product requirement into a structured, editable KiCad project package. The repository contains the evidence actually present in the audited bundle:

- `hardware/` — Editable KiCad hardware files (5 files).
- `bom/` — Bill of materials (1 file).
- `evidence/` — Block diagrams, schematic screenshots, and other project evidence (6 files).
- `LICENSES/` — Approved license texts and references (2 files).

This release does not claim to include PCB placement, routing, Gerbers, firmware, simulation, or bench validation.

Some standalone project-local library exports are intentionally absent from this public package; see [provenance/EXCLUDED_ASSETS.md](provenance/EXCLUDED_ASSETS.md).

## Architecture and editable evidence

The generated project separates three engineering domains:

- `POWER` accepts the charging input and protected cell, manages single-cell charging, reports charge status, senses battery voltage, and generates `1V8_SYS`.
- `CORE` contains the nRF52832, clocks, decoupling, SWD access, the BLE antenna path, I2C, and sensor interrupt connections.
- `SENSORS` connects the MAX30101 optical PPG sensor and LIS2DW12 accelerometer to the shared I2C bus and dedicated interrupt signals.

![Top-level KiCad schematic linking the POWER, CORE, and SENSORS sheets](evidence/schematic-overview.png)

The top-level sheet exposes named interfaces including `1V8_SYS`, `LED_VBAT`, `BAT_SENSE`, `CHG_STATUS_N`, `I2C0_SCL`, `I2C0_SDA`, `PPG_INT_N`, `IMU_INT`, `RESET_N`, `SWD_CLK`, and `SWD_IO`. The individual module files remain editable under `hardware/modules/`.

Additional rendered evidence is available for the [nRF52832 core](evidence/core-schematic.png), [sensor sheet](evidence/sensors-schematic.png), and [charging and power sheet](evidence/power-schematic.png).

## BOM highlights

The included CSV identifies the concrete first-draft parts and references, including:

- `NRF52832-QFAA-R` BLE SoC;
- `MAX30101EFD+T` optical PPG sensor;
- `LIS2DW12TR` low-power accelerometer;
- `MCP73831T-2ATI/OT` single-cell charger;
- `TPS7A0218PDQNR` 1.8 V LDO;
- `KH-1608-H08` chip antenna, crystal, RF passives, protection, decoupling, and nine test points.

The BOM is evidence of the generated design choices, not approval of part availability, ratings, symbols, footprints, or suitability for a wearable product.

## Open in KiCad

1. Install KiCad 10 or a compatible version.
2. Download and extract the latest release, or clone this repository.
3. Open the `.kicad_pro` file under `hardware/`.
4. Review embedded symbols, hierarchy, pin mappings, and footprint assignment strings. Standalone library exports listed in [provenance/EXCLUDED_ASSETS.md](provenance/EXCLUDED_ASSETS.md) were excluded from the public package.

## Download

[Download the public editable KiCad project package from the latest GitHub Release](https://github.com/SpeedUp-Tech/nrf52832-smart-ring-kicad-schematic/releases/latest).

Release version: `v0.1.0`. This project was generated from product requirements using SpeedUp and is intended as a starting point for engineering review.

## Engineering status

Read [ENGINEERING_LIMITATIONS.md](ENGINEERING_LIMITATIONS.md) before using or modifying the files. Component choices, ratings, power behavior, interfaces, protection, thermal assumptions, RF/EMC, safety, compliance, test, manufacturing, and production release all require qualified engineering review.

For this project, the next review should focus on battery and charging limits, peak and sleep current, PPG LED current and optical geometry, accelerometer orientation and interrupt behavior, I2C electrical details, RF matching and enclosure detuning, SWD access, component footprints, mechanical fit, skin-contact materials, and the boundary between wellness use and regulated medical claims.

## Licensing and provenance

See [LICENSE_SCOPE.md](LICENSE_SCOPE.md) and [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md). Copyright and license scope do not establish engineering fitness or transfer rights in third-party materials.

## Project links

- https://speed-up.ai/blog/smart-ring-circuit-design-nrf52832-max30101/
- https://speed-up.ai/demo/nrf52832-smart-ring/
- https://speed-up.ai/

KiCad is a trademark of the KiCad project. SpeedUp is independent and is not affiliated with or endorsed by the KiCad project.
