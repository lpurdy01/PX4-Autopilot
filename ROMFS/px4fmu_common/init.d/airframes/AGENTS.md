# PX4 Airframe Definitions — Agent Guidance

This directory contains airframe startup scripts that define vehicle types, mixer
assignments, and default parameters for each supported configuration.

## Context

- **Parent guidance:** `px4/AGENTS.md` (vendor submodule — read + build only)
- Each numbered file (e.g. `1001_rc_quad_x.hil`) is a shell script sourced at boot.

## How airframes work

- File naming: `<airframe_id>_<name>`
- Each script sets: geometry, mixer, default params, MAVLink streams
- Custom vehicles require a new airframe file + corresponding Gazebo model
- The `_sih` suffix indicates Software-In-Hardware simulation variants
- The `.hil` extension indicates Hardware-In-The-Loop variants

## Relevance to px4-sim-suite

- The default test model (`x500`) maps to airframe files in this directory
- Adding a custom aircraft starts here: define the airframe, then create the matching SDF model in `px4-gazebo-models/models/`
- Parameter defaults set here affect scenario behavior (e.g. `COM_RC_IN_MODE`)

## What agents should do here

- **Read** airframe scripts to understand parameter defaults for a given vehicle
- **Reference** airframe IDs when configuring simulation targets
- **Compare** airframe definitions when diagnosing parameter mismatches

## What agents must not do

- Do not create or modify airframe files without human approval
- Do not change airframe IDs — they must be globally unique across PX4
