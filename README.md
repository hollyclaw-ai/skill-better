# skill-better

An Agent Skill for evaluating and improving other skills through testing, feedback, and iterative refinement.

Portable and runtime-agnostic. Hermes and other platform rules live in optional adapters. The default workflow stays light: prioritize by use, propose concrete edits, and get owner confirmation. Independent review / Round-2 dispute handling is optional detail.

**Status:** draft. Static checks and fictional walkthroughs only. **Not tested against real private skills** and **not measured with live model runs**. Licensed under the repository [MIT LICENSE](LICENSE) (Copyright (c) 2026 hollyclaw-ai).

## Install

Clone or copy this repository into your agent's skills directory so that:

```text
<skills-root>/skill-better/SKILL.md
```

Keep the folder name `skill-better` matching frontmatter `name`. Examples of skills roots (product-dependent): project `.agents/skills/`, Claude skills folders, or Hermes `~/.hermes/skills/...`. Reload/restart the agent session if your runtime only indexes skills at startup.

## Usage

- Ask the agent to improve or retire existing skills with skill-better (default: suggestions / candidates; live replace only after owner confirmation).
- For deeper testing, follow `references/eval-protocol.md` and mark `not_run` without a provider.
- For independent reviewer/editor/owner roles and Round 2 disputes, see `references/independent-review-protocol.md`.

## Layout

- `SKILL.md` — executable workflow
- `references/` — optional protocols, rubric, adapters, sources
- `examples/` — fictional before/after cases with expected audits and evals
- `LICENSE` — MIT (Copyright (c) 2026 hollyclaw-ai)

## Open-source notes

- Do not invent a different copyright holder
- Re-verify upstream licenses in `references/sources.md` before vendoring third-party text
- Examples are synthetic; replace or keep them clearly labeled if you fork
- Run skill-better on real libraries only with owner permission
