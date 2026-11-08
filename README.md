# Kai Critical-Thinking Toolkit

A single installable skill that gives Kai six ways out of a stall: **inversion, collision, meta-pattern, scale, simplification cascade, lineage tracing**.

Adapted for [Kai](https://github.com/SimonSchubert/Kai) from [obra/superpowers-skills](https://github.com/obra/superpowers-skills), then restructured for how Kai installs skills today.

---

## Install

Kai → **Settings → Tools → Skills → Add Skill → Install from GitHub**, then paste:

```
bruxef/kai-skills
```

One install, one slash command: **`/thinking-toolkit`**.

Requires the Linux sandbox (Android). After installing, type `/thinking-toolkit` at the start of a message and describe the problem - the skill's instructions are attached for that turn only.

---

## What changed in v2

**v1** shipped six separate skills (`/inversion-exercise`, `/scale-game`, ...) as six folders. That broke in two ways:

1. **Installing from the repo root failed** with `SKILL.md not found`, because there is no `SKILL.md` at the root - you had to know to append the folder name.
2. **Six installs, six slash commands, six prompt payloads.** Nobody remembers six commands, and combining lenses meant stacking unrelated bodies.

**v2** is one skill with a router: it names the symptom, picks one lens, runs it in four steps, and states what changed. Full originals live in `references/` and are read from the sandbox only when depth is needed.

| | v1 | v2 |
|---|---|---|
| Installs | 6 | 1 |
| Always-in-prompt cost | 0 (but 6 commands to remember) | 0 |
| Cost when active | 0.5-1.8k tokens | ~1k tokens, depth on demand |
| Install from repo root | fails | works |

---

## Structure

```
SKILL.md              # the router + six condensed lenses (~4.7 KB)
references/           # full original text per lens, read on demand
  inversion-exercise.md
  collision-zone-thinking.md
  meta-pattern-recognition.md
  scale-game.md
  simplification-cascades.md
  tracing-knowledge-lineages.md
```

---

## Still want the six standalone skills?

They are preserved on the `v1-legacy` tag. Install one at a time with an explicit ref path:

```
https://github.com/bruxef/kai-skills/tree/v1-legacy/inversion-exercise
https://github.com/bruxef/kai-skills/tree/v1-legacy/scale-game
```

Beware: `bruxef/kai-skills/inversion-exercise` on `main` no longer exists by design.

---

## Credits

Original skills by the [obra/superpowers-skills](https://github.com/obra/superpowers-skills) team. The underlying heuristics are much older - Polya's *How to Solve It* (1945), TRIZ, Munger's latticework - which is exactly why the content aged fine and the packaging did not.

License: MIT.
