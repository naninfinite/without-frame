# Tech

Architecture, rendering setup, performance budget, folder layout and tooling. Changes here need a decision record.

## Architecture

The battle rules are a pure GDScript core with no nodes, scenes or rendering. Input becomes commands, the rules apply them and emit an event log, and the view plays the log back. See `decisions/ADR-004-rules-view-split.md`.

```mermaid
flowchart LR
    Input["Input<br/>keyboard, trackpad, touch"] --> Cmd["Commands<br/>move, act, wait, face"]
    Data[("Data<br/>jobs, abilities, units, laws, maps")] --> Rules
    Cmd --> Rules["Rules core<br/>battle state, clock, laws"]
    Rules --> Log["Event log"]
    Log --> View["View<br/>terrain, sprites, UI, effects"]
    View --> Screen["Screen 720×720"]
    Tests["Headless tests"] --> Cmd
    Log --> Tests
```

Consequences:

- Every rule can be tested without a display, in CI and by agents.
- A battle is reproducible from its seed plus its command list. Bugs are reported as seed + commands.
- Animation bugs can never change game state.

## The clock (one tick)

Order taken from FFT. Spec: `design/turn-system.md`.

```mermaid
flowchart TD
    A["Tick starts"] --> B["1. Status effects<br/>durations count down"]
    B --> C["2. Charged abilities<br/>each gauge += ability speed"]
    C --> D{"Any gauge ≥ 100?"}
    D -- yes --> E["Resolve them<br/>in queue order"]
    D -- no --> F
    E --> F["3. Units<br/>CT += Speed"]
    F --> G{"Any CT ≥ 100?"}
    G -- yes --> H["Those units take turns<br/>in unit order"]
    H --> A
    G -- no --> A
```

## One unit's turn

```mermaid
stateDiagram-v2
    [*] --> Choosing
    Choosing --> Moved: move
    Choosing --> Acted: act
    Choosing --> Facing: wait
    Moved --> MovedAndActed: act
    Moved --> Facing: wait
    Acted --> MovedAndActed: move
    Acted --> Facing: wait
    MovedAndActed --> Facing
    Facing --> [*]: CT -= 100 / 80 / 60
```

## Rendering

| Setting | Value | Why |
|---|---|---|
| Renderer | Mobile (Vulkan) | Reported to run well on the Pi 5; Compatibility gave poor editor performance in user reports. Confirm in SPIKE-01. |
| 3D resolution | 360×360 in a viewport, scaled 2× to 720×720 with nearest filtering | Crisp pixels, a quarter of the pixel work |
| Camera | Orthographic, 4 rotations in 90° steps | FFT look; rotation is a pillar |
| Sprites | Upright, face the camera, 1 sprite pixel = 1 viewport pixel | Crisp at any rotation |
| Lighting | One directional light, blob shadows, no SSAO, GI or volumetrics | Pi GPU budget |
| Texture filter | Nearest, everywhere | One consistent pixel style |

## Performance budget

| Item | Budget | Status |
|---|---|---|
| Frame rate in battle | 30fps sustained, including after 10 minutes of play | Measured in SPIKE-01 |
| Frame time | ≤ 33ms, 1% lows reported | SPIKE-01 |
| Draw calls, sprite count, map size | Set from SPIKE-01 results | Pending |

## Folder layout

| Path | Owner | Contents |
|---|---|---|
| `game/rules/` | `mech` | Pure battle rules. No nodes or rendering. |
| `game/view/` | `env` | Scenes, camera, terrain, sprite playback, UI (M1) |
| `game/input/` | `env` | Keyboard, trackpad and touch to commands |
| `data/` | `mech` (Balance later) | Jobs, abilities, units, laws as data files |
| `maps/` | `env` | Map files per `contracts/map-format.md` |
| `assets/` | `art` | Sprites, textures, UI art, audio |
| `tests/rules/` | `mech` writes, `qa` reviews | Rules tests, including every worked example |
| `tests/integration/` | `qa` | Scene and end-to-end tests |
| `tools/` | `env` (Tools later) | Scripts, checkers, deploy |
| `.github/` | `env` | CI workflows |
| `docs/`, `devlog/` | Director | Lanes edit only their own lane doc, handoffs, reports and changelog lines |

## Rules for all code

- **Strings:** all on-screen text goes through string tables. No literal UI text in code.
- **Randomness:** only through the battle's seeded random number generator in `game/rules/`.
- **Numbers:** in `data/`, never hard-coded.
- **Engine version:** pinned in M0-T01. Godot 4.6.2 is reported running well on a Pi 5; 4.7.x also exists. Check the current stable release and Pi reports before pinning.

## Testing

- GdUnit4, run headless locally and in a GitHub Action on every pull request (M0-T03).
- Every worked example in `docs/design/` becomes a test with the same numbers.
- Later: mutation testing (gdmutant) to check the tests actually catch bugs.

## Tooling

Filled in by M0-T05. Candidates, all to be read before installing and pinned to a version:

| Tool | Purpose |
|---|---|
| godot-mcp (slangwald) | Claude Code ↔ Godot editor and running game, screenshots |
| GDScript language server plugin (minami110 or twaananen) | Real errors for agents instead of guesses |
| One skill pack: GodotPrompter or awesome-gamedev-agent-skills | Godot-specific agent knowledge |
| pixel-art-mcp + Blender MCP | Sprite pipeline, pending SPIKE-02 |
