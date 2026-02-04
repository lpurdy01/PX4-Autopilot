# PX4-Autopilot — Agent Guidance

This is a **forked submodule** of the PX4-Autopilot project.
Agents operating in this directory must follow different rules than the parent repo.

---

## Ownership and authority

- **Upstream:** [PX4/PX4-Autopilot](https://github.com/PX4/PX4-Autopilot)
- **Fork:** lpurdy01/PX4-Autopilot
- This code is **vendor-managed**. Treat it as a dependency, not owned code.

## What agents must NOT do here

- **Do not commit directly** to this submodule
- Do not modify PX4 source files without human approval
- Do not repoint or update internal PX4 submodules (MAVLink, Gazebo plugins, DDS, etc.)
- Do not run `make` targets that alter the source tree
- Do not modify board configurations or airframe definitions without explicit instructions

## What agents may do here

- **Read** any file for context (build system, airframe configs, module source)
- **Build** SITL firmware via `make px4_sitl_default` (produces artifacts in `build/`, does not alter source)
- **Reference** PX4 internals when writing orchestration code in the parent repo
- **Propose changes** via the patch process defined in the root `AGENTS.md`

## Build context

- SITL build target: `make px4_sitl_default`
- Build output: `build/px4_sitl_default/bin/px4`
- Gazebo model integration: via `PX4_GZ_MODEL_PATH` environment variable
- Flight logs: `build/px4_sitl_default/rootfs/log/`

## Key directories for reference

| Path | Purpose |
|------|---------|
| `ROMFS/px4fmu_common/init.d-posix/airframes/` | SITL airframe definitions |
| `src/modules/` | Flight controller modules |
| `Tools/simulation/gz/` | Gazebo Harmonic bridge |
| `Tools/setup/ubuntu.sh` | Dependency installer (used by devcontainer) |
| `boards/px4/sitl/` | SITL board configuration |

## Cross-reference

- Parent repo rules: `/AGENTS.md` (root)
- Patch process: `/AGENTS.md` section 5
- Build orchestration: `/tools/simtest`
