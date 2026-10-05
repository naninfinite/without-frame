# Battle basics: grid, height, facing, forecast

Status: **draft for M1**. Owner: Engineers (rules), Geomancers (maps and display). Numbers marked *tunable* live in `data/`. Exact formulas are set during M1 and recorded here before they are coded.

## Intent

The battlefield itself is a tactical resource. High ground, flanks and backs reward thinking about position, and the forecast makes every outcome readable before you commit. (Pillars 1 and 3.)

## Rules

### Grid and height

1. The battlefield is a square grid. M1 uses one 12×12 map.
2. Each tile has a **height** in whole units *(map data)*. One unit of height is half a block visually.
3. A unit moves up to its **Move** stat in tiles per turn, around obstacles and units.
4. A unit can step between adjacent tiles only if the height difference is at most its **Jump** stat, going up or down.
5. Units cannot end a move on an occupied tile. They may pass through allies but not enemies *(tunable)*.

### Ranged attacks and height

6. Ranged attacks gain range when shooting down and lose it shooting up *(formula tunable, set in M1)*.

### Facing

7. Every unit faces one of four directions, chosen at the end of its turn.
8. Attacks are classed by where they land relative to the target's facing: **front**, **side** or **back**.
9. Side and back attacks are more likely to hit *(tunable modifiers, set in M1)*.

### Forecast

10. Before confirming an action, the forecast shows: hit chance, expected damage, the target's remaining HP, any law it would break, and where the unit's next turn would land in the queue.

## Worked examples

### Example A: climbing

A unit with Jump 3 stands on a height-1 tile. It can step to an adjacent height-4 tile (difference 3) but not to a height-5 tile (difference 4). From the height-4 tile it can step down to height 1, since the drop is also 3.

### Example B: facing

A target faces north. An attacker standing directly south of it hits its **back**. An attacker standing east or west hits its **side**. An attacker standing north hits its **front**.

## Open questions

- Damage formula for M1: keep it simple and data-driven. To be written here before Engineers code it.
- Exact hit modifiers for side and back attacks.
- Ranged height formula.
- Should falling from a height cause damage? (Parked unless a law or map needs it.)
