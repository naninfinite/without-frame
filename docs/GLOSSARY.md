# Glossary

One meaning per term. If a doc uses a term differently, the doc is wrong.

## Battle

| Term | Meaning |
|---|---|
| **Tick** | One step of the battle clock. Everything in the turn system advances in ticks. |
| **CT (charge time)** | A unit's turn gauge. Rises by the unit's Speed each tick. The unit takes a turn at 100 or more. |
| **Speed** | Unit stat. CT gained per tick. |
| **Turn cost** | CT removed at the end of a turn: 100 for move and act, 80 for one of them, 60 for wait. |
| **Wait** | Ending a turn without moving or acting, or after doing only one. Also when facing is chosen. |
| **Charged ability** | An ability that resolves some ticks after it is declared, e.g. Fire. |
| **Ability speed** | How fast a charged ability's own gauge fills per tick. Independent of the caster's Speed. |
| **Tile target / unit target** | A tile-targeted charged ability hits whatever is on that tile when it resolves; a unit-targeted one follows the unit. |
| **Facing** | The direction a unit faces. Attacks from the side or back are stronger. |
| **Height** | A tile's elevation in height units. Limits movement (Jump) and affects ranged attacks. |
| **Jump** | Unit stat. Maximum height difference a unit can climb or drop in one step. |
| **Turn queue** | The on-screen list of upcoming turns and charged-ability resolutions. |
| **Forecast** | The on-screen preview of an action's hit chance and damage before confirming. |

## Laws

| Term | Meaning |
|---|---|
| **Judge** | The battle's referee. Announces the laws and issues cards. |
| **Law** | A rule for one battle forbidding a category of action, e.g. "No fire". |
| **Yellow card** | First breach of a law in a battle. A warning. |
| **Red card** | Second breach. The unit is ejected from the battle. |
| **Ejection** | The red-carded unit leaves the battlefield for the rest of the battle. |
| **Jail / bail** | Campaign layer (M3+): ejected units go to jail between battles. |

## Project

| Term | Meaning |
|---|---|
| **Lane** | A team of agents that owns a set of paths, e.g. Engineers own `game/rules/`. |
| **Service role** | A role that reviews or checks but owns no game files, e.g. Judges. |
| **Shift change** | Routine handover to a fresh agent at ≥ 50% context, via a handoff document. |
| **Card (agent)** | Yellow: minor breach, noted. Red: agent fired, incident note written. |
| **Handoff** | The document one shift writes for the next. |
| **Event log** | The list of events the battle rules emit. The only thing the visuals read. |
| **Contract** | A format two or more lanes build to, in `docs/contracts/`. |
| **ADR** | Architecture/design decision record, in `docs/decisions/`. |
| **Spike** | A short, timeboxed experiment to test a risky assumption. |
| **Parking lot** | Where ideas wait until a milestone planning session. |
