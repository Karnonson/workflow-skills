# workflow-skills

A Claude Code marketplace holding one plugin, `workflow`: the six-step build loop taught in the
AI Coding Mini-Course.

| Step | Skill | Writes |
| --- | --- | --- |
| 1 | `/ideate` | `idea.md` |
| 2 | `/refine` | `decisions.md` |
| 3 | `/spec` | `spec.md` |
| 4 | `/slice` | `slices.md` |
| 5 | `/implement` | the code, plus ticks under the slice |
| 6 | `/audit` | `audits/<NN>.md` |

All six write into one folder per idea, `builds/<NN>-<slug>/`, and each reads what the last one left.

## Install

In any Claude Code session:

```
/plugin marketplace add Karnonson/workflow-skills
/plugin install workflow@workflow-skills
```

Then `/ideate` and the rest answer by name. `/plugin details workflow` shows what it costs you per
session; `/plugin uninstall workflow` removes it.

## Where these come from

The skills in this repo are **copies**. They are written and revised in `~/Desktop/skill-hub/skills`, which is the
source of truth, and copied here to be published. Do not edit them here — the next copy out will overwrite it.

`refine` is adapted from Matt Pocock's `grilling` (MIT) — github.com/mattpocock/skills.
