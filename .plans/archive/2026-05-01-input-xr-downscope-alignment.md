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

### Task 2: Independent QA verification

**Bead ID:** `oc-6zg`  
**SubAgent:** `primary`  
**Role:** `qa`  
**References:** `REF-01`, `REF-02`, `REF-03`, `REF-04`, `REF-05`, `REF-06`  
**Prompt:** Independently verify the coder output end-to-end, inspect README/plugin/testbed/tests for truth alignment, rerun validation, confirm XR is future/deprioritized only rather than current official v1 input, update this plan with QA findings, and do not close the bead.

**Folders Created/Deleted/Modified:**
- `.plans/`
- `.testbed/`

**Files Created/Deleted/Modified:**
- `.plans/2026-05-01-input-xr-downscope-alignment.md`

**Status:** ✅ Complete

**Results:** QA independently checked the repo against `aerobeat-docs` and confirmed the public truth surfaces are aligned. `README.md` now states XR is future support only and not part of the current official v1 gameplay-input story; it explicitly restates camera-driven Boxing + Flow on PC first. `plugin.cfg` now labels the package as future support and says it is not official v1 gameplay input. `.testbed/addons.jsonc` comments truthfully describe the hidden workbench manifest as transition-era metadata while reiterating XR's future-only status. `.testbed/project.godot` remains a neutral hidden workbench with only GUT enabled, and `.testbed/tests/test_example.gd` validates manifest readability rather than asserting false product support. QA reran `godotenv addons install`, `godot --headless --path .testbed --import`, and GUT; validation passed with `2/2` tests passing. Non-blocking notes: `bd update oc-6zg --status in_progress --json` failed due to a Beads workspace identity mismatch, so the bead was not modified or closed; Godot import regenerated an untracked `.testbed/tests/test_example.gd.uid` file.

### Task 3: Independent audit and bead closure

**Bead ID:** `oc-6zg`  
**SubAgent:** `primary`  
**Role:** `auditor`  
**References:** `REF-01`, `REF-02`, `REF-03`, `REF-04`, `REF-05`, `REF-06`  
**Prompt:** Independently truth-check the finished repo against the downscoped docs, rerun validation, verify README/plugin/testbed/tests truth plus repo cleanliness, decide whether `.testbed/tests/test_example.gd.uid` should be committed or cleaned, update this plan with the audit outcome, and close the bead yourself only if the repo truly passes.

**Folders Created/Deleted/Modified:**
- `.plans/`
- `.testbed/tests/`

**Files Created/Deleted/Modified:**
- `.plans/2026-05-01-input-xr-downscope-alignment.md`
- `.testbed/tests/test_example.gd.uid`

**Status:** ✅ Complete

**Results:** Audit reread the parent plan plus the XR docs truth in `aerobeat-docs`, then independently inspected `README.md`, `plugin.cfg`, `.testbed/addons.jsonc`, `.testbed/project.godot`, and `.testbed/tests/test_example.gd`. The repo surfaces are truthful: XR is preserved as future-only support for a later VR return, while official v1 gameplay input remains camera-driven Boxing + Flow on PC first. Audit reran `godotenv addons install`, `godot --headless --path .testbed --import`, and GUT; validation again passed with `2/2` tests. The generated `.testbed/tests/test_example.gd.uid` was judged canonical and committed rather than cleaned because comparable sibling input repos already track repo-owned Godot script UID files for the same hidden-testbed pattern, and this file is regenerated by import. After committing the UID and this audit-plan update, the repo was confirmed clean and bead `oc-6zg` was closed with an explicit audit reason.

## Final Results

**Status:** ✅ Complete

**What We Built:** A light repo-truth pass that makes `aerobeat-input-xr` clearly future/deprioritized instead of presenting XR as current official gameplay input. README, plugin metadata, and testbed manifest notes now align with the downscoped docs stance while preserving the package for future VR-return work. Independent QA verified those surfaces, and independent audit reran validation, committed the canonical test-script UID artifact, confirmed repo cleanliness, and closed the bead.

**Reference Check:** `REF-04`, `REF-05`, and `REF-06` were satisfied: XR is documented as future support only, while official v1 gameplay input remains camera only. No repo surface now claims XR as equal-status current shipping input.

**Commits:**
- `Align XR input repo with v1 downscope` - pushed to `main`
- `Audit XR downscope bead and commit test UID` - commits `.testbed/tests/test_example.gd.uid` plus the audit-plan update

**Lessons Learned:** Even a small repo-truth pass benefits from making validation intent explicit: the package can remain internally coherent and testable without implying that the associated input path is part of official v1 scope. In these Godot workbench repos, script `.uid` files should be treated deliberately: if the repo pattern already commits repo-owned script UIDs and validation regenerates them, they are better committed than left as recurring local dirt.

**QA Handoff Notes:** Independent QA pass completed. Re-ran `godotenv addons install`, `godot --headless --path .testbed --import`, and `godot --headless --path .testbed --script addons/gut/gut_cmdln.gd -gdir=res://tests -ginclude_subdirs -gexit`; result was GUT `2/2 passed`. Beads status update was not performed because `bd` reported a workspace identity mismatch. Validation produced an untracked `.testbed/tests/test_example.gd.uid` artifact.

**Audit Notes:** Independent audit reran the same validation successfully, checked repo truth against `aerobeat-docs`, treated `.testbed/tests/test_example.gd.uid` as canonical based on sibling repo norms plus deterministic regeneration during import, committed the artifact, confirmed the repo was clean afterward, and closed `oc-6zg`.

---

*Completed on 2026-05-01*