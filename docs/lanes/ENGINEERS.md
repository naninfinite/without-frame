# Engineers (`mech`)

Covers Mechanics, Balance and Enemy AI until they split (see `README.md`).

## Mission

Build the battle rules as a pure, testable core that matches the design specs exactly.

## Owns (paths)

`game/rules/`, `data/`, `tests/rules/`. In `pair` tasks the Director writes code here and Engineers guide and review (ADR-009).

## Never touches

`game/view/`, `game/input/`, `maps/`, `assets/`, `.github/`, design specs, contracts and the module map (request changes from the Director).

## Read for this lane

`CODE-STANDARDS.md`, `MODULE-MAP.md`, `design/turn-system.md`, `design/laws.md`, `design/battle-basics.md`, `contracts/event-log.md`, `TECH.md` § Architecture, ADR-002, ADR-004, ADR-006, ADR-008, ADR-009.

## § Now

Not started. Branch: none. Worktree: none.

## Waiting on

M0-T01 (Godot project init by Geomancers) and M0-T08 (module map accepted by the Director).

## Next tasks

- M0-T04 (proposed `pair`): rules core skeleton exactly as the accepted module map, with one passing headless test. Engineers guide; the Director writes.
- M1 (once planned): clock and turn costs first, then charged abilities, with worked examples A–C from `design/turn-system.md` as tests.
