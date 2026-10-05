# Vision

A tactics RPG for a pocket Linux handheld. The timing depth of Final Fantasy Tactics, the rule-bending of FFTA's laws, the clarity of Fire Emblem, sized for a 4" square screen and a BlackBerry keyboard.

## Pillars

Every feature must serve at least one pillar. If it serves none, it goes in `PARKING-LOT.md`.

1. **Every turn is a timing puzzle.** Charge time, charged spells, waiting and facing make *when* you act as important as *what* you do.
2. **Laws with teeth.** Each battle's laws are real constraints. Breaking them is a choice with consequences, for you and the enemy.
3. **Readable in your pocket.** Everything important is legible at 720×720 and playable from the keyboard alone.
4. **Made for the Hackberry.** It runs smoothly on the device and respects the battery. If it can't run well there, it doesn't ship.

## What it is not

- Not real-time. The clock never runs while you decide (see `decisions/ADR-003-atb-parked.md`).
- Not full 3D characters. Sprites on 3D terrain (see `decisions/ADR-001-sprites-on-3d-terrain.md`).
- Not a clone. Original world, characters, names and art. FFT, FFTA and Fire Emblem are references, not sources.
- Not huge. Small, well-made battles before breadth.

## Target device

| | |
|---|---|
| Hardware | HackberryPi CM5, Raspberry Pi CM5 with 16GB RAM, BCM2712 (4× Cortex-A76 at 2.4GHz) |
| Screen | 4" 720×720 touch display |
| Input | BlackBerry keyboard, trackpad, touch |
| Engine | Godot 4.x, Mobile renderer (exact version pinned in M0) |
| Target | 30fps in battle, 3D rendered at 360×360 and scaled 2× |
| Built on | The Hackberry itself (ADR-007) |
