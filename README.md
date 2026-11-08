# Kai Critical-Thinking Toolkit

A single installable skill that gives Kai six ways out of a stall: **inversion, collision, meta-pattern, scale, simplification cascade, lineage tracing**.

Adapted for [Kai](https://github.com/SimonSchubert/Kai) from [obra/superpowers-skills](https://github.com/obra/superpowers-skills), then restructured for how Kai installs skills today.

---

## Install

Kai → **Settings → Tools → Skills → Add Skill → Install from GitHub**, then paste:

```
bruxef/kai-skills/thinking-toolkit
```

One install, one slash command: **`/thinking-toolkit`**.

> **Do not install `bruxef/kai-skills` (the repo root).** It will install `SKILL.md` but silently drop `references/`. See [Why the subfolder path](#why-the-subfolder-path) below. The root intentionally has no `SKILL.md` so the failure is loud instead of silent.

Requires the Linux sandbox (Android). After installing, type `/thinking-toolkit` at the start of a message and describe the problem - the skill's instructions are attached for that turn only.

---

## Why the subfolder path

Kai's installer resolves bundled files like this (`SkillRegistry.kt`):

```kotlin
val siblings = tree.filter { it.startsWith("$path/") && it != "$path/SKILL.md" }
```

When you install from a repo root, `path` is `""`, so the filter becomes `startsWith("/")`. No path in a git tree starts with a slash, so **`siblings` is always empty**: the installer fetches `SKILL.md` and nothing else. Any skill whose depth lives in sibling files loses them silently when installed from its repo root.

Install from a subfolder (`path = "thinking-toolkit"`) and the filter works as intended, including nested directories - `references/*.md` download with their relative paths.

This is an upstream bug, not a repo bug. A one-line fix would trim the empty case:

```kotlin
val base = path.trim('/')
val prefix = if (base.isEmpty()) "" else "$base/"
val siblings = tree.filter { it.startsWith(prefix) && it != "$prefix/SKILL.md" }
```

Copying the missing files into `~/skills/<id>/` by hand does **not** survive: `SkillManager.install()` calls `deleteEntry(base, recursive = true)` before writing, so the next install wipes them again.

---

## What changed in v2

**v1** shipped six separate skills (`/inversion-exercise`, `/scale-game`, ...) as six folders. That broke in two ways:

1. **Installing from the repo root failed** with `SKILL.md not found`, because there was no `SKILL.md` at the root - you had to know to append the folder name.
2. **Six installs, six slash commands, six prompt payloads.** Nobody remembers six commands, and combining lenses meant stacking unrelated bodies.

**v2** is one skill with a router: it names the symptom, picks one lens, runs it in four steps, and states what changed. Full originals live in `references/` and are read from the sandbox only when depth is needed.

**v2.1** moved the skill into `thinking-toolkit/` after discovering that a root-level install drops every bundled file (see above).

| | v1 | v2.1 |
|---|---|---|
| Installs | 6 | 1 |
| Always-in-prompt cost | 0 (but 6 commands to remember) | 0 |
| Cost when active | 0.5-1.8k tokens | ~1.4k tokens, depth on demand |
| Depth files survive install | yes | yes (via subfolder path) |

The router is also mirrored, as a ~150-token trigger table, in Kai's **soul** (`Settings → Agent → Soul`). The soul decides *when* a lens is warranted; the skill holds *how* to run it. Without the soul line the skill only fires when you remember to type `/thinking-toolkit` - which, empirically, is never.

---

## Structure

```
thinking-toolkit/
  SKILL.md            # the router + six condensed lenses (~5.5 KB)
  references/         # full original text per lens, read on demand
    inversion-exercise.md
    collision-zone-thinking.md
    meta-pattern-recognition.md
    scale-game.md
    simplification-cascades.md
    tracing-knowledge-lineages.md
```

After install, the skill lives at `~/skills/thinking-toolkit/` (folder name follows the frontmatter `name`, not the repo path).

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
