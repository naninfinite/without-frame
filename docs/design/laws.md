# Laws

Status: **draft for M1** (one law, cards and ejection only). Owner: Engineers (rules), Director (law design). Numbers marked *tunable* live in `data/`.

## Intent

Each battle has rules you can break, at a real cost. Laws create decisions FFT alone doesn't: do you use your best attack and risk a card, or play around the law? Punishments have teeth, like FFTA, not the softened FFTA2 version. They are always fair: you know the law before the battle and are warned before breaking it. (Pillar 2.)

## Rules

### Judges and laws

1. Every battle has a judge. The judge announces the battle's laws before deployment, and they stay visible in the battle info screen.
2. A law forbids one **category** of action *(data)*:

   | Category | Example law |
   |---|---|
   | Element | No fire |
   | Action type | No ranged attacks; no magic; no items |
   | Weapon type | No swords |
   | Target condition | No attacking a unit from behind |

3. M1 battles have **one** law. Later battles may have more.
4. Laws apply to **both sides**. Enemies can be carded and ejected too.

### Breaking a law

5. When a player selects an action that breaks a law, the game warns them and asks for a second confirmation. Breaking a law is always a choice, never a misread.
6. For a charged ability, the law is checked when it is **declared**, not when it resolves.
7. The action still happens. The card is issued after it resolves.
8. Each unit's breaches are counted for the whole battle, across all laws:

   | Breach | Card | Effect |
   |---|---|---|
   | 1st | Yellow | Warning, shown on the unit |
   | 2nd | Red | Unit is **ejected** once the action resolves |

9. An ejected unit leaves the battlefield for the rest of the battle. Its charging abilities are cancelled, and it gains no CT. It counts as out for victory and defeat, but it is not knocked out.
10. Victory: every enemy is knocked out or ejected. Defeat: every player unit is knocked out or ejected.

### Enemy AI and laws

11. M1 enemy AI never breaks a law. From M2, law-aware AI may deliberately risk a yellow card when the payoff is high.

## Worked example

Law: **No fire.** A player's Black Mage has Fire and Blizzard.

| Step | What happens |
|---|---|
| 1 | Black Mage selects Fire. Warning: "Fire breaks today's law (no fire). Confirm?" Player confirms. |
| 2 | Fire is declared and charges normally. When it resolves, the judge issues a **yellow card** to the Black Mage. |
| 3 | Next turn the Black Mage casts Blizzard. Legal; no card. |
| 4 | Later, the Black Mage casts Fire again and confirms the warning. When it resolves, the judge issues a **red card**. The Black Mage is ejected. |

## Edge cases

- An area attack that hits a target the law protects is a breach, even if the main target was legal.
- A breach by a charged ability is issued after resolution. If the caster is knocked out before resolution, the ability is cancelled and no card is issued.
- Cards do not carry over between battles (until the M3 campaign layer decides otherwise).

## Tunables (`data/`)

Breaches per red card (2), the law list and categories, which laws can appear on which maps.

## Open questions

- Reward for keeping the law: FFTA-style judge points feeding special moves. (Parked for M2.)
- Law cards and antilaws, to add or cancel laws. (Parked for M2+.)
- Jail and bail after a red card. (Parked for M3, campaign layer.)
- Should some laws forbid moves, e.g. "no climbing"? Interesting with height. Decide at M2 planning.
