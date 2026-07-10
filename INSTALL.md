# Installation Guide

## Prerequisites

- **Kai app** installed (v1.0+)
- **Internet connection** (for initial install)

---

## Method 1: One-Click Install (Recommended)

For each skill you want, open Kai → **Add Skill** → **Install from GitHub** → paste the URL:

```
bruxef/kai-skills/inversion-exercise
bruxef/kai-skills/collision-zone-thinking
bruxef/kai-skills/meta-pattern-recognition
bruxef/kai-skills/scale-game
bruxef/kai-skills/simplification-cascades
bruxef/kai-skills/tracing-knowledge-lineages
```

Tap **Install**. Repeat for each skill.

---

## Method 2: Batch Install (Advanced)

If you're comfortable with the Kai CLI or want to script it:

```bash
# Example using Kai's CLI (if available)
kai skill install bruxef/kai-skills/inversion-exercise
kai skill install bruxef/kai-skills/collision-zone-thinking
# ... etc
```

---

## Verification

After installation, each skill appears in **Kai → Skills → Installed**.

Test one:
> "Hey Kai, run the **Inversion Exercise** on my idea to quit my job and start a bakery."

You should see a structured inversion analysis.

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| "Invalid SKILL.md frontmatter" | You're using an old fork. Pull latest from `bruxef/kai-skills`. |
| Skill doesn't appear | Restart Kai. Check internet. Re-install. |
| "Repository not found" | Check spelling: `bruxef/kai-skills/<skill-name>` (all lowercase, hyphens). |

---

## Why These URLs Work

Each skill folder contains a valid `SKILL.md` with Kai-compatible frontmatter:

```yaml
name: inversion-exercise        # ✅ lowercase, hyphens only
version: "1.0.0"
description: "Stress-test ideas by flipping assumptions upside-down."
author: "obra (adapted for Kai by bruxef)"
tags: [thinking, decision-making, mental-models]
```

The upstream repo used `name: "Inversion Exercise"` — Kai rejects that. This repo fixes it.

---

## Updating Skills

Re-run the install command for a skill to get the latest version. Kai handles updates gracefully.

---

## Questions?

Open an issue on [GitHub](https://github.com/bruxef/kai-skills/issues) or ask in the Kai community.
