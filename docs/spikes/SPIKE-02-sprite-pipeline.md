# SPIKE-02: Sprite pipeline

Owner: Director, with Art. Timebox: 2 sessions. Status: **not started**.

## Question

Can MCP-driven tools produce sprites that are consistent across every frame and both facings, look good on the Hackberry's screen, and take a sensible amount of time per character?

## Tools

- **pixel-art-mcp** (NNTin): Blender model → consistent views from set angles → transparent pixel sprites on a palette → packed sheet with metadata. Its container targets Linux x86-64, so it runs on the dev machine, not the Hackberry.
- **Blender MCP** (ahujasid, now "mcp-for-blender"): general modelling. By default it lets the agent run any Python inside Blender, so use it in a dedicated Blender project.

Before installing either: read the code and setup, pin the version, install at project scope only.

## Steps

1. Choose a master palette (start from an existing palette of up to 32 colours).
2. Build one low-poly character (e.g. a knight) in Blender through the MCP.
3. Render `idle`, `walk` and `attack` at the game's fixed camera angle, in both diagonal facings (front and back), at two candidate frame sizes: 24×32 and 32×40.
4. Export sheets and metadata per `contracts/sprite-spec.md`.
5. Drop them into the SPIKE-01 scene and view them **on the Hackberry** at all four camera rotations.

## Judge on

- Consistency: does the character read as the same person in every frame and facing?
- Readability at 720×720 on the real screen, at both sizes
- Style: would you put this in the game?
- Time per character, and how much hand-fixing was needed

## Pass criteria

The Director signs off: "I would ship this style." Time per character is acceptable to the Director.

## If it fails

Options for an ADR: the Director draws key sprites by hand with agents assembling sheets and metadata; image generation constrained by reference sheets; licensed or CC0 sprite packs as placeholders until the pipeline improves.

## Output

- Chosen frame size and palette size, which finalise `contracts/sprite-spec.md`
- Results below, with screenshots from the device in `devlog/media/`

## Results

*(to be written)*
