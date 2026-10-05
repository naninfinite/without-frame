# Roadmap

Milestones with definitions of done. Tasks are added here only at milestone planning. Mid-milestone ideas go to `PARKING-LOT.md`.

## M0: Setup and spikes

**Goal:** prove the risky assumptions and get the foundations running, before investing in features.

**Mode** (see `WORKFLOW.md` § Task modes): `agent` = an agent writes the code; `pair` = the Director writes the code, an agent guides and reviews; `director` = decision or doc work.

| ID | Lane | Mode | Task | Done when |
|---|---|---|---|---|
| M0-T01 | `env` | agent | Godot project init: pinned version, Mobile renderer, 3D in a 360×360 viewport scaled 2× with nearest filtering, folder layout from `TECH.md`, typed-GDScript warnings set to errors per `CODE-STANDARDS.md` | Empty project opens and runs on the Hackberry |
| M0-T02 | `env` | agent | Local device loop: one command to run the game, in-game perf overlay plus a logger writing FPS, frame time and draw calls to a file, and a capture key that saves a screenshot stamped with date, commit and battle seed (see `devlog/README.md`) | Director can run, read a perf log and grab a stamped screenshot, one command or key each |
| SPIKE-01 | `env` | agent | Device performance spike (`spikes/SPIKE-01-device-performance.md`) | Report written, pass or fail against its criteria |
| SPIKE-02 | Director + `art` | director | Sprite pipeline spike (`spikes/SPIKE-02-sprite-pipeline.md`) | Director signs off or rejects the pipeline |
| M0-T03 | `qa` | agent | Checks on every pull request: GdUnit4 headless, `gdlint` and `gdformat` with the limits in `CODE-STANDARDS.md`, `jscpd` duplicate detection over `game/` | A failing test, an over-long file and a duplicated block each block a pull request |
| M0-T08 | Director | director | Agree the rules-core module map (`MODULE-MAP.md`): classes, responsibilities, dependencies. Grill it before accepting. **No rules code before this is accepted.** | `MODULE-MAP.md` status is Accepted |
| M0-T04 | `mech` | pair (proposed) | Rules core skeleton exactly as the accepted module map: battle state, command input, event log output per `contracts/event-log.md`, with one passing test | Test passes headless, all checks pass, no class outside the module map |
| M0-T05 | Director + `env` | director | Agent tooling: Godot MCP server, GDScript language server plugin, Matt Pocock's skills (install or update, then run `setup-matt-pocock-skills` and reconcile its doc locations with ours), gdtoolkit, jscpd. Read each before installing, pin versions, project scope only, Linux ARM64 only | Tools listed in `TECH.md` § Tooling with versions |
| M0-T06 | `env` | agent | Repo guard checks in a GitHub Action on every pull request: (1) fail when a `<lane>/` branch touches paths outside that lane; (2) fail when any commit's author is not `naninfinite` with the noreply address, or a commit message contains a session link; (3) fail when a pull request changes more than the diff budget in `CODE-STANDARDS.md` | A test branch breaking each rule is blocked |
| M0-T07 | Director | director | Record spike outcomes as decision records (render scale, sprite size, renderer) | ADRs accepted, `TECH.md` and contracts updated |

**M0 is done when** both spikes pass (or the plan is changed by ADR), every task above is ticked, and the Director can run a build on the Hackberry and see a perf log.

## M1: One battle

**Goal:** a single battle that is fun to replay on the Hackberry. If this works, everything after is content.

Scope (broken into task IDs at M1 planning, each with a mode; the module map is extended and accepted before each new area of code):

- One 12×12 map with height, camera rotation in 90° steps, grid cursor and tile picking on raised terrain
- 4 player units against 5 enemies, 3 jobs (melee, ranged, caster), stats in data
- Full charge-time system per `design/turn-system.md`: move, act, wait, facing, charged spells
- Height and facing per `design/battle-basics.md`
- Turn queue with "where will my next turn land" preview, and a combat forecast box
- One law per `design/laws.md`: yellow and red cards, ejection from the battle (no jail campaign layer yet)
- Basic enemy AI that respects the law
- Visuals play back the event log with placeholder sprites and animations
- Victory and defeat

**M1 is done when** every worked example in the design specs is a passing test, the battle holds 30fps on the Hackberry, and the Director has played three full battles on the device and wants to play a fourth.

## Later (not planned)

Sketch only. Planned properly when M1 ends.

- **M2:** split Balance and Enemy AI lanes; real art through the pipeline; job system with ability learning; status effects; more laws
- **M3:** Story lane; campaign layer (missions, jail and bail); Audio lane
