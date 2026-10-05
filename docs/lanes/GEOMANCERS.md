# Geomancers (`env`)

Covers Environment, view, UI, Tech/Build and Tools until they split (see `README.md`).

## Mission

Make the battle visible, playable and fast on the Hackberry: terrain, camera, sprite playback, UI, input, builds and the device loop.

## Owns (paths)

`game/view/`, `game/input/`, `maps/`, `tools/`, `.github/`, `project.godot` and Godot project settings

## Never touches

`game/rules/` (reads the event log only), `data/`, `assets/` (requests from Art), design specs and contracts (request changes from the Director).

## Read for this lane

`TECH.md` (all), `contracts/event-log.md`, `contracts/map-format.md`, `contracts/sprite-spec.md`, ADR-001, ADR-004, `spikes/SPIKE-01-device-performance.md`.

## § Now

Not started. Branch: none. Worktree: none.

## Waiting on

Nothing. M0-T01 can start.

## Next tasks

- M0-T01: Godot project init (pinned version, Mobile renderer, 360×360 viewport scaled 2×, folder layout).
- M0-T02: device loop (ARM64 export, one-command deploy, perf overlay and logger).
- SPIKE-01: device performance spike.
- M0-T06: lane path check in CI.
- M0-T05 with the Director: agent tooling.
