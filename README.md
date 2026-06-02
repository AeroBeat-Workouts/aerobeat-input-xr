# AeroBeat Input Driver - XR

This repo preserves AeroBeat's XR input path as **future support only**.

It exists for later VR-return exploration and API continuity, but it is **not** part of the current official AeroBeat v1 gameplay-input story. Official v1 gameplay remains **camera-driven Boxing and Flow on PC first**.

Input Drivers bridge hardware-specific signals (camera pipelines, XR controllers, accessibility devices, and other experiments) into normalized AeroBeat input contracts.

## Current scope

- preserve the XR repo/package surface for future work
- avoid implying XR gameplay parity with the current v1 camera path
- keep development/test metadata truthful for anyone auditing the package today

## 📋 Repository Details

*   **Type:** Input Driver
*   **Current Product Status:** **Future support only**
*   **License:** **Mozilla Public License 2.0 (MPL 2.0)**
*   **Dependencies:**
    *   `aerobeat-input-core` (Canonical shared input contract / intended lane ownership)
    *   `aerobeat-vendor-*` (Allowed)

## GodotEnv development flow

This repo uses the AeroBeat GodotEnv package convention.

- Canonical dev/test manifest: `.testbed/addons.jsonc`
- Installed dev/test addons: `.testbed/addons/`
- GodotEnv cache: `.testbed/.addons/`
- Hidden workbench project: `.testbed/project.godot`
- Repo-local unit tests: `.testbed/tests/`

The repo root remains the package/published boundary for downstream consumers. Day-to-day development, debugging, and validation happen from the hidden `.testbed/` workbench using the pinned OpenClaw toolchain: Godot `4.6.2 stable standard`.

### Restore dev/test dependencies

From the repo root:

```bash
cd .testbed
godotenv addons install
```

That restores this repo's current dev/test manifest into `.testbed/addons/`. The intended lane naming for input repos is `aerobeat-input-core`, but this repo's current manifest still reflects the older transition-era `aerobeat-core` package key.

### Open the workbench

From the repo root:

```bash
godot --editor --path .testbed
```

Use this `.testbed/` project as the canonical direct-development and bugfinding surface for input-driver work.

### Import smoke check

From the repo root:

```bash
godot --headless --path .testbed --import
```

### Run unit tests

From the repo root:

```bash
godot --headless --path .testbed --script addons/aerobeat-vendor-godot-unit-test/gut_cmdln.gd \
  -gdir=res://tests \
  -ginclude_subdirs \
  -gexit
```

### Validation notes

- `.testbed/addons.jsonc` is the committed dev/test dependency contract.
- The current manifest still pins the transition-era `aerobeat-core` package key to `v0.1.0` alongside GUT `main`. Canonical lane ownership is `aerobeat-input-core`.
- Repo-local unit tests live under `.testbed/tests/`; this repo's current package payload is rooted at `/`, so the workbench does not ship a `.testbed/src` bridge for this subset.
- The current package shape is consumed from the repo root (`subfolder: "/"`) for downstream installs.
- Passing validation here means the package surface is internally coherent, **not** that XR is an official v1 gameplay input.