# SOLUTION I

```bash
elvis@MRElvis MINGW64 ~/Documents/PROJECTS/Advanced-Git (main)
$ cd src

elvis@MRElvis MINGW64 ~/Documents/PROJECTS/Advanced-Git/src (main)
$ git add test1.md

elvis@MRElvis MINGW64 ~/Documents/PROJECTS/Advanced-Git/src (main)
$ git commit -m "chore: Initial File"
[main b6b6b86] chore: Initial File
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 src/test1.md

elvis@MRElvis MINGW64 ~/Documents/PROJECTS/Advanced-Git/src (main)
$ git add test2.md

elvis@MRElvis MINGW64 ~/Documents/PROJECTS/Advanced-Git/src (main)
$ git commit -m "chore: Second File"
[main 157521d] chore: Second File
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 src/test2.md

elvis@MRElvis MINGW64 ~/Documents/PROJECTS/Advanced-Git/src (main)
$ git add test3.md

elvis@MRElvis MINGW64 ~/Documents/PROJECTS/Advanced-Git/src (main)
$ git commit -m "chore: Third and Fourth Files"
[main e44015e] chore: Third and Fourth Files
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 src/test3.md

elvis@MRElvis MINGW64 ~/Documents/PROJECTS/Advanced-Git/src (main)
$ git status
On branch main
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        test4.md

nothing added to commit but untracked files present (use "git add" to track)

elvis@MRElvis MINGW64 ~/Documents/PROJECTS/Advanced-Git/src (main)
$ git add test4.md

elvis@MRElvis MINGW64 ~/Documents/PROJECTS/Advanced-Git/src (main)
$ git commit --amend -m "chore: Now, Third and Fourth Files"
[main e4f9c29] chore: Now, Third and Fourth Files
 Date: Fri Jun 26 14:45:20 2026 +0200
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 src/test3.md
 create mode 100644 src/test4.md

elvis@MRElvis MINGW64 ~/Documents/PROJECTS/Advanced-Git/src (main)
$ git status
On branch main
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

elvis@MRElvis MINGW64 ~/Documents/PROJECTS/Advanced-Git/src (main)
$ git log --oneline
e4f9c29 (HEAD -> main) chore: Now, Third and Fourth Files
157521d chore: Second File
b6b6b86 chore: Initial File
```