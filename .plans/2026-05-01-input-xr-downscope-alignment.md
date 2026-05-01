# aerobeat-input-xr

**Date:** 2026-05-01  
**Status:** Complete  
**Agent:** Chip 🐱‍💻

---

## Goal

Align `aerobeat-input-xr` with the locked AeroBeat v1 downscope by making XR explicitly future/deprioritized rather than implied as a current official gameplay input.

---

## Overview

This repo is part of the AeroBeat input/platform downscope wave following the completed shell pass. The work stayed intentionally narrow: audit the repo's public truth surfaces, remove stale parity claims, and keep the package/testbed metadata honest without pretending XR is part of the current shipping gameplay slice.

The docs source of truth keeps XR documented as a future support path for a later VR return, while official v1 gameplay remains camera-driven Boxing and Flow on PC first. This pass therefore focused on README wording, plugin metadata, and testbed manifest notes rather than widening scope into new runtime implementation work.

---

## REFERENCES

| ID | Description | Path |
| --- | --- | --- |
| `REF-01` | Parent input/platform coordination plan | `/home/derrick/.openclaw/workspace/projects/openclaw-chip/.plans/2026-05-01-aerobeat-input-platform-downscope-pass.md` |
| `REF-02` | Downscoped docs source of truth | `/home/derrick/.openclaw/workspace/projects/aerobeat/aerobeat-docs` |
| `REF-03` | Owning repo | `/home/derrick/.openclaw/workspace/projects/aerobeat/aerobeat-input-xr` |
| `REF-04` | Current input architecture / provider stance | `/home/derrick/.openclaw/workspace/projects/aerobeat/aerobeat-docs/docs/architecture/input.md` |
| `REF-05` | Future-support XR API docs | `/home/derrick/.openclaw/workspace/projects/aerobeat/aerobeat-docs/docs/api/inputs/xr/index.md` |
| `REF-06` | Product-level input downscope wording | `/home/derrick/.openclaw/workspace/projects/aerobeat/aerobeat-docs/docs/gdd/input-system/agnostic-input.md` |

---

## Tasks

### Task 1: Audit and align repo truth

**Bead ID:** `oc-6zg`  
**SubAgent:** `primary`  
**Role:** `coder`  
**References:** `REF-01`, `REF-02`, `REF-03`, `REF-04`, `REF-05`, `REF-06`  
**Prompt:** Claim the assigned bead, audit the repo against the downscoped AeroBeat docs truth, implement the required alignment changes, run relevant validation, commit/push to `main`, and leave concise QA handoff notes.

**Folders Created/Deleted/Modified:**
- `.plans/`
- `.testbed/`

**Files Created/Deleted/Modified:**
- `README.md`
- `plugin.cfg`
- `.testbed/addons.jsonc`
- `.plans/2026-05-01-input-xr-downscope-alignment.md`

**Status:** ✅ Complete

**Results:** Reworded the README so the repo now explicitly describes XR as future support only, tied it to the later VR return path, and restated the official v1 gameplay truth as camera-driven Boxing + Flow on PC first. Updated `plugin.cfg` so the package name/description no longer imply current official XR support. Updated `.testbed/addons.jsonc` comments so the hidden workbench contract is described truthfully as transition-era metadata rather than present-tense product support. Validation passed via `godotenv addons install`, `godot --headless --path .testbed --import`, and GUT (`2/2` tests passing). Commit/push details recorded below.

---

## Final Results

**Status:** ✅ Complete

**What We Built:** A light repo-truth pass that makes `aerobeat-input-xr` clearly future/deprioritized instead of presenting XR as current official gameplay input. README, plugin metadata, and testbed manifest notes now align with the downscoped docs stance while preserving the package for future VR-return work.

**Reference Check:** `REF-04`, `REF-05`, and `REF-06` were satisfied: XR is documented as future support only, while official v1 gameplay input remains camera only. No repo surface now claims XR as equal-status current shipping input.

**Commits:**
- `Align XR input repo with v1 downscope` - pushed to `main`

**Lessons Learned:** Even a small repo-truth pass benefits from making validation intent explicit: the package can remain internally coherent and testable without implying that the associated input path is part of official v1 scope.

**QA Handoff Notes:** Verify that the repo's public-facing surfaces now consistently say XR is future support only: `README.md`, `plugin.cfg`, and `.testbed/addons.jsonc`. Re-run `godot --headless --path .testbed --import` and `godot --headless --path .testbed --script addons/gut/gut_cmdln.gd -gdir=res://tests -ginclude_subdirs -gexit`; expected result is GUT `2/2 passed` with no wording left that calls XR an official v1 gameplay path.

---

*Completed on 2026-05-01*