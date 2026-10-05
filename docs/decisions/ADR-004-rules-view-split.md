# ADR-004: Battle rules separate from visuals, joined by an event log

Status: Accepted
Date: 2026-10-05

## Context

The game is built largely by agents. Agents work best when they can verify their own work, and they cannot see the Hackberry's screen. Godot scene files also merge badly when several lanes touch them.

## Decision

The battle rules live in a pure GDScript core (`game/rules/`) with no nodes, scenes or rendering. Input becomes commands; the rules apply them and append to an event log (`contracts/event-log.md`). The view (`game/view/`) only plays the log back. All randomness comes from a seeded generator in the rules.

## Alternatives considered

- **Rules inside scene nodes (typical Godot style):** faster to start, but untestable without a display and tangles lanes together. Rejected.

## Consequences

- Every rule is testable headless, by agents and in CI. Worked examples in the specs become tests.
- Battles are reproducible from seed + commands, so bugs are reported that way.
- Animation bugs cannot change game state.
- The view lane can work in parallel against the event log contract.
- Slightly more upfront structure than a quick prototype.
