# ADR-006: FFTA-style laws with real punishments

Status: Accepted
Date: 2026-10-05

## Context

FFTA's judges and laws made battles distinctive: breaking a law had real consequences. FFTA2 softened them. The Director wants the original teeth back, without the frustrations (gotcha breaches, laws that made a battle unwinnable).

## Decision

Laws with real punishments: yellow card on the first breach, red card and ejection on the second, jail and bail in the later campaign layer. Made fair by: laws announced before deployment, a warning and second confirmation before any breach, and enemies bound by the same laws. M1 ships one law per battle. Spec: `design/laws.md`.

## Alternatives considered

- **FFTA2-style optional bonus conditions:** less frustrating but toothless. Rejected; it removes pillar 2.
- **Breach with no warning:** more punishing, but makes breaches feel like misreads. Rejected.

## Consequences

- Laws must be balanced so none makes a battle unwinnable. Balance simulations check this once the Balance lane exists.
- Enemy AI needs law awareness: M1 never breaks laws; M2 may gamble.
- Ejection must be handled everywhere a unit can leave the battle (victory, defeat, charging abilities).
