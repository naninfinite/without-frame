# Contract: event log

Status: **draft for M0-T04**. Producer: Engineers. Consumers: Geomancers (view playback), Judges (tests).

The battle rules emit an ordered list of events. The view reads only this list; it never inspects or changes battle state directly. Tests assert on this list.

## Event shape

Every event has:

| Field | Type | Meaning |
|---|---|---|
| `seq` | int | Position in the log, starting at 0 |
| `tick` | int | Clock tick when it happened |
| `type` | string | One of the types below |
| `data` | dictionary | Type-specific fields |

Units are referred to by a stable `unit_id` string. Tiles are `[x, y]` (see `map-format.md`).

## Event types (M1)

| Type | Data |
|---|---|
| `battle_started` | `seed`, `map_id`, `laws` (list of law ids), `units` (initial state) |
| `turn_started` | `unit_id`, `ct` |
| `unit_moved` | `unit_id`, `path` (list of tiles) |
| `ability_declared` | `unit_id`, `ability_id`, `target` (tile or unit), `charged` (bool) |
| `charge_cancelled` | `unit_id`, `ability_id`, `reason` |
| `ability_resolved` | `ability_id`, `caster_id`, `affected` (list of unit ids) |
| `attack_hit` | `attacker_id`, `target_id`, `damage`, `side` (`front`/`side`/`back`) |
| `attack_missed` | `attacker_id`, `target_id`, `side` |
| `unit_ko` | `unit_id` |
| `law_warning` | `unit_id`, `law_id` (emitted when a player confirms a breach) |
| `card_issued` | `unit_id`, `law_id`, `card` (`yellow`/`red`) |
| `unit_ejected` | `unit_id` |
| `facing_set` | `unit_id`, `facing` (`n`/`e`/`s`/`w`) |
| `turn_ended` | `unit_id`, `moved` (bool), `acted` (bool), `ct_after` |
| `battle_ended` | `result` (`victory`/`defeat`) |

## Rules

- Events are appended, never edited or removed.
- The same seed plus the same command list must produce an identical log.
- Adding a field is a minor change (note in the changelog). Renaming or removing a type or field needs a decision record.
