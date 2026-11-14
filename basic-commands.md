# Basic Git Commands

## Introduction

Git is a distributed version control system that allows developers to track changes, manage different versions of a project, and collaborate with other developers.

This guide introduces the most commonly used Git commands with practical examples.

## 1. git init

The `git init` command initializes a new Git repository in the current directory.

### Example

```bash
mkdir MyProject
cd MyProject
git init
```

This creates a new directory called `MyProject` and initializes it as a Git repository.

## 2. git clone

The `git clone` command downloads an existing repository from a remote server such as GitHub.

### Example

```bash
git clone https://github.com/username/repository.git
```

Replace `username` and `repository` with the actual GitHub username and repository name.

## 3. git status

The `git status` command displays the current state of the working directory and staging area.

### Example

```bash
git status
```

This command helps developers identify modified, staged, and untracked files.

## 4. git add

The `git add` command adds changes to the staging area before creating a commit.

### Example

```bash
git add README.md
```

To stage all changes in the current directory:

```bash
git add .
```

## 5. git commit

The `git commit` command records staged changes in the local repository history.

### Example

```bash
git commit -m "Add project documentation"
```

A meaningful commit message should clearly describe the changes made.

## 6. git push

The `git push` command uploads local commits to a remote repository.

### Example

```bash
git push -u origin feature/documentation
```

This command pushes the local `feature/documentation` branch to GitHub and sets its upstream branch.

## 7. git pull

The `git pull` command downloads changes from a remote repository and integrates them into the current local branch.

### Example

```bash
git switch main
git pull origin main
```

This updates the local main branch with the latest changes from GitHub.

## 8. git branch

The `git branch` command is used to list, create, and manage branches.

### Example

```bash
git branch
```

This displays the local branches.

To create a new branch:

```bash
git branch feature/login
```

## 9. git switch

The `git switch` command allows developers to move between branches.

### Example

```bash
git switch main
```

To create a new branch and switch to it:

```bash
git switch -c feature/login
```

## 10. git log

The `git log` command displays the commit history of a repository.

### Example

```bash
git log
```

For a shorter output:

```bash
git log --oneline
```

This displays each commit using its abbreviated identifier and commit message.

## Practical Example

The following example demonstrates a basic Git workflow.

### Step 1: Create a Project Directory

```bash
mkdir GitExample
cd GitExample
```

### Step 2: Initialize Git

```bash
git init
```

### Step 3: Create a File

```bash
echo "# My First Git Project" > README.md
```

### Step 4: Check the Repository Status

```bash
git status
```

### Step 5: Stage the File

```bash
git add README.md
```

### Step 6: Commit the Changes

```bash
git commit -m "Add initial README file"
```

### Step 7: View the Commit History

```bash
git log --oneline
```

