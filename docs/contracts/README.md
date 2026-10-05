# Contracts

Formats that more than one lane builds to. Lanes never negotiate a format between themselves: they request a change from the Director, and any change needs a decision record.

| Contract | Producer | Consumers | Status |
|---|---|---|---|
| `event-log.md` | Engineers (rules) | Geomancers (view), Judges (tests) | Draft for M0-T04 |
| `map-format.md` | Geomancers | Engineers (rules), Judges (map checker) | Draft for M1 |
| `sprite-spec.md` | Art | Geomancers (view) | Draft, finalised after SPIKE-02 |

Later: dialogue and mission data (Story), ability and law data schema (Balance), UI string tables.
