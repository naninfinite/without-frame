# Lanes

A **lane** owns paths and writes. A **service role** reviews or checks and owns no game files. Each active lane has a mission-control doc here. See ADR-005 for why we start small.

## Active

| Lane | Callsign | Doc | Suggested models |
|---|---|---|---|
| Director | — | `DIRECTOR.md` | naninfinite + Opus 5.5 (planning, specs, final review) |
| Engineers | `mech` | `ENGINEERS.md` | Sonnet 5.5 writes; Opus plans hard tasks; Codex cross-reviews |
| Geomancers | `env` | `GEOMANCERS.md` | Sonnet 5.5 writes with the Godot MCP; Codex cross-reviews |
| Judges | `qa` | `JUDGES.md` | A different model family from whoever wrote the code; cheap multimodal models for screenshot and log triage |
| Art (spike only) | `art` | `ART.md` | Director-led, via MCP tools |

## Not yet staffed, and the signal to split them off

Split a lane only when its signal appears. Splitting needs an ADR.

| Future lane | Callsign | Currently inside | Split when… |
|---|---|---|---|
| Balance | Calculators `bal` | Engineers | Number tuning starts competing with rules work, or balance simulations need their own owner (expected M2) |
| Enemy AI | Templars `ai` | Engineers | AI work grows beyond "never breaks a law" (expected M2) |
| Art | Illusionists `art` | Spike | SPIKE-02 passes and real sprite production starts |
| Presentation | Dancers `stage` | Geomancers | Event-log playback, effects and animation timing become a workload of their own |
| UI/UX | Seers `ui` | Geomancers | Menus, turn queue and forecast work collide with terrain and camera work |
| Tools | Chemists `tools` | Geomancers | More than two internal tools are maintained |
| Story | Oracles `story` | — (one-page bible by Director) | M3 campaign planning |
| Audio | Bards `audio` | — | M3 |
| Librarian | Time Mages `lib` | Judges | Doc drift checks become a regular chore |
| Producer | Mediators `prod` | Director | Mission control upkeep takes more than the weekly ritual |

## Lane doc template

```
# <Lane> (<callsign>)
## Mission
## Owns (paths)
## Never touches
## Read for this lane
## § Now
## Waiting on
## Next tasks
```
