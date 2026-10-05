# Contract: sprite spec

Status: **draft, finalised after SPIKE-02**. Producer: Art. Consumer: Geomancers (view).

## Facings

- Two facings are drawn per animation: **front-diagonal** and **back-diagonal**.
- They are mirrored horizontally to make all four on-screen facings. The view picks the frame from the unit's facing relative to the current camera rotation.

## Animations (M1)

| Animation | Loops | Frames |
|---|---|---|
| `idle` | Yes | Set in SPIKE-02 |
| `walk` | Yes | Set in SPIKE-02 |
| `attack` | No | Set in SPIKE-02 |
| `cast` | Yes, while charging | Set in SPIKE-02 |
| `hit` | No | Set in SPIKE-02 |
| `ko` | No, holds last frame | Set in SPIKE-02 |

## Format

- Frame size: **set in SPIKE-02**. Candidates at the 360×360 render: 24×32 or 32×40 pixels.
- Pivot: bottom centre, at the feet.
- Transparent background. No anti-aliasing. Colours only from the shared master palette (size set in SPIKE-02).
- One sprite sheet per character plus a metadata file listing animations, frame order and timing.
- Naming: `assets/sprites/<character_id>/<character_id>.png` and `<character_id>.json`.

## Checks (asset checker, Judges)

Frame size, palette compliance, every required animation present for both facings, pivot set, naming correct.
