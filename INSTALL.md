# Installation Guide

Last checked against Kai's skill docs (2026-10) and the app source (`SkillFrontmatterParser.kt`, `SkillManager.kt`, `SkillRegistry.kt`).

---

## Prerequisites

- Kai on **Android** (skills live in the Linux sandbox, which other platforms lack)
- Linux sandbox installed: Settings → Sandbox → Set up sandbox
- Network access for the initial install

---

## Install (single skill)

1. Settings → **Tools** → **Skills**
2. **Add Skill** → **Install from GitHub**
3. Paste:

```
bruxef/kai-skills
```

4. **Install**

That is it. The skill appears as **Thinking Toolkit** with the slash command `/thinking-toolkit`.

---

## Use

Start a message with the slash command:

```
/thinking-toolkit nossa API de pagamentos está lenta e todo mundo já tentou otimizar
```

The skill body is appended to the system prompt **for that turn only**. Nothing is added on other turns.

---

## How installation actually works

So you can debug it yourself:

- The installer parses `owner/repo[/path]`, or `.../tree/<ref>/<path>`.
- It fetches `https://raw.githubusercontent.com/<owner>/<repo>/<ref>/<path>/SKILL.md`.
- If the path is empty, it fetches `<repo>/main/SKILL.md` - **a repo with no root `SKILL.md` fails with `SKILL.md not found`**. This was v1's bug.
- Frontmatter rules: starts with `---`, closed by a second `---`; `name` = lowercase letters, digits, hyphens, ≤64 chars; `description` non-empty, ≤1024 chars. **Every other key is ignored** - including `when_to_use`, which is why triggers now live inside `description`.
- Files land in `~/skills/<id>/`, siblings included (text only, <256 KB).

---

## Troubleshooting

| Symptom | Cause | Fix |
|---|---|---|
| `SKILL.md not found at .../SKILL.md` | Installed the repo root of v1, or a path that no longer exists | Install `bruxef/kai-skills` (root now has `SKILL.md`) |
| Skills section shows "Install the sandbox first" | Sandbox missing | Settings → Sandbox → set up |
| Skill installs but never activates | Wrong id in the slash command | Use `/thinking-toolkit`; autocomplete appears when you type `/` |
| `name must be lowercase letters, digits, and hyphens` | Frontmatter has spaces/underscores | Fix `name:` in `SKILL.md` |

---

## Legacy: the six standalone skills

Preserved on tag `v1-legacy`:

```
https://github.com/bruxef/kai-skills/tree/v1-legacy/inversion-exercise
https://github.com/bruxef/kai-skills/tree/v1-legacy/collision-zone-thinking
https://github.com/bruxef/kai-skills/tree/v1-legacy/meta-pattern-recognition
https://github.com/bruxef/kai-skills/tree/v1-legacy/scale-game
https://github.com/bruxef/kai-skills/tree/v1-legacy/simplification-cascades
https://github.com/bruxef/kai-skills/tree/v1-legacy/tracing-knowledge-lineages
```
