    # Git & GitHub: Complete Commands and Lessons

### Beginner → Intermediate → Advanced

A practical Git course for software engineering students. Learn the
concepts, use the commands, and practice in a repository.

> Git has many commands. Focus on understanding the workflow instead of
> memorizing every command. Commands that can discard work are marked
> with **WARNING**.

## Course roadmap

1.  Git fundamentals and configuration
2.  Create and initialize repositories
3.  Basic workflow: status, add, commit
4.  Inspect changes and history
5.  Branching
6.  Merge and conflict resolution
7.  GitHub and remote repositories
8.  Undo changes safely
9.  Stashing
10. Rebase and cherry-pick
11. Tags and releases
12. `.gitignore`
13. Collaboration workflow
14. Advanced commands
15. Practice project and cheat sheet

------------------------------------------------------------------------

# Lesson 1 --- Git Fundamentals

## What is Git?

Git is a distributed version control system. It tracks code changes,
preserves snapshots, supports branching, and helps developers
collaborate.

### Git vs GitHub

  -----------------------------------------------------------------------
  Git                                 GitHub
  ----------------------------------- -----------------------------------
  Version-control software            Online hosting and collaboration
                                      platform

  Works locally                       Hosts remote repositories

  Tracks snapshots and history        Pull requests, reviews, issues, and
                                      sharing
  -----------------------------------------------------------------------

## Install and configure

``` bash
git --version
git config --global user.name "Chanrith"
git config --global user.email "your-email@example.com"
git config --global init.defaultBranch main
git config --list
git config user.name
git config user.email
```

Useful configuration commands:

``` bash
git config --global core.editor "code --wait"
git config --global color.ui auto
git config --global --unset user.name
```

`--global` applies to your user account. Omitting it configures only the
current repository.

------------------------------------------------------------------------

# Lesson 2 --- Create a Repository

``` bash
mkdir git-practice
cd git-practice
git init
echo "# Git Practice" > README.md
git status
```

Initialize a repository in the current directory:

``` bash
git init
```

Initialize using a specific directory:

``` bash
git init my-project
```

Clone an existing repository:

``` bash
git clone https://github.com/username/repository.git
git clone https://github.com/username/repository.git my-folder
git clone --branch main https://github.com/username/repository.git
```

------------------------------------------------------------------------

# Lesson 3 --- Basic Workflow

## The three main areas

-   **Working directory:** files you edit.
-   **Staging area (index):** changes selected for the next commit.
-   **Repository:** committed snapshots.

``` text
Working Directory --git add--> Staging Area --git commit--> Local Repository
Local Repository --git push--> Remote Repository (GitHub)
Remote Repository --git fetch/pull--> Local Repository
```

## Check status

``` bash
git status
git status --short
```

## Stage changes

``` bash
git add README.md
git add .
git add -A
git add *.java
git add -p
```

-   `git add <file>` stages a file.
-   `git add .` stages changes under the current directory.
-   `git add -A` stages additions, modifications, and deletions across
    the working tree.
-   `git add -p` lets you stage selected portions interactively.

## Commit

``` bash
git commit -m "Initial commit"
git commit
git commit -am "Update tracked files"
git commit --amend
git commit --amend -m "Correct commit message"
```

`git commit -am` stages modifications and deletions of already tracked
files, but does **not** stage new untracked files. `--amend` replaces
the latest commit; avoid amending commits already shared with others.

## Remove and rename files

``` bash
git rm filename.txt
git rm --cached filename.txt
git mv old-name.txt new-name.txt
```

`git rm --cached` removes a file from Git tracking but keeps it on disk.

------------------------------------------------------------------------

# Lesson 4 --- Inspect Changes and History

## Diff commands

``` bash
git diff
git diff --staged
git diff HEAD
git diff -- README.md
git diff main feature-login
git diff <commit1> <commit2>
git diff --stat
git diff --name-only
```

## History commands

``` bash
git log
git log --oneline
git log -5
git log --oneline --graph --decorate --all
git log -- README.md
git log --author="Chanrith"
git log --since="2 weeks ago"
git log --grep="login"
git show
git show <commit-hash>
git show HEAD
git show HEAD~1
```

Useful formatted history:

``` bash
git log --pretty=format:"%h | %an | %ad | %s" --date=short
```

Inspect line-by-line authorship:

``` bash
git blame README.md
git blame -L 10,20 README.md
```

Find a commit or branch position after operations:

``` bash
git reflog
git reflog --all
```

------------------------------------------------------------------------

# Lesson 5 --- Branching

Branches isolate feature work from the main line of development.

``` bash
git branch
git branch -a
git branch feature-login
git switch feature-login
git switch -c feature-login
git switch main
git branch -m feature-auth
git branch -d feature-login
git branch -D feature-login
```

Older branch-switching syntax:

``` bash
git checkout main
git checkout -b feature-login
```

