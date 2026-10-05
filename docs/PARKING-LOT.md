# Parking lot

Every idea that is not in the current milestone. Triaged weekly by the Director. Entries are promoted into `ROADMAP.md` at milestone planning, or rejected with a one-line reason.

Format: **Idea** (date, who): one line. Pillar it serves. Status.

## Turn system

- **Real-time ATB clock** (2026-10-05, Director): the clock keeps running while the player decides, as in FF IV–IX. Rejected as the default: it turns charged-spell dodging into a reflex test and fights the small screen and keyboard. See `decisions/ADR-003-atb-parked.md`. Could return as a battle law ("swift judgement": the clock runs in this battle) or an optional Active setting. Pillars 1, 2. **Parked.**
- **ATB-style weighted turn costs** (2026-10-05, Director): replace FFT's flat 100/80/60 costs with costs from base + tiles moved + action weight (e.g. base 40, +6 per tile, dagger 30, sword 50), so short moves and light weapons buy tempo. Same idea as FFX's turn system. Costs are data, so this is a cheap experiment after M1. Pillar 1. **Parked: candidate experiment after M1.**
- **ATB gauges as visuals only**: animate everyone's charge gauge filling between turns. No gameplay change. Pillar 3. **Parked: candidate for M1 polish.**

## Laws

- **Law cards and antilaws** (FFTA): players can add or cancel laws. Pillar 2. **Parked: M2+.**
- **Jail and bail** campaign layer: red-carded units go to jail between battles; pay bail or sit out missions. Pillar 2. **Parked: M3 with the campaign layer.**
- **Judge points and combos** for following recommended actions. Pillar 2. **Parked: M2.**

## Camera and visuals

- **Two tilt angles** for the camera, as in FFT. Pillar 3. **Parked.**
- **See-through tall tiles** near the cursor. Pillar 3. **Parked: only if the silhouette outline isn't enough.**

## Content and structure

- **Optional permadeath**, Fire Emblem style. Pillar 1. **Parked: needs a campaign first.**
- **Japanese localisation.** All on-screen text goes in string tables from day one (`TECH.md`), so this stays cheap. **Parked.**

## Lanes

- Lanes not yet staffed and the signal that splits each one off: see `lanes/README.md`.
