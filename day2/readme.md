
# 📘 Day 2 – Branching & Parallel Development Workflow

## Objective of Day 2

By the end of this session, students will:

* Understand why branching is required
* Create and manage multiple branches
* Work on parallel features safely
* Merge feature branches into main
* Understand real-world collaborative workflows

---

## 1. What is Branching in Git?

### Simple Definition

A branch is a **separate line of development** in Git.

It allows you to:

* Work on new features
* Fix bugs
* Experiment safely
  Without affecting the main code.

---

### Why Branching Is Needed

Without branches:

* Everyone works on main
* Code breaks easily
* Conflicts increase
* Production risk

With branches:

* Safe development
* Parallel work
* Stable main branch
* Easy testing

---

## 2. Branching Fundamentals

### Default Branch

When you create a repository:

Default branch is usually:

```
main
```

This branch represents:

* Stable code
* Production-ready code

---

### Branch Structure Example

```
main
   \
    feature-login
```

Main branch stays stable.
Feature branch is used for development.

---

## 3. Creating and Managing Branches

---

### View All Branches

```bash
git branch
```

Shows:

* All local branches
* Current branch with *

---

### Create New Branch

```bash
git branch feature-ui
```

This creates branch but does NOT switch.

---

### Create and Switch Together

Recommended method:

```bash
git checkout -b feature-ui
```

OR new syntax:

```bash
git switch -c feature-ui
```

---

### Switch Between Branches

```bash
git checkout main
```

or

```bash
git switch main
```

---

### Important Point

Each branch has:

* Its own commit history
* Independent changes

---

## 4. Feature Branch Workflow

### What is Feature Branch Workflow?

Feature branch workflow means:

Each new feature is developed in a **separate branch**.

---

### Typical Flow

```
main
   \
    feature-payment
```

Steps:

1. Create feature branch
2. Develop feature
3. Commit changes
4. Merge into main
5. Delete feature branch

---

### Benefits

* Clean development
* Easy rollback
* Better code review
* Parallel work support

---

## 5. Working on Parallel Features

### Example Scenario

Developer A:

```
feature-login
```

Developer B:

```
feature-dashboard
```

Both branches work independently.

Main branch remains stable.

---

## 6. Merging Feature Branch into Main

---

### Step 1 — Switch to Main Branch

```bash
git checkout main
```

---

### Step 2 — Merge Feature Branch

```bash
git merge feature-ui
```

---

### What Happens?

Git:

* Combines feature changes
* Updates main branch
* Creates merge commit (if required)

---

## 7. Understanding Merge Strategies

---

### Fast Forward Merge

Happens when:

* Main branch has no new commits
* Feature branch is ahead

Git simply moves pointer forward.

No merge commit created.

---

### Normal Merge (Three-Way Merge)

Happens when:

* Both main and feature branches have new commits

Git:

* Combines histories
* Creates merge commit
* Preserves branch structure

---

## 8. Merge Commit Concept

### What is Merge Commit?

Merge commit:

* Joins two branches
* Has two parent commits
* Keeps branch history

It is NOT duplicate code.

It is a **history marker**.

---

## 9. Introduction to Collaborative Development Workflow

---

### How Teams Use Branches

Real project workflow:

```
main  → stable production code
feature branches → development work
```

---

### Typical Team Flow

1. Create feature branch
2. Work on code
3. Commit changes
4. Merge to main
5. Deploy

---

## 10. Best Practices for Branching

---

### Use Meaningful Branch Names

Good examples:

```
feature-login
bugfix-payment
hotfix-auth
```

Bad examples:

```
test1
newbranch
abc
```

---

### Keep Main Branch Stable

Never:

* Commit directly to main
* Test experimental code on main

---

### Update Branch Frequently

Regularly sync with main:

* Reduce conflicts
* Keep code updated

---

## 11. Common Mistakes Students Make

---

### Mistake 1 — Working Directly on Main

Fix:

Always create feature branch.

---

### Mistake 2 — Forgetting Current Branch

Always check:

```bash
git branch
```

Before committing.

---

### Mistake 3 — Not Deleting Old Branches

After merge:

```bash
git branch -d feature-ui
```

Keeps repo clean.

---

## End of Day 2 Summary

Students should now be able to:

* Create and switch branches
* Work on parallel features
* Follow feature branch workflow
* Merge branches into main
* Understand merge strategies
* Apply team collaboration concepts

