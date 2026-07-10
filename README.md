# Advanced Git — A Hands-On Deep Dive into Git Internals

> 30 challenges. 3 parts. One repository, rewritten, branched, merged, rebased, conflicted, and pulled apart — on purpose — to actually understand how Git works under the hood.

This repository isn't a tutorial I copied. It's a real Git history, built commit by commit, where every rebase, squash, conflict, and detached HEAD actually happened in my terminal — mistakes included. The goal was never to memorize commands; it was to understand **what Git is doing to the object graph** every time I run one.

---

## Table of Contents

- [Why This Repo Exists](#why-this-repo-exists)
- [Repository Structure](#repository-structure)
- [Part 1 — Refining Git History](#part-1--refining-git-history)
- [Part 2 — Branching Basics](#part-2--branching-basics)
- [Part 3 — Advanced Workflows](#part-3--advanced-workflows)
- [Concepts I Now Actually Understand](#concepts-i-now-actually-understand)
- [Mistakes I Made (And What They Taught Me)](#mistakes-i-made-and-what-they-taught-me)
- [How to Explore This Repo](#how-to-explore-this-repo)
- [Author](#author)

---

## Why This Repo Exists

Most people learn Git as a short list of memorized commands: `add`, `commit`, `push`, `pull`. That's enough to survive, but it's not enough to *trust yourself* when history goes wrong — when a rebase conflicts, when you're stuck in detached HEAD, when someone force-pushed over your branch.

This repository is my answer to that gap. Every challenge here was done for real, against a real remote on GitHub, with real mistakes along the way (a stuck rebase, a `HEAD~3` that didn't exist, a merge that stubbornly refused to conflict on the first try). I kept those mistakes in the documentation on purpose — understanding *why* something failed taught me more than the commands that worked on the first try.

## Repository Structure

```
Advanced-Git/
├── README.md                          <- you are here
├── index.html                         <- interactive portfolio page for this repo
├── test1.md ... test6.md              <- scratch files used across the exercises
├── feature.txt, readme.txt            <- files used in branching/merge/conflict demos
├── .gitignore                         <- excludes /tmp
└── git-exercises-readme/
    ├── part1-refining-history/        <- 10 READMEs: amend, rebase, squash, split, drop,
    │                                      reorder, cherry-pick, visualize, reflog
    ├── part2-branching-basics/        <- 10 READMEs: create/switch/delete/rename branches,
    │                                      local vs remote, merge vs rebase, detached HEAD
    └── part3-advanced-workflows/      <- 10 READMEs: stash, conflicts (manual + mergetool),
                                           .gitignore, tags, push/pull with real divergence
```

Each of the 30 files in `git-exercises-readme/` documents one challenge: the concept behind it, the exact commands run, the real output produced, and a plain-English explanation of what Git actually did internally. They're written to be readable on their own — as reference material I can come back to, not just a changelog.

---

## Part 1 — Refining Git History

History rewriting: the part of Git most tutorials skip, and the part that actually separates "I use Git" from "I understand Git."

| # | Challenge | Core Command |
|---|---|---|
| 1 | Missing File Fix | `git commit --amend` |
| 2 | Editing Commit History | `git rebase -i` + `reword` |
| 3 | Squashing Commits | `git rebase -i --root` + `squash` |
| 4 | Splitting a Commit | `git reset` (mixed mode) |
| 5 | Advanced Squashing | `git rebase -i` + `squash` |
| 6 | Dropping a Commit | `git rebase -i` + `drop` |
| 7 | Reordering Commits | `git rebase -i` (line reordering) |
| 8 | Cherry-Picking | `git cherry-pick` |
| 9 | Visualizing History | `git log --graph --all` |
| 10 | Understanding Reflogs | `git reflog` |

**What this taught me:** a commit's hash is a fingerprint of its content *and* its parent's hash. The moment you touch any commit — even just its message — every commit built on top of it gets rewritten with a new hash, whether its content changed or not. Once that clicked, rebase stopped feeling like magic and started feeling like arithmetic.

## Part 2 — Branching Basics

| # | Challenge | Core Command |
|---|---|---|
| 1 | Feature Branch Creation | `git checkout -b` |
| 2 | Working on the Feature Branch | commit as normal, on a different branch |
| 3 | Switching Back | `git checkout main` |
| 4 | Local vs. Remote Branches | `git push -u origin <branch>`, `git branch -vv` |
| 5 | Branch Deletion | `git branch -d` / `-D` |
| 6 | Branch from a Specific Commit | `git checkout -b <name> <hash>` |
| 7 | Branch Merging | `git merge` (three-way merge) |
| 8 | Branch Rebasing | `git rebase main` |
| 9 | Renaming Branches | `git branch -m` |
| 10 | Detached HEAD | `git checkout <hash>` |

**What this taught me:** a branch is just a movable label pointing at a commit — nothing more. Switching branches doesn't "load a different project," it swaps your working directory to match wherever that label currently points. And merge vs. rebase isn't "which is correct" — it's "do I want to preserve exactly what happened (merge), or pretend I started here (rebase)?"

## Part 3 — Advanced Workflows

| # | Challenge | Core Command |
|---|---|---|
| 1 | Stashing Changes | `git stash` |
| 2 | Retrieving Stashed Changes | `git stash pop` |
| 3 | Merge Conflicts (manual) | conflict markers, manual resolution |
| 4 | Merge Conflicts (mergetool) | `git mergetool` |
| 5 | Detached HEAD (deeper dive) | recovery via `git reflog` |
| 6 | Ignoring Files | `.gitignore` |
| 7 | Working with Tags | `git tag` |
| 8 | Listing/Deleting Tags | `git tag -d`, `git push origin --delete` |
| 9 | Pushing Local Work | `git push -u origin <branch>` |
| 10 | Pulling Remote Changes | `git pull` (fetch + merge) |

**What this taught me:** this is the part where Git stops being "commands I run on my own machine" and becomes "how I collaborate without stepping on someone else's work." Stashing, resolving real conflicts, and understanding that `git pull` is secretly `fetch` + `merge` are the skills that actually matter day to day.

---

## Concepts I Now Actually Understand

**Rebase rewrites, merge preserves.**
Rebase replays your commits on top of a new base — clean, linear, but every replayed commit gets a new hash. Merge creates a new commit with two parents, joining two histories exactly as they happened, without touching either one. I now choose deliberately between them, instead of defaulting to whichever one avoided a conflict.

**A commit isn't really deleted until it's unreachable *and* garbage collected.**
`git reflog` logs every HEAD movement — every commit, rebase step, reset, and checkout — separately from `git log`. This is what makes Git forgiving: nearly every mistake (a bad rebase, a wrong `reset --hard`, a dropped commit) is recoverable for a window of time via the reflog, as long as I catch it before Git's garbage collector cleans it up.

**Detached HEAD is not an error state — it's just "not attached to a label."**
`HEAD` normally points at a branch name, which points at a commit. Check out a raw commit hash instead, and `HEAD` points straight at the commit with no branch in between. Perfectly safe to look around; risky only if I commit there and switch away without creating a branch first.

**`-d` (branch delete) checks reachability everywhere it can see — not just your current branch.**
I expected `git branch -d` to refuse deleting an unmerged branch. It didn't, because the branch had already been pushed to `origin`, and Git considered that "safe enough," warning instead of refusing. Small detail, but it changed how I think about what "merged" actually means to Git.

**Not every "conflict demo" produces a conflict.**
A conflict only happens when two branches change the *same lines* independently, after diverging. My first attempt at creating one just fast-forwarded, because only one side had actually changed. I had to make both sides commit competing changes before Git had anything to reconcile.

**`git pull` is `fetch` + `merge`, always.**
Understanding this made every "why did I get a merge commit I didn't ask for" moment make sense — if local and remote have both moved forward independently, pulling *will* merge them, conflict or not.

## Mistakes I Made (And What They Taught Me)

- **A stuck rebase** (editor closed mid-rebase) → learned `git rebase --abort` as a genuine safety net, and configured a reliable `core.editor` afterward.
- **`fatal: invalid upstream 'HEAD~3'`** → learned `~n` can't go past the root commit, and `git rebase -i --root` is the correct tool when you need to rewrite all the way back to the first commit.
- **A "conflict demo" that fast-forwarded instead of conflicting** → learned that conflicts require genuine divergence on both sides, not just a differently-named branch.
- **`.orig` files left behind by `git mergetool`** → learned about `mergetool.keepBackup` and why the tool keeps a pre-resolution copy by default.

## How to Explore This Repo

```bash
git clone https://github.com/Manzi-Elvis/Advanced-Git.git
cd Advanced-Git

# See the full commit graph across every branch
git log --oneline --graph --all

# See every branch, local and remote, with tracking status
git branch -vv

# Every HEAD movement ever made in this repo, mistakes included
git reflog

# Read the challenge-by-challenge breakdowns
cd git-exercises-readme
```

## Author

**MANZI RURANGIRWA Elvis**
Full-stack software engineer, learning Git one deliberate, real, occasionally-messy commit at a time.