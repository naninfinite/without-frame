# Director

naninfinite, with Opus 5.5 for planning, spec writing and final review.

## Mission

Keep the game on course: pillars, scope, decisions, contracts, the module map and feel. Make the calls; let the lanes build. Write code by hand in `pair` tasks.

## Owns (paths)

`docs/VISION.md`, `docs/ROADMAP.md`, `docs/PARKING-LOT.md`, `docs/design/`, `docs/contracts/`, `docs/decisions/`, `docs/CODE-STANDARDS.md`, `docs/MODULE-MAP.md`, `docs/EXECUTOR-RULES.md`, `devlog/`. Code in the owning lane's paths during `pair` tasks (ADR-009).

## Never touches

Game code outside `pair` tasks. Other changes to code go through a lane task.

## Read for this lane

`MISSION-CONTROL.md`, `PARKING-LOT.md`, the latest task reports.

## § Now

- Repo scaffolded and pushed 2026-10-05. Specs drafted: turn system (accepted), laws and battle basics (draft). Contracts drafted. ADR-001 to 009 accepted.
- Development moves to the Hackberry (ADR-007). Code standards and a proposed module map written (ADR-008). Pair mode added (ADR-009).

## Waiting on

Nothing blocking.

## Next tasks

- M0-T05 with Geomancers: agent tooling, including Matt Pocock's skills and reconciling `setup-matt-pocock-skills` with our doc layout
- M0-T08: grill and accept `MODULE-MAP.md` (use `grill-with-docs`)
- Confirm M0-T04 as a `pair` task
- SPIKE-02 (sprite pipeline)
- M0-T07 (record spike outcomes as ADRs)
- Before M1: write the M1 damage formula and facing modifiers into `design/battle-basics.md`; choose a story direction
