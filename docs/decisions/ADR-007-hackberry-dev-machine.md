# ADR-007: The Hackberry is the development machine as well as the target

Status: Accepted
Date: 2026-10-05

## Context

The original plan assumed development on a separate machine with builds deployed to the Hackberry over SSH. The Director will develop on the HackberryPi CM5 itself, with a Mac possibly joining later.

## Decision

The Hackberry is the primary development machine. The Godot editor, the agents' command-line tools, the Godot MCP bridge, tests and the game all run on it. Builds run locally; there is no remote deploy step in M0.

## Alternatives considered

- **Separate dev machine, deploy to the device:** faster editor and agents, but not how the Director wants to work. Kept as an option if a Mac joins later.

## Consequences

- **M0-T02** becomes a local loop: run, perf overlay, perf logger, capture key. Remote deploy is dropped.
- **Shared resources.** Editor, game, MCP bridge and agents share four CPU cores and a passive heatsink. Work plugged in; expect throttling in long sessions.
- **Clean measurements.** Any performance measurement is taken with the editor closed and agents stopped.
- **Small screen.** The editor is cramped at 720×720. Prefer terminal and agent workflows; use an external monitor over HDMI or the editor's display scale for editor sessions.
- **Storage.** NVMe strongly preferred over an SD card for Godot's import cache and Git.
- **ARM64 tooling.** Every tool must run on Linux ARM64. pixel-art-mcp ships as an x86-64 container, so SPIKE-02 must run it elsewhere or find an ARM64 route.
