# PX4 Modules — Agent Guidance

This directory contains the runtime modules that make up the PX4 autopilot.
Each subdirectory is an independent module with its own entry point, parameters, and Kconfig.

## Context

- **Parent guidance:** `px4/AGENTS.md` (vendor submodule — read + build only)
- These modules are upstream PX4 code. Do not modify without explicit human approval.

## Key modules for this project

| Module | Purpose | Relevance |
|--------|---------|-----------|
| `commander/` | Arming, mode transitions, failsafes | Governs flight state machine tested by scenarios |
| `ekf2/` | Extended Kalman Filter — sensor fusion | Produces position/velocity estimates used in flight reports |
| `flight_mode_manager/` | High-level flight mode logic | Determines behavior during takeoff, hold, land |
| `land_detector/` | Ground contact detection | Critical for landing verification in `takeoff_land.py` |
| `logger/` | ULog flight recorder | Produces `.ulg` files consumed by `generate_flight_report.py` |
| `control_allocator/` | Motor mixing | Maps control inputs to motor outputs for airframe type |

## What agents should do here

- **Read** module source to understand flight behavior during scenario debugging
- **Reference** parameter names (`module.yaml`, `params_*.yaml`) when tuning scenarios
- **Trace** state machine logic in `commander/` when diagnosing arming or mode issues

## What agents must not do

- Do not modify module source code
- Do not add new modules — that belongs in the PX4 upstream fork workflow
- Do not change Kconfig or parameter defaults
