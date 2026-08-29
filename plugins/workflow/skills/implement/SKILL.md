---
name: implement
description: Use after the slices exist. Builds exactly one slice — the one named, else the next whose blockers are done — runs it, ticks its Done-when boxes, commits. One slice per window; open slices can run in parallel, one window each.
---

Read `builds/<NN>-<slug>/slices.md` first (a number or name given as argument picks the folder, else the only one, else ask). **Open** slices are those whose **Blocked by** are all done. Take the one named, else the first open. If that slice already has an **Audit:** line with *fix first*, the work is that list in `audits/<NN>.md` — nothing else; when done, tick nothing new, replace the Audit line with **Fixed:** and say run `/audit` again. Name the others: each can be built at the same time in its own window with `/implement <folder> <NN>`; this window does not touch them. If more than one is open, work on a branch — `git worktree add ../<slug>-<NN> -b slice-<NN>` — so windows never overwrite each other. Then read `spec.md` (its Implementation and Testing decisions are the rules) and whatever code exists. Code lives in the project root, the folder holding `builds/`.

Before any code, say in plain words, under ten lines: what you will make, what it looks like from their side, the exact command or click that starts it, how each **Done when** line will be tried. Wait for a yes. That is the only check-in. Stuck later: one question, two or three choices, your pick.

Build this slice only — nothing for later slices, no "while I'm here" extras. Smallest thing that makes every Done when line true; install nothing the spec did not imply. Where the spec's Testing decisions name a seam this slice touches, write that check first, from outside, then the code that passes it. A check that cannot be made from outside: say so, never fake one.

Run it the way they would — the real command, the real click. Try every Done when line yourself. Tick a box in `slices.md` only after you saw it pass; a box you could not try stays open with one line saying why. Anything the spec did not foresee: smallest reasonable choice, one line under the slice starting **Chosen:**.

Finish by adding under the slice **How to run:** the command, and **Files:** what you made or changed. Commit with the slice number and title as the message. Stop and say: run `/audit` before merging or starting the next slice — that is a new window, not this one.
