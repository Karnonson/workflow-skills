---
name: audit
description: Use after /implement finished a slice and before it is merged or the next slice starts. Audits the slice's changes on two axes — does it do what the slice and spec asked, is the code sound — in read-only sub-agents, and writes an audit with a verdict. Never fixes, never merges.
---

Find the slice under `builds/` (a number or name given as argument picks the folder, else the only one, else ask): the slice number named, else the last one with ticked boxes in `slices.md`. The fixed point is the commit before that slice's work began — its title is the commit message in `git log --oneline`; if unclear, ask. Confirm `git diff <fixed-point>...HEAD` is not empty first. If the slice carries a **Fixed:** line this is a second pass: the fixed point is the commit named at the top of `audits/<NN>.md`, and the only question is whether each fix-first item landed and broke nothing.

Spawn two read-only sub-agents at once, each given the diff command and commit list, neither the other's brief:

**Spec axis** gets `spec.md` and the slice's section from `slices.md`. Brief: for each **Done when** line and each Implementation or Testing decision this slice touches — done, part done, or missing; anything built that no line asked for; anything that looks done but reads wrong; if there is a **Look** heading, a fresh screenshot against it. Quote the line each finding answers. Under 300 words.

**Code axis** gets the smell list: a name that does not say what it holds; the same lines twice; one thing doing two jobs; a number or string standing in for a real idea; parts added for a need no line asks for; a check that reads the thing's insides instead of driving it from outside. Brief: the three that would cost the next slice most — name each, quote the lines, say the fix in one sentence. Judgement calls, never violations. Skip anything a linter would catch. Under 300 words.

Write `audits/<NN>.md` beside `slices.md` (a second pass appends **Second pass**): the commit audited on the first line, then **Spec** then **Code**, each report lightly cleaned into plain words, never merged or reranked across axes — a slice can pass one and fail the other. End with **Verdict**: *merge* when every Done when line holds and the seams pass — code findings then go under **Later**, not in the way; *fix first* only for a Done when line missing or part done, wrong behaviour, a crash, or something built no line asked for (list what, shortest first); *back to slice* when the slice or spec was wrong, say which line. A second pass ends in merge or back to slice, never fix first again. Add **Audit:** and the verdict under the slice in `slices.md`.

Show the verdict and the fix-first list, then stop. Do not fix anything, do not merge: fixes go back to `/implement` on the same slice, in a new window.
