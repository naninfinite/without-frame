# ADR-003: ATB not adopted; parked

Status: Accepted
Date: 2026-10-05

## Context

Active Time Battle (FF IV–IX) was considered in two forms on top of FFT's charge time:

1. **Real-time clock:** the clock keeps running while the player decides.
2. **Weighted turn costs:** each action costs time by its weight (e.g. base 40, +6 per tile moved, dagger 30, sword 50) instead of a flat 100/80/60.

FFT's charge time is itself a descendant of ATB with the clock paused while you decide; both were designed by Hiroyuki Ito.

## Decision

Neither is adopted. The game uses FFT's charge time as specified (ADR-002). Both variants are kept in `PARKING-LOT.md`.

## Alternatives considered

- **Real-time clock as default:** rejected. On a 4" screen with a BlackBerry keyboard, reading height, facing and the turn queue takes seconds; with the clock running, a Fire spell lands before the player can commit a dodge, turning FFT's best tactical moment into a reflex test.
- **Weighted costs now:** not rejected outright, but it adds numbers to track and balancing work before the core is proven.

## Consequences

- Possible future returns: a "swift judgement" law where the clock runs for one battle; an optional Active setting; weighted costs as an experiment after M1 (costs are data, so it's cheap).
- Animated charge gauges between turns can give an ATB look with no gameplay change (parking lot).
