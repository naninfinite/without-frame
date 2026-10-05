# ADR-001: FFT-style sprites on 3D terrain, with camera rotation

Status: Accepted
Date: 2026-10-05

## Context

The game targets the HackberryPi CM5, whose Raspberry Pi GPU is weak. Camera rotation is a must-have: it is half of what makes FFT's battles feel like FFT, and it solves units hidden behind terrain.

## Decision

3D block terrain built from map data, with 2D sprite characters that always turn to face the camera, as in FFT. Orthographic camera rotating in 90° steps. 3D rendered at 360×360 and scaled 2× with nearest filtering. Characters drawn in two diagonal facings, mirrored to make four.

## Alternatives considered

- **Pure 2D isometric (FFTA style):** cheapest and most GBA-faithful, but no rotation, harder height rendering and tile picking. Rejected because rotation is required.
- **Full 3D characters:** rigging and animation workload too high, and too heavy for the GPU. Rejected.

## Consequences

- Height, rotation and tile picking come almost for free from the 3D terrain.
- Art workload is two drawn facings per animation.
- Needs a silhouette outline for units behind terrain.
- The 360×360 render must be confirmed on the device (SPIKE-01).
