# Engineers (`mech`)

Covers Mechanics, Balance and Enemy AI until they split (see `README.md`).

## Mission

Build the battle rules as a pure, testable core that matches the design specs exactly.

## Owns (paths)

`game/rules/`, `data/`, `tests/rules/`

## Never touches

`game/view/`, `game/input/`, `maps/`, `assets/`, `.github/`, design specs and contracts (request changes from the Director).

## Read for this lane

`design/turn-system.md`, `design/laws.md`, `design/battle-basics.md`, `contracts/event-log.md`, `TECH.md` § Architecture and § Rules for all code, ADR-002, ADR-004, ADR-006.

## § Now

Not started. Branch: none. Worktree: none.

## Waiting on

M0-T01 (Godot project init by Geomancers).

## Next tasks

- M0-T04: rules core skeleton (battle state, command input, event log output) with one passing headless test.
- M1 (once planned): clock and turn costs first, then charged abilities, with worked examples A–C from `design/turn-system.md` as tests.
