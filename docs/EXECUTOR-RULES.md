# Executor rules

Hard rules for any agent that writes to this repo. New rules come from incident notes (`docs/incidents/`). Pruned at each milestone end so the list stays short.

1. Follow the read order in `AGENTS.md`. Do not skim the whole `docs/` tree.
2. Cite the spec section you implement. If no spec section covers it, stop and ask.
3. Write only inside your lane's owned paths.
4. Battle rules never depend on visuals. Code under `game/rules/` must not reference nodes, scenes or rendering.
5. Visuals never change game state. They only read the event log.
6. No magic numbers in code. Tunable values live in `data/`.
7. Never edit, skip or delete a test to make it pass. Report the disagreement instead.
8. Never invent a Godot API. If unsure a method exists in the pinned version, check the docs or the language server before using it.
9. Run the relevant tests before reporting done, and paste the result into the report.
10. A spec that contradicts another doc is a stop condition, not a judgement call.
11. Update your lane § Now and `CHANGELOG.md` before ending a shift.
12. Write British English everywhere (`AGENTS.md` § Project rules, rule 1).
13. Never write the owner's real name anywhere. Use "naninfinite" or "the Director".
14. Commit as `naninfinite` with the GitHub noreply address. Claude's `Co-Authored-By` trailer is fine; session links are not.

## Rules added from incidents

None yet.
