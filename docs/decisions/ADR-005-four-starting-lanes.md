# ADR-005: Start with four lanes; split only when it hurts

Status: Accepted
Date: 2026-10-05

## Context

A full studio-style roster was drafted (fifteen teams: Mechanics, Balance, Enemy AI, Environment, Art, Presentation, UI/UX, Story, Audio, Tech/Build, Tools, QA, Librarian, Producer, Director). Every lane adds a lane doc, handoffs, contracts, review overhead and usage cost. This is a hobby project, and the Director needs to keep up mentally.

## Decision

Start with four roles:

| Role | Callsign | Covers for now |
|---|---|---|
| Director | — | Vision, roadmap, decisions, contracts, playtests (naninfinite + Opus) |
| Engineers | `mech` | Mechanics, Balance, Enemy AI |
| Geomancers | `env` | Environment, view, UI, Tech/Build, Tools |
| Judges | `qa` | QA, playtest log, cards |

Art runs only as SPIKE-02 until the pipeline is proven. Other lanes are split off when a signal appears (`lanes/README.md`).

## Alternatives considered

- **Full roster from day one:** rejected; process overhead would replace the game.
- **One generalist agent:** rejected; no review separation and no ownership boundaries.

## Consequences

- Fewer handoffs and contracts in M0–M1.
- Engineers and Geomancers own broad areas, so their lane docs must stay tightly scoped to the current milestone.
- Splitting a lane needs a new ADR.
