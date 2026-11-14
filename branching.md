# Branch Management in Git

## Introduction
This section explains how to create, manage, and work with branches in Git. Branching is one of Git's most essential features, allowing developers to work on different parts of a project simultaneously without interfering with the main codebase.

---

## 1. What Is a Branch?
A branch in Git is an independent line of development. Think of it as a separate workspace where you can edit files, test new ideas, and record commits without affecting the stable `main` branch.

Behind the scenes, a branch is simply a lightweight, movable pointer to a specific commit. Every time you make a new commit, the pointer for your current branch automatically moves forward to that new commit.

```text
          A---B---C  (docs/complete-branching)
         /
    D---E---F---G  (main)
```
*In the diagram above, `docs/complete-branching` splits off from `main` at commit `E`. Any work done on this branch (`A`, `B`, `C`) remains isolated until it is ready to be merged back into `main`.*

---

## 2. Why Do We Use Branches?
* **Safe Isolation:** You can write code, fix bugs, or update documentation without risking breaking the working version of the project on `main`.
* **Parallel Collaboration:** Multiple team members can work on their assigned tasks at the same time (for example, one developer works on `docs/complete-branching` while another works on `feature/collaboration.md`).
* **Clean Code Reviews:** Branches allow you to group related commits together and open a **Pull Request** so teammates can review and approve your changes before merging.

---

## 3. Creating a New Branch
Before creating a new branch, always make sure you are on the `main` branch and have pulled the latest changes.

**Method 1: Create a branch without switching to it:**
```bash
git branch test-branch
```

**Method 2: Create a branch and switch to it immediately (Recommended):**
```bash
git checkout -b test-branch
```
*(Note: In newer versions of Git, you can also run `git switch -c test-branch`).*

**Expected Terminal Output:**
```text
Switched to a new branch 'test-branch'
```

---

## 4. Viewing Existing Branches
To see a list of all local branches on your computer, run:
```bash
git branch
```

**Expected Terminal Output:**
```text
* docs/complete-branching
  feature/collaboration.md
  main
```
*The asterisk (`*`) and green text highlight the branch you are currently working on.*

To view both **local** branches and **remote** branches (on GitHub), use the `-a` flag:
```bash
git branch -a
```

---

## 5. Switching Between Branches
To move from your current branch to another existing branch, use `git checkout` followed by the branch name:
```bash
git checkout main
```
*(Or in newer Git versions: `git switch main`).*

> **Tip for Beginners:** Always commit your changes before switching branches. Uncommitted changes may follow you to the new branch or prevent you from switching if they cause a conflict.

### Practical Terminal Example (Viewing, Creating, and Switching):
![terminal-branch](<img width="600" height="316" alt="terminal-branch" src="https://github.com/user-attachments/assets/5f615830-388e-4c4d-8a87-9b6843cb2721" />)

*As shown in the terminal screenshot above:*
1. Running `git branch` shows we are initially on `docs/complete-branching` (marked with `*`).
2. Running `git checkout -b test-branch` creates `test-branch` and switches to it immediately.
3. Running `git branch` again confirms the green `*` pointer has moved to `test-branch`.

## 6. Renaming a Branch

## 7. Deleting a Branch

## 8. Pushing a Branch to GitHub

<img width="1556" height="613" alt="github-branches" src="https://github.com/user-attachments/assets/a16e3561-f62f-4fab-894c-25dd911f4482" />
<img width="892" height="208" alt="push-branch" src="https://github.com/user-attachments/assets/e5f4e9b4-cbcc-47f8-85d4-5417602ba202" />
## 9. Practical Example