-   `-d` safely deletes a merged branch.
-   `-D` force-deletes a branch. Use carefully.
-   `git branch -a` lists local and remote-tracking branches.

------------------------------------------------------------------------

# Lesson 6 --- Merge and Resolve Conflicts

Merge a feature branch into `main`:

``` bash
git switch main
git merge feature-login
```

Create a merge commit even when fast-forward is possible:

``` bash
git merge --no-ff feature-login
```

Abort an in-progress merge:

``` bash
git merge --abort
```

## Conflict resolution

A conflict can look like:

``` text
<<<<<<< HEAD
Content from the current branch
=======
Content from the incoming branch
>>>>>>> feature-login
```

Steps:

1.  Open each conflicted file.
2.  Choose or combine the correct content.
3.  Remove conflict markers.
4.  Stage resolved files.
5.  Complete the merge commit.

``` bash
git status
git add resolved-file.txt
git commit
```

------------------------------------------------------------------------

# Lesson 7 --- Remote Repositories and GitHub

## Remote commands

``` bash
git remote
git remote -v
git remote add origin https://github.com/username/repository.git
git remote set-url origin https://github.com/username/repository.git
git remote rename origin upstream
git remote remove upstream
```

## Push

``` bash
git push
git push origin main
git push -u origin feature-login
git push --all origin
git push --tags
```

`-u` sets the upstream tracking branch, making future pushes and pulls
simpler.

## Fetch and pull

``` bash
git fetch
git fetch origin
git fetch --all
git pull
git pull origin main
git pull --rebase
```

-   `fetch` downloads remote information without integrating it into
    your current branch.
-   `pull` fetches and then integrates changes (usually by merge, or
    rebase if configured/requested).

## Track remote branches

``` bash
git branch -r
git switch --track origin/feature-login
```

## Delete a remote branch

``` bash
git push origin --delete feature-login
```

## Remove stale remote-tracking branches

``` bash
git fetch --prune
git remote prune origin
```

------------------------------------------------------------------------

# Lesson 8 --- Undo Changes Safely

## Discard unstaged changes

``` bash
git restore README.md
git restore .
```

**WARNING:** These commands discard unstaged edits in the selected
files.

## Unstage changes

``` bash
git restore --staged README.md
git restore --staged .
```

## Restore a file from a commit

``` bash
git restore --source=HEAD~1 README.md
git restore --source=<commit-hash> -- README.md
```

## Reset commits

``` bash
git reset --soft HEAD~1
git reset --mixed HEAD~1
git reset HEAD~1
git reset --hard HEAD~1
```

-   `--soft`: move branch pointer; keep changes staged.
-   `--mixed` (default): move pointer; keep changes unstaged.
-   `--hard`: move pointer and discard working-tree/staging changes.
    **WARNING: can destroy work.**

## Revert a commit

``` bash
git revert <commit-hash>
git revert HEAD
git revert --no-edit <commit-hash>
```

`revert` creates a new commit that reverses the chosen commit. It is
generally safer for commits already shared with teammates.

## Clean untracked files

Preview first:

``` bash
git clean -n
git clean -nd
```

Remove untracked files or directories:

``` bash
git clean -f
git clean -fd
```

**WARNING:** `git clean` deletes untracked files. Always preview with
`-n` first.

------------------------------------------------------------------------

# Lesson 9 --- Stash

Temporarily save work without committing:

``` bash
git stash
git stash push -m "WIP login feature"
git stash push -u -m "Include untracked files"
git stash list
git stash show
git stash show -p
git stash apply
git stash apply stash@{1}
git stash pop
git stash drop stash@{0}
git stash clear
```

-   `apply` restores a stash but keeps it in the stash list.
-   `pop` restores and removes the stash entry if successful.
-   `-u` includes untracked files.
-   `clear` removes all stash entries.

------------------------------------------------------------------------

# Lesson 10 --- Rebase and Cherry-Pick

## Rebase

``` bash
git switch feature-login
git rebase main
git rebase --continue
git rebase --skip
git rebase --abort
```

Rebase reapplies commits on a new base. Avoid rewriting published/shared
history unless your team agrees.

## Interactive rebase

``` bash
git rebase -i HEAD~3
```

Interactive rebase can reorder, edit, squash, or drop commits. Common
actions in its editor:

-   `pick`: keep commit.
-   `reword`: change commit message.
-   `edit`: stop to edit a commit.
-   `squash`: combine with previous commit.
-   `fixup`: combine and discard this commit message.
-   `drop`: remove commit.

## Cherry-pick

``` bash
git cherry-pick <commit-hash>
git cherry-pick --continue
git cherry-pick --abort
```

Cherry-pick applies a selected commit onto the current branch.

------------------------------------------------------------------------

# Lesson 11 --- Tags and Releases

