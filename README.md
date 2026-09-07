# workflow-skills

A plugin marketplace (Claude Code, Codex and Antigravity) holding one plugin, `workflow`: the six-step build loop taught in the
AI Coding Mini-Course.

| Step | Skill | Writes |
| --- | --- | --- |
| 1 | `/workflow:ideate` | `idea.md` |
| 2 | `/workflow:refine` | `decisions.md` |
| 3 | `/workflow:spec` | `spec.md` |
| 4 | `/workflow:slice` | `slices.md` |
| 5 | `/workflow:implement` | the code, plus ticks under the slice |
| 6 | `/workflow:audit` | `audits/<NN>.md` |

All six write into one folder per idea, `builds/<NN>-<slug>/`, and each reads what the last one left.

## Install

In a terminal, standing in the project you want the loop in:

```
claude plugin marketplace add Karnonson/workflow-skills
claude plugin install workflow@workflow-skills --scope project
```

`--scope project` switches the plugin on for that folder only (it writes `.claude/settings.json`
there); leave it off and it switches on for every project on your machine. Then `/workflow:ideate`
and the rest answer by name in any Claude Code window opened in that folder. `claude plugin details
workflow` shows what it costs you per session; `claude plugin uninstall workflow --scope project`
removes it.

## Install in Codex or Antigravity

The same plugin installs in OpenAI's Codex CLI and in Google's Antigravity CLI (`agy`). Both install it
for every project on the machine (there is no per-folder switch), and both call the skills by a slightly
different name.

Codex:

```
codex plugin marketplace add Karnonson/workflow-skills
codex plugin add workflow@workflow-skills
```

Then the skills answer as `$workflow:ideate`, `$workflow:refine`, … in any Codex window (`/skills` lists them;
`codex plugin list` shows the plugin; `codex plugin remove workflow@workflow-skills` removes it).

Antigravity:

```
agy plugin install https://github.com/Karnonson/workflow-skills
```

Then the skills answer as `/ideate`, `/refine`, `/spec`, `/slice`, `/implement`, `/audit` in any `agy` window
(`/skills` lists them; `agy plugin list` shows the plugin; `agy plugin uninstall workflow` removes it).

## Where these come from

The skills in this repo are **copies**. They are written and revised in `~/Desktop/skill-hub/skills`, which is the
source of truth, and copied here to be published. Do not edit them here — the next copy out will overwrite it.

`refine` is adapted from Matt Pocock's `grilling` (MIT) — github.com/mattpocock/skills.
