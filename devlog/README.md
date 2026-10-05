# Devlog

The human record of building this game: what happened, what was decided, what it looked like, and how it felt. The docs say what is true now; the devlog says how we got here.

## Structure

```
devlog/
  day-001-2026-10-05.md
  day-002-<date>.md
  media/
    day-001/
    day-002/
```

- A **day** is a working day on the project, not a calendar day. Skip days freely; the number only goes up when work happens.
- One markdown file per day, with that day's media in `media/day-NNN/`.

## Entry template

```
# Day NNN: <short title>
<yyyy-mm-dd> · Milestone: <M0/M1…>

## Set out to
## What happened
## Decisions
(link ADRs)
## Surprises and lessons
## The agents
(which lanes worked, any cards or firings)
## Pictures
## How it felt
## Next
```

## The routine

1. **During the session,** save captures into `media/day-NNN/` as you go. Name them `HHMM-<what>.<ext>`, e.g. `1432-first-rotation.webm`.
2. **At the end,** ask an agent to draft the entry from `git log`, `docs/CHANGELOG.md`, task reports and the captures in the folder. It writes facts only.
3. **You edit it into your own voice** and add "How it felt". That part is yours; agents shouldn't write it.
4. Commit the entry with the day's last commit.

## Capturing

| What | Tool | Notes |
|---|---|---|
| In-game screenshot | Capture key (M0-T02) | Saves a PNG stamped with date, commit and battle seed, so any picture can be reproduced |
| Clean gameplay video | Godot Movie Maker mode (`--write-movie`) on the dev machine | Renders every frame at a fixed rate, not in real time, so the video is perfectly smooth whatever the hardware |
| Quick on-device video | `wf-recorder` on the Hackberry | Works with Pi OS's Wayland desktop. The Pi 5 chip has no hardware H.264 encoder, so recording costs CPU and lowers FPS. Never record during a perf measurement |
| "It runs on the Hackberry" | Your phone, filming the device in hand | Often the most honest and nicest-looking shot |
| Agents at work | `asciinema` | Records terminal sessions as small text files that replay in a browser |
| Mission control, PRs, diagrams | Normal screenshots | |

## Keeping the repo light

- Compress video before committing: 720px or smaller, 20 seconds or less, WebM or MP4 (`ffmpeg`).
- Video and large images go through **Git LFS** (`.gitattributes` is set up). Run `git lfs install` once per machine. GitHub's free LFS quota is limited, so check it.
- Long recordings (full sessions, playthroughs) go in a GitHub Release per milestone, or in your own storage, with a link from the entry.

## Later

The devlog can become a public page (GitHub Pages, or your portfolio site) at any point, since it's already markdown with media.
