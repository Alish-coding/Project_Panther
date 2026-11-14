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

---

## 6. Renaming a Branch
If you made a typo in your branch name or want a clearer name, you can rename it locally.

**If you are currently inside the branch you want to rename:**
```bash
git branch -m new-branch-name
```

**If you are on a different branch (e.g., `main`) and want to rename another branch:**
```bash
git branch -m old-branch-name new-branch-name
```

---

## 7. Deleting a Branch
Once your work on a branch is complete and merged into `main`, it is good practice to delete the old branch to keep your workspace clean.

1. First, make sure you are **not** currently inside the branch you want to delete (switch to `main` or another active branch):
   ```bash
   git checkout main
   ```
2. Safely delete a branch that has already been merged:
   ```bash
   git branch -d test-branch
   ```
3. **Force-deleting an unmerged branch:** If you created a temporary or experimental branch that is **not** merged, Git will prevent `-d` from deleting it to protect your work (`error: the branch 'test-branch' is not fully merged`). To force-delete it anyway, use a capital `-D`:
   ```bash
   git branch -D test-branch
   ```

---

## 8. Pushing a Branch to GitHub
When you create a branch locally, it only exists on your computer. To share your branch with teammates on GitHub and open a Pull Request, you must push it to the remote repository (`origin`):

```bash
git push -u origin docs/complete-branching
```
*(The `-u` flag links your local branch to the remote branch on GitHub. For future pushes on the same branch, you only need to type `git push`).*

### Step 1: Terminal Output When Pushing a Branch
![push-branch](<img width="892" height="208" alt="push-branch" src="https://github.com/user-attachments/assets/e5f4e9b4-cbcc-47f8-85d4-5417602ba202" />)

*As seen above, Git uploads the branch (`[new branch] docs/complete-branching -> docs/complete-branching`), sets up tracking with `origin`, and provides a direct URL to open a Pull Request.*

### Step 2: Verifying the Branch on GitHub
![github-branches](<img width="1556" height="613" alt="github-branches" src="https://github.com/user-attachments/assets/a16e3561-f62f-4fab-894c-25dd911f4482" />)

*Once pushed, opening the **Branches** page on the GitHub repository shows `docs/complete-branching` listed under **Your branches** and **Active branches** right alongside the default `main` branch.*

---

## 9. Practical Example
Below is the complete end-to-end workflow for a team member completing an assigned documentation task using a dedicated branch:

```bash
# 1. Switch to the main branch and pull the latest changes
git checkout main
git pull origin main

# 2. Create and switch to a dedicated branch for the issue
git checkout -b docs/complete-branching

# 3. Verify your active branch
git branch

# 4. Edit 'branching.md', then stage and commit your changes in meaningful steps
git add branching.md
git commit -m "Add initial branch management explanations and examples"

# 5. Push the branch to the remote GitHub repository
git push -u origin docs/complete-branching
```
After pushing the branch in Step 5, navigate to the repository on GitHub, click **Compare & pull request**, link your Issue (e.g., `Closes #2`), and ask a teammate to review and merge your work!
