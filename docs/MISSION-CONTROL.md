# Mission control

The one page to read to know where everything stands. Each lane keeps its own row current. The Producer role checks it weekly.

## Current milestone

**M0: Setup and spikes.** Prove the two biggest unknowns (device performance, sprite pipeline) and get the repo, Godot project and checks running. Definition of done in `ROADMAP.md`.

## Lanes

| Lane | Callsign | Status | § Now | Waiting on |
|---|---|---|---|---|
| Director | — | Active | ADR-001 to 009 accepted; code standards and proposed module map written | Nothing |
| Engineers | `mech` | Active | Not started | M0-T01 (Godot project), M0-T08 (module map) |
| Geomancers | `env` | Active | Not started | Nothing. Can start M0-T01 |
| Judges | `qa` | Active | Not started | M0-T01 (Godot project) |
| Art | `art` | Spike only | SPIKE-02 brief written | Director to run SPIKE-02 |

Lanes not yet staffed (Balance, Enemy AI, Presentation, UI/UX, Story, Audio, Tools, Librarian, Producer) are listed in `lanes/README.md` with the signal that triggers their split.

## Next three tasks

1. **M0-T05** (Director + `env`): agent tooling on the Hackberry, including Matt Pocock's skills
2. **M0-T01** (`env`): Godot project init, pinned version, Mobile renderer, 360×360 viewport scaled 2×, typed-GDScript warnings as errors
3. **M0-T08** (Director): grill and accept the module map

## Open decisions

- Is M0-T04 (rules core skeleton) a `pair` task? Proposed yes.
- Story direction: needed before M1 planning, not blocking M0.
