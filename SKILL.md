---
name: thinking-toolkit
description: Six critical-thinking lenses for when reasoning stalls - invert a core assumption, collide two unrelated domains, extract the pattern behind 3+ examples, pressure-test at extreme scale, collapse special cases into one rule, or trace an idea's lineage before replacing it. Use when a decision feels forced into a single path, when solutions feel incremental, when complexity keeps growing, or before rewriting something that looks wrong.
---

# Critical Thinking Toolkit

Six lenses for a stuck mind. Each is a frame-shift you apply on purpose, not a mood you wait for.

## How to use

1. **Name the symptom** using the router below. Pick one lens, not three.
2. **Run its four steps out loud**, in six lines or fewer. Terse beats thorough.
3. **State what changed.** If nothing changed, the lens failed - say so and stop.

A lens that fired and found nothing is noise. Report the failure instead of dressing it up.

Depth files sit in `~/skills/thinking-toolkit/references/` in the Linux sandbox. Read one only when the lens is actually doing work - not to show diligence.

## Router

Diagnose the symptom, apply **one** lens. When two symptoms match, the lower number wins - the ordering is a tie-break, not a ranking of importance.

| # | Symptom you hear | Lens | Move |
|---|---|---|---|
| 1 | "There's only one way to do this" | Inversion | Flip the load-bearing assumption |
| 2 | "I've tried everything in this domain" | Collision | Treat A as if it were B |
| 3 | "Why does this exist?" / "let's rewrite this" | Lineage | Find what it replaced and why |
| 4 | "We just need one more special case" | Simplification | Find the rule with no exceptions |
| 5 | "It works in dev" / "should scale fine" | Scale | Test at 1000x and at 1/1000 |
| 6 | "Same shape keeps appearing" | Meta-pattern | Extract the form, find its third instance |

**Discipline:** state in one line what changed. If no decision changed, drop the lens silently - a performed lens is worse than no lens.

**Why precedence exists:** the symptoms genuinely overlap. "The solution feels incremental" matches both Collision and Simplification; "this is unique" matches Meta-pattern and Lineage. Without a tie-break the choice is arbitrary and unauditable.

**Cap:** six lenses, and adding a seventh means deleting one. Beyond that the symptom phrases stop being mutually recognisable, so dispatch degrades faster than coverage grows. At the other extreme, a single lens (Inversion) covers most ordinary stalls.

## 1. Inversion - "what if the opposite were true?"

1. List what *must* be true for the current plan to work.
2. Invert each one literally.
3. Ask what you would do if the inversion were true.
4. Keep the inversions that are already true somewhere in the world.

The payoff is not the opposite plan. It is finding which assumption was never checked.
Depth: `references/inversion-exercise.md`

## 2. Collision - "what if we treated X like Y?"

1. Pick a source domain with real structure (biology, economics, electrical circuits, postal systems).
2. Force the mapping: "our X behaves like their Y".
3. List what the mapped domain has that yours lacks.
4. Say precisely where the metaphor breaks - that edge is the finding.

Depth: `references/collision-zone-thinking.md`

## 3. Meta-pattern - "this is the third time I've seen this shape"

1. Spot the same structure in 3+ places.
2. Write it with every domain noun removed.
3. List how it adapts per domain - those are the knobs.
4. Apply it where it has not appeared yet.

Two instances is a coincidence. Three is a principle.
Depth: `references/meta-pattern-recognition.md`

## 4. Scale - "what breaks at 1000x?"

1. Pick the dimension that would vary: volume, rate, duration, failure rate, number of users.
2. Push it to both extremes, not just up.
3. Note what breaks.
4. Note what survives - that is what is fundamentally sound.

Extremes are cheap thought experiments that replace expensive production surprises.
Depth: `references/scale-game.md`

## 5. Simplification cascade - "is this all one thing?"

1. List the variations and the special cases.
2. Ask: "what if these are the same underneath?"
3. Name the general rule.
4. Count what you can delete.

A real cascade removes components. If nothing gets deleted, you renamed the complexity.
Depth: `references/simplification-cascades.md`

## 6. Lineage - "why does this exist at all?"

1. Find when and why the current approach was adopted (git log, ADRs, decision records, asking).
2. Find what it replaced, and what that replaced.
3. Separate "failed because flawed" from "failed because the context was different".
4. Ask whether the context has changed.

Before proposing a replacement, know what the original solved. Rewrites that skip this step re-derive the same scars.

Depth: `references/tracing-knowledge-lineages.md`

## Combining

The strongest chain is **Invert -> Scale -> Simplify**: inversion finds the unchecked premise, scale finds where it breaks, simplification deletes whatever only existed to protect it.

## Failure modes

- **Ritual performance.** Producing a tidy table that changes no decision. Worse than no lens.
- **Metaphor worship.** Collisions that sound clever and predict nothing. Test the mapping, do not admire it.
- **Inversion without checking.** Not every inversion is valid; some assumptions are true for good reasons.
- **Stacking lenses.** Running four lenses on a small question hides the answer in ceremony.
