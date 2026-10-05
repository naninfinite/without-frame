# ADR-002: FFT charge-time turn system

Status: Accepted
Date: 2026-10-05

## Context

The turn system defines how battles feel. Options were Fire Emblem-style phases (whole army moves, then the enemy), FFTA-style individual turns ordered by speed with instant abilities, or FFT's charge time with charged abilities.

## Decision

FFT's charge time, faithfully: CT rises by Speed each tick, units act at 100, turn costs of 100/80/60 with leftover capped at 60, charged abilities with their own speed, and tile- versus unit-targeting. Paired with FFTA's readability: an always-visible turn queue with a next-turn preview. Spec: `design/turn-system.md`.

## Alternatives considered

- **Fire Emblem phases:** simpler, less UI, easier AI, but loses speed and charged-spell timing. Rejected.
- **FFTA turns:** speed-based but abilities resolve instantly, losing FFT's timing play. Rejected.
- **ATB:** see ADR-003.

## Consequences

- Deep timing decisions, matching pillar 1.
- The turn queue and its preview are essential UI, not polish.
- Turn costs are data, so variants (e.g. weighted costs) can be tested later without code changes.
