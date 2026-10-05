# Turn system (charge time)

Status: **accepted for M1** (ADR-002). Owner: Engineers. Numbers marked *tunable* live in `data/`.

## Intent

Make *when* you act as important as *what* you do. Fast units act more often, waiting buys an earlier next turn, and charged spells let both sides set traps and dodge them. (Pillar 1.)

## Rules

### The clock

1. All units start the battle at CT 0. Knocked-out and ejected units do not gain CT.
2. The battle advances one tick at a time. Each tick runs three steps in order:
   1. **Status effects:** durations count down (status effects arrive in M2).
   2. **Charged abilities:** each charging ability's gauge rises by its ability speed. Any gauge at 100 or more resolves now, in the order the abilities were declared.
   3. **Units:** every active unit's CT rises by its Speed. Every unit at CT 100 or more takes a turn, in unit order.
3. CT can go above 100. The excess carries over.
4. **Unit order** is fixed at battle start: enemies first, then players, each in deployment order. *(Our choice, tunable. FFT also broke ties by a fixed unit list.)*

### A turn

5. On its turn a unit may **move** once and **act** once, in either order, and may end the turn early with **wait**.
6. At the end of every turn the unit chooses its **facing**.
7. **Turn cost** is subtracted from CT when the turn ends:

   | The unit… | Cost *(tunable)* |
   |---|---|
   | moved and acted | 100 |
   | only moved, or only acted | 80 |
   | did neither | 60 |

8. After subtracting, CT is **capped at 60**.

### Charged abilities

9. Declaring a charged ability uses the unit's act. Its gauge starts at 0.
10. Each ability has an **ability speed** *(data)*. It is not affected by the caster's Speed. Example: speed 25 resolves on the 4th tick after declaration.
11. Each ability is either **tile-targeted** (hits whatever stands on the target tiles when it resolves) or **unit-targeted** (follows the target unit) *(data)*.
12. If the caster's turn comes while it is still charging, it may **wait** to keep charging. Moving or acting cancels the charge.
13. While charging, a unit **cannot evade** and takes **50% more physical damage** *(tunable)*.
14. If the caster is knocked out or ejected, its charging ability is cancelled.

### The turn queue

15. The turn queue shows upcoming unit turns and charged-ability resolutions in the order they will happen.
16. While choosing an action, the queue previews where the unit's next turn lands for "move and act", "one of them" and "wait".

## Worked examples

These become tests with the same numbers (`tests/rules/`).

### Example A: when does a unit first act?

A Knight with Speed 8 starts at CT 0. After tick 12 its CT is 96; after tick 13 it is 104. **It takes its first turn on tick 13** with CT 104.

### Example B: turn cost and the cap

- Knight at CT 104 moves and acts: 104 − 100 = **4**.
- Knight at CT 104 only moves: 104 − 80 = **24**.
- Knight at CT 104 waits: 104 − 60 = **44**.
- A unit at CT 130 waits: 130 − 60 = 70, **capped to 60**.

### Example C: dodging a charged Fire

Setup: Knight (Speed 8, CT 0), Archer (enemy, Speed 7, CT 0), Mage (enemy, Speed 6, CT 40). Fire has ability speed 25, tile-targeted, hitting its target tile and the four adjacent tiles.

| Tick | What happens |
|---|---|
| 10 | Mage reaches CT 100. Declares Fire on the Knight's tile (acted only): CT 100 − 80 = 20. |
| 11–13 | Fire gauge: 25, 50, 75. |
| 13 | Knight reaches CT 104 and takes a turn. The queue shows Fire resolving on tick 14. |
| 14 | Fire gauge reaches 100 and resolves on its tiles. |
| 15 | Archer reaches CT 105 and takes a turn. |

The Knight's three options on tick 13:

| Choice | Fire on tick 14 | Knight's CT after | Next Knight turn |
|---|---|---|---|
| Move 2+ tiles out of the area, then attack | Misses | 4 | Tick 25 (CT 100) |
| Move out of the area only | Misses | 24 | Tick 23 (CT 104) |
| Wait in place | **Hits the Knight** | 44 | Tick 20 (CT 100) |

The Mage's next turn is tick 24 (20 + 14 × 6 = 104).

## Edge cases

- Two charged abilities resolving on the same tick resolve in declaration order.
- A unit-targeted ability whose target is knocked out before resolution fizzles.
- A unit ejected by a red card while charging loses its charge (rule 14).
- A tile-targeted ability hits allies and enemies alike on its tiles.

## Tunables (`data/`)

Turn costs (100/80/60), CT cap after a turn (60), CT to act (100), charging damage multiplier (1.5), each ability's speed and targeting, unit Speed.

## Open questions

- Should some battles start with uneven CT, e.g. ambushes? (M2+)
- Status effects that change CT (Haste, Slow, Stop, Quick) arrive in M2. FFT-style values are Haste ×1.5, Slow ×0.5, Stop freezes CT and charges, Quick sets CT to 100. Confirm when M2 is planned.
- Can a unit undo a move before acting, as FFT allows? Proposed yes. Decide in M1 UI work.
