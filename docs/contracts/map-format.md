# Contract: map format

Status: **draft for M1**. Producer: Geomancers. Consumers: Engineers (rules), Judges (map checker).

Maps are data files in `maps/`, one per map.

## Coordinates

- Tiles are `[x, y]`. Origin `[0, 0]` is the north-west corner. `x` increases eastward, `y` increases southward.
- North is the `-y` direction. Facing values `n`, `e`, `s`, `w` use this compass.

## Fields

| Field | Type | Meaning |
|---|---|---|
| `id` | string | Stable map id |
| `name` | string key | String-table key, not literal text |
| `size` | `[w, h]` | Width and height in tiles. M1: `[12, 12]` |
| `tiles` | list of rows | Row-major, `h` rows of `w` tiles. Each tile: `height` (int ≥ 0) and `terrain` (see below) |
| `spawns` | dictionary | `player` and `enemy`, each a list of tiles |
| `camera_start` | int 0–3 | Starting rotation in 90° steps |

## Terrain (M1)

| Terrain | Walkable | Notes |
|---|---|---|
| `ground` | Yes | Default |
| `stone` | Yes | Visual variation only in M1 |
| `water` | No | Impassable in M1 |
| `void` | No | No tile; nothing drawn |

## Checks (map checker, Judges)

- Size matches the `tiles` array.
- Every spawn is on a walkable tile, with no duplicates.
- Every walkable tile is reachable from every spawn for a unit with Jump 3 (default M1 Jump; tunable).
- No height above the M1 maximum (set after SPIKE-01).
