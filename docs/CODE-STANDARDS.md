# Code standards

Status: **Accepted** (ADR-008). Applies to every line of GDScript, whether an agent or the Director writes it. Judges enforce it in review; the checks in M0-T03 and M0-T06 enforce what can be automated.

## 1. Boundaries before code

- **No class exists until it is in `MODULE-MAP.md`**, with its one-sentence responsibility, owning lane, folder and allowed dependencies. The Director accepts map changes before any code is written.
- Agents implement **inside** the map. They never invent classes, autoloads, folders or addons. If a task seems to need one, the agent stops and proposes a map change.
- Dependencies only point the ways the map allows. No cycles.

## 2. Object-oriented, the Godot way

1. **One class per file.** Every script declares `class_name`. File names are `snake_case` versions of the class name.
2. **One responsibility per class.** If its purpose can't be said in one sentence without "and", split it. That sentence goes in the module map and the class's `##` doc comment.
3. **Rules code is plain objects.** Classes in `game/rules/` extend `RefCounted` (or `Resource` for data). Never `Node`.
4. **Composition over inheritance.** Inherit only for a genuine "is a" with shared behaviour, e.g. command types. At most two levels below a Godot base class.
5. **Encapsulation.** State is private (`_name`) and changed only through the owning class's methods. No reaching into another object's internals.
6. **Dependencies are passed in,** through `_init` or a setup method, never fetched globally. Autoloads exist only if listed in the module map, and never in `game/rules/`.
7. **Polymorphism over type checks.** No `if x is A … elif x is B` chains; put the behaviour on the class.
8. **Rules talk to the outside only through the event log** (ADR-004). The view uses signals among its own nodes.

## 3. Typed GDScript

- Static types on every variable, parameter and return value. `:=` is fine when the type is obvious from the right-hand side.
- Typed arrays and typed dictionaries.
- Project settings (set in M0-T01, names confirmed against the pinned Godot version): the GDScript warnings `untyped_declaration`, `unsafe_property_access`, `unsafe_method_access`, `unsafe_cast` and `unsafe_call_argument` are raised to **Error**.

## 4. Hard size limits

| Limit | Maximum | Enforced by |
|---|---|---|
| File length | 300 lines including comments (aim for 200) | `gdlint` `max-file-lines` |
| Line length | 100 characters | `gdlint` `max-line-length` |
| Parameters per function | 4 (group more into a small typed class) | `gdlint` `function-arguments-number` |
| Public methods per class | 10 | `gdlint` `max-public-methods` |
| Function body | 30 lines | Review now; a Tools-lane script later |
| Nesting depth | 3 levels | Review now; a Tools-lane script later |
| Pull request size | 400 changed lines of code, excluding tests, data and docs | M0-T06 check |

Hitting a limit is a design signal: split the class and update the module map. Never squeeze code to fit.

## 5. No duplication

- **Search before writing.** Before adding a function, search the codebase (language server or `grep`) for existing behaviour, and reuse or extract it.
- **Any duplicated block in `game/` fails the checks** (`jscpd`, minimum 5 lines or 50 tokens). Test helpers live in `tests/helpers/`.
- Shared logic lives in exactly one class, named in the module map.

## 6. No bloat

- Build only what the task's acceptance criteria need. No speculative options, hooks or "for later" code.
- No dead code, no commented-out code, no `TODO` without a task ID.
- No new addons or libraries without a decision record.
- Task reports state net lines added and removed. Deleting code is a good outcome.

## 7. Style

- The Godot GDScript style guide, formatted by `gdformat`: `snake_case` functions and variables, `PascalCase` classes, `CONSTANT_CASE` constants, signals named in the past tense.
- British English in comments and doc comments. API identifiers keep their own spelling (`Color`).
- Comments explain *why*, not *what*.
- Every class has a `##` doc comment with its one-sentence responsibility.

## 8. Tests

- Every public method in `game/rules/` is covered by a test. Test names describe behaviour.
- Every worked example in `docs/design/` is a test with the same numbers.

## 9. Review checklist (Judges)

- [ ] Every new class is in `MODULE-MAP.md`, and its code matches its stated responsibility
- [ ] Dependencies only point the ways the map allows
- [ ] Fully typed; checks green (tests, `gdlint`, `gdformat`, `jscpd`)
- [ ] Size limits respected, including function length and nesting
- [ ] Nothing beyond the acceptance criteria
- [ ] Pair-mode tasks: the code was written by the Director

**Cards:** a size-limit or duplication breach is a yellow card. A class or autoload outside the module map, rules code depending on the view, or a broken dependency rule is a red card.