``` bash
git tag
git tag v1.0.0
git tag -a v1.0.0 -m "Release 1.0.0"
git show v1.0.0
git push origin v1.0.0
git push origin --tags
git tag -d v1.0.0
git push origin --delete v1.0.0
```

Tags are useful for marking releases such as `v1.0.0`, `v1.1.0`, and
`v2.0.0`.

------------------------------------------------------------------------

# Lesson 12 --- .gitignore

Example Java/Spring Boot `.gitignore`:

``` gitignore
target/
*.class
*.log
.env
application-local.properties
.idea/
.vscode/
.DS_Store
```

Example Next.js `.gitignore`:

``` gitignore
node_modules/
.next/
out/
.env
.env.local
npm-debug.log*
```

If a file is already tracked, `.gitignore` alone will not untrack it:

``` bash
git rm --cached filename
git commit -m "chore: stop tracking local file"
```

Never commit passwords, API keys, private keys, or production secrets.

------------------------------------------------------------------------

# Lesson 13 --- Team Workflow

A common feature branch workflow:

``` bash
git switch main
git pull origin main
git switch -c feature-student-profile

# Make changes
git status
git add .
git commit -m "feat: add student profile"

git push -u origin feature-student-profile
```

Then open a Pull Request on GitHub, request review, address feedback,
and merge according to your team's policy.

## Conventional Commit examples

``` text
feat: add user authentication
fix: resolve login validation bug
docs: update README
refactor: simplify user service
test: add user service unit tests
chore: update dependencies
style: format source code
perf: optimize database query
```

------------------------------------------------------------------------

# Lesson 14 --- Advanced Commands

## Bisect: find which commit introduced a bug

``` bash
git bisect start
git bisect bad
git bisect good <known-good-commit>
# Test the version Git checks out
git bisect good
git bisect bad
git bisect reset
```

## Worktree: work with multiple working directories

``` bash
git worktree list
git worktree add ../project-feature feature-login
git worktree add -b feature-new main ../project-new
git worktree remove ../project-feature
git worktree prune
```

## Submodules

``` bash
git submodule add https://github.com/example/library.git libs/library
git submodule update --init --recursive
git submodule update --remote
git submodule status
git submodule deinit libs/library
```

## Archive a repository snapshot

``` bash
git archive --format=zip HEAD -o project.zip
```

## Verify repository integrity

``` bash
git fsck
git count-objects -v
```

## Search tracked files

``` bash
git grep "TODO"
git grep "class Student"
git grep -n "TODO" <commit-hash>
```

------------------------------------------------------------------------

# Lesson 15 --- Practice Project

Create a small Student Management project repository.

## Step 1: Initialize

``` bash
mkdir student-management
cd student-management
git init
echo "# Student Management System" > README.md
git add .
git commit -m "Initial commit"
```

## Step 2: Create a feature branch

``` bash
git switch -c feature-student
echo "Student feature" > student.txt
git add .
git commit -m "feat: add student feature"
```

## Step 3: Merge the feature

``` bash
git switch main
git merge feature-student
git log --oneline --graph --all
```

## Step 4: Connect to GitHub

Create an empty GitHub repository, then:

``` bash
git remote add origin https://github.com/username/student-management.git
git push -u origin main
```

## Practice challenges

-   [ ] Create a repository and make three commits.
-   [ ] Create a feature branch and merge it.
-   [ ] Make a merge conflict and resolve it.
-   [ ] Stash changes, switch branches, then restore them.
-   [ ] Revert a commit.
-   [ ] Push a branch to GitHub and open a Pull Request.
-   [ ] Create a release tag `v1.0.0`.
-   [ ] Use `git reflog` to inspect recent HEAD movements.

------------------------------------------------------------------------

# Git Command Cheat Sheet

  Task                   Command
  ---------------------- ----------------------------------
  Initialize             `git init`
  Clone                  `git clone <url>`
  Status                 `git status`
  Stage                  `git add <file>`
  Stage all              `git add -A`
  Commit                 `git commit -m "message"`
  History                `git log --oneline`
  Diff                   `git diff`
  Staged diff            `git diff --staged`
  Branch list            `git branch`
  Create/switch branch   `git switch -c <branch>`
  Switch branch          `git switch <branch>`
  Merge                  `git merge <branch>`
  Fetch                  `git fetch`
  Pull                   `git pull`
  Push                   `git push`
  Restore file           `git restore <file>`
  Unstage file           `git restore --staged <file>`
  Revert commit          `git revert <hash>`
  Stash                  `git stash`
  Apply stash            `git stash apply`
  Reflog                 `git reflog`
  Tag                    `git tag -a v1.0.0 -m "Release"`

## Recommended learning order

Practice these first until they feel natural:

``` bash
git init
git clone
git status
git add
git commit
git log
git diff
git branch
git switch
git merge
git pull
git push
git restore
git revert
git stash
```

The goal is to use Git every day while building projects---not just
memorize commands.
