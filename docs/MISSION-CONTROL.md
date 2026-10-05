# Mission control

The one page to read to know where everything stands. Each lane keeps its own row current. The Producer role checks it weekly.

## Current milestone

**M0: Setup and spikes.** Prove the two biggest unknowns (device performance, sprite pipeline) and get the repo, Godot project and checks running. Definition of done in `ROADMAP.md`.

## Lanes

| Lane | Callsign | Status | § Now | Waiting on |
|---|---|---|---|---|
| Director | — | Active | Repo scaffolded, specs drafted, ADR-001 to 006 accepted | Spike results |
| Engineers | `mech` | Active | Not started | M0-T01 (Godot project) |
| Geomancers | `env` | Active | Not started | Nothing. Can start M0-T01 |
| Judges | `qa` | Active | Not started | M0-T01 (Godot project) |
| Art | `art` | Spike only | SPIKE-02 brief written | Director to run SPIKE-02 |

Lanes not yet staffed (Balance, Enemy AI, Presentation, UI/UX, Story, Audio, Tools, Librarian, Producer) are listed in `lanes/README.md` with the signal that triggers their split.

## Next three tasks

1. **M0-T01** (`env`): Godot project init, pinned version, Mobile renderer, 360×360 viewport scaled 2×
2. **SPIKE-01** (`env`): device performance spike
3. **SPIKE-02** (Director + `art`): sprite pipeline spike

## Open decisions

None blocking. Open questions live in each design spec's "Open questions" section.
