# SPIKE-01: Device performance

Owner: Geomancers. Timebox: 2 sessions. Status: **not started**.

## Question

Can the HackberryPi CM5 hold 30fps with our rendering setup (ADR-001) for a battle-sized scene, sustained, without overheating?

## Throwaway scene

Built on a spike branch (`env/SPIKE-01`), not merged.

- 12×12 block terrain with heights 0–6
- 10 upright placeholder sprites facing the camera (flat coloured quads are fine)
- Orthographic camera rotating 90° every 2 seconds, continuously
- 3D rendered in a 360×360 viewport, scaled 2× to 720×720 with nearest filtering
- One directional light, blob shadows, nothing else
- Perf overlay and logger from M0-T02

## Variants to measure

| Variant | Renderer | 3D resolution | Sprites |
|---|---|---|---|
| A (baseline) | Mobile | 360×360 | 10 |
| B | Compatibility | 360×360 | 10 |
| C (stress) | Mobile | 360×360 | 20 |
| D (fallback) | Mobile | 240×240, scaled 3× | 10 |

## Measure, 10 minutes each, on the device

- Average FPS and 1% lows, frame time
- Draw calls
- SoC temperature at start and end (`vcgencmd measure_temp`) and throttle flags (`vcgencmd get_throttled`)
- Battery percentage at start and end

## Pass criteria

Variant A holds **30fps or more for the full 10 minutes**, 1% lows above 25fps, and no throttle flags.

## If it fails

Try, in order: variant D's lower resolution, fewer terrain faces (merge blocks into larger meshes), the Compatibility renderer. If none pass, the Director revisits ADR-001 in a new ADR.

## Output

- A results section appended below, with a table of the four variants
- Raw perf logs in `docs/spikes/data/SPIKE-01/`
- A short screen capture or phone video of the device running variant A, for the devlog

## Results

*(to be written)*
