# ADR-009: Pair mode, where the Director writes some of the code

Status: Accepted
Date: 2026-10-05

## Context

Agents can write the code faster, but the Director wants to write some of it by hand, with AI as a guide, for learning and for fun.

## Decision

Every task has a mode: `agent` (an agent writes), `pair` (the Director writes; an agent guides, explains and reviews but never edits code files), or `director` (no game code). Pair tasks may sit in any lane's paths; the Director writes there under that lane's rules. The `teach` skill supports learning sessions. Pair tasks get the same standards, review and task report as any other.

## Alternatives considered

- **Agents write everything:** faster, but loses the point of the project for the Director.
- **The Director writes in separate side projects:** keeps the main codebase agent-only, but the learning wouldn't be on the real game.

## Consequences

- Pair tasks will take longer; they are chosen for being small, central and educational.
- Agents must check a task's mode before acting. Writing code in a pair task is a red card.
- The first proposed pair task is M0-T04, the rules core skeleton.
