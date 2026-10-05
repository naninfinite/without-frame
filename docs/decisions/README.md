# Decision records

Why things are the way they are. One file per decision. Never edited after acceptance; a change of mind is a new record that supersedes the old one and links back.

| ADR | Decision | Status | Date |
|---|---|---|---|
| [001](ADR-001-sprites-on-3d-terrain.md) | FFT-style 2D sprites on 3D terrain, with camera rotation | Accepted | 2026-10-05 |
| [002](ADR-002-fft-charge-time.md) | FFT charge-time turn system | Accepted | 2026-10-05 |
| [003](ADR-003-atb-parked.md) | ATB not adopted; parked | Accepted | 2026-10-05 |
| [004](ADR-004-rules-view-split.md) | Battle rules separate from visuals, joined by an event log | Accepted | 2026-10-05 |
| [005](ADR-005-four-starting-lanes.md) | Start with four lanes; split only when it hurts | Accepted | 2026-10-05 |
| [006](ADR-006-laws-with-teeth.md) | FFTA-style laws with real punishments | Accepted | 2026-10-05 |
| [007](ADR-007-hackberry-dev-machine.md) | The Hackberry is the development machine as well as the target | Accepted | 2026-10-05 |
| [008](ADR-008-code-standards-and-module-map.md) | Strict code standards and a module map before any code | Accepted | 2026-10-05 |
| [009](ADR-009-pair-mode.md) | Pair mode, where the Director writes some of the code | Accepted | 2026-10-05 |

## Template

```
# ADR-NNN: <title>
Status: Proposed | Accepted | Superseded by ADR-NNN
Date: yyyy-mm-dd

## Context
What forced the decision.

## Decision
What we chose.

## Alternatives considered
What else, and why not.

## Consequences
What this makes easier, harder, or rules out.
```
