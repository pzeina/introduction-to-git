# introduction-to-git
Use Git like a Pro! – Educational Repository

This repository is designed for **learning and teaching Git**.
It contains small demos and visual explanations of the most important Git concepts: commits, branches, merges, rebases, conflicts, staging, and GitHub Actions.

---

## 📚 Table of Contents

1. [Getting Started](#getting-started)
2. [Core Git Commands](#core-git-commands)
3. [Commit History & Graphs](#commit-history--graphs)
4. [Branching](#branching)
5. [Merging vs Rebasing](#merging-vs-rebasing)
6. [Solving Merge Conflicts](#solving-merge-conflicts)
7. [Staging Area](#staging-area)
8. [GitHub Actions](#github-actions)
9. [Repository Exercises](#repository-exercises)
10. [References](#references)

---

## 🚀 Getting Started

Clone this repo to play with the demos:

```bash
git clone https://github.com/pzeina/introduction-to-git.git
cd introduction-to-git
```

Useful aliases for pretty commit graphs:

```bash
git config --global alias.lg "log --oneline --graph --decorate --all"
```

---

## 🔧 Core Git Commands

| Command                    | Description                        |
| -------------------------- | ---------------------------------- |
| `git init`                 | Initialize a new repository        |
| `git clone <url>`          | Copy a remote repository           |
| `git status`               | Show working directory changes     |
| `git add <file>`           | Stage file(s)                      |
| `git commit -m "msg"`      | Save staged changes                |
| `git log --oneline`        | View history                       |
| `git branch`               | List branches                      |
| `git checkout -b <branch>` | Create + switch branch             |
| `git merge <branch>`       | Merge into current branch          |
| `git rebase <branch>`      | Replay commits onto another branch |

---

## 📜 Commit History & Graphs

Example after some commits:

```
* c3 (feature) Added new function
* c2 Updated README
* c1 Initial commit
```

Using `git lg`:

```
* c3 (HEAD -> feature) Added new function
| * c2 (main) Updated README
|/
* c1 Initial commit
```

---

## 🌱 Branching

Branches let you experiment safely.

![branch diagram](docs/images/branches.png)

---

## 🔀 Merging vs Rebasing

### Merge

```
main
  \
   feature ---- merge --> main
```

Keeps full history.

### Rebase

```
main ------
             \
              feature (rebased)
```

History is rewritten into a straight line.

![merge vs rebase](docs/images/merge-vs-rebase.png)

---

## ⚡ Solving Merge Conflicts

When Git can’t auto-merge:

```bash
git merge feature
# conflict in file.txt
```

Conflicted file looks like:

```diff
<<<<<<< HEAD
Line from main
=======
Line from feature
>>>>>>> feature
```

Resolve manually → `git add file.txt` → `git commit`.

---

## 📦 Staging Area

The staging area lets you **prepare commits**:

```bash
git add file1.txt    # staged
git add -p           # stage chunks
git reset HEAD file1 # unstage
```

![staging area diagram](docs/images/staging.png)

---

## 🤖 GitHub Actions

This repo also contains a simple workflow (`.github/workflows/ci.yml`):

```yaml
name: CI
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - run: echo "Hello GitHub Actions!"
```

Try pushing changes and watch Actions run 🚀

---

## 🏋️ Repository Exercises

* Create a new branch and commit changes
* Merge vs Rebase it into `main`
* Introduce a conflict and resolve it
* Stage only part of a file
* Add a GitHub Action that runs tests

---

## 📖 References

* [Pro Git Book (free)](https://git-scm.com/book/en/v2)
* [Git Documentation](https://git-scm.com/docs)
* [GitHub Actions Docs](https://docs.github.com/actions)

---

## 💡 Repo Structure Proposal

```
git-for-professionals-edu/
│── README.md
│── docs/images/          # diagrams (branch, merge, rebase, staging)
│── demos/
│   ├── merge-demo/       # small project for merge practice
│   ├── rebase-demo/      # rebase exercises
│   ├── conflict-demo/    # intentional conflict setup
│── .github/workflows/ci.yml
```

