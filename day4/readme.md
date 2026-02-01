# 📘 Day 4 – Collaboration Workflow & Essential Git Commands

## Objective of Day 4

By the end of this session, students will:

* Understand real-world team collaboration workflow
* Create and manage Pull Requests
* Participate in code reviews
* Handle advanced Git commands safely
* Understand merge strategies and conflicts
* Recover from common Git mistakes

---

## 1. What is Collaboration Workflow?

### Simple Meaning

Collaboration workflow defines:

How multiple developers:

* Work on the same repository
* Share code
* Review changes
* Merge safely into main branch

---

### Typical Team Workflow

```
Create Feature Branch
        ↓
Develop & Commit
        ↓
Push to Remote
        ↓
Create Pull Request
        ↓
Code Review
        ↓
Merge to Main
```

---

## 2. Pull Request (PR) Workflow

---

### What is a Pull Request?

A Pull Request is:

A request to merge code from one branch into another branch.

Used to:

* Review code
* Discuss changes
* Approve features
* Maintain quality

---

### PR Workflow Steps

1. Create feature branch
2. Commit changes
3. Push branch to GitHub
4. Open Pull Request
5. Review and approve
6. Merge PR
7. Delete feature branch

---

### Benefits of PR

* Code quality improves
* Bugs detected early
* Team collaboration
* Clear change tracking

---

## 3. Code Review Process

---

### What is Code Review?

Code review means:

Other developers review your code before merging.

---

### What Reviewers Check

* Code correctness
* Performance
* Security issues
* Coding standards
* Readability

---

### Best Practices

* Keep PRs small
* Write clear commit messages
* Respond to comments
* Fix requested changes

---

## 4. Fork-Based Contribution Workflow

---

### What is Fork?

Fork means:

Creating a copy of someone else’s repository in your GitHub account.

Used in:

* Open-source projects
* External contributions

---

### Fork Workflow

```
Fork Repo
   ↓
Clone Fork
   ↓
Create Feature Branch
   ↓
Push Changes
   ↓
Create PR to Original Repo
```

---

### Why Fork Is Important

* You don’t get direct write access
* Safe contribution model
* Maintains repository security

---

## 5. Updating Feature Branch with Latest Base Changes

When main branch gets new commits:

Your feature branch becomes outdated.

---

### Method 1 — Merge Main into Feature

```bash
git checkout feature
git merge origin/main
```

Creates merge commit.

---

### Method 2 — Rebase Feature onto Main

```bash
git checkout feature
git rebase origin/main
```

Creates clean linear history.

---

### Industry Practice

* Merge for shared branches
* Rebase for personal feature branches

---

## 6. Git Stash (Temporary Work Management)

---

### What is Git Stash?

Git stash temporarily saves:

* Uncommitted changes
* Working directory state

Allows you to:

* Switch branches
* Pull updates
* Resume later

---

### Save Work

```bash
git stash
```

---

### View Stash List

```bash
git stash list
```

---

### Restore Latest Stash

```bash
git stash pop
```

---

### Apply Without Removing

```bash
git stash apply
```

---

## 7. Git Revert (Safe Rollback)

---

### What is Git Revert?

Revert:

* Creates new commit
* Reverses changes safely
* Does NOT rewrite history

---

### Revert Command

```bash
git revert <commit-id>
```

---

### When to Use Revert?

* Production bug
* Shared branch rollback
* Safe undo required

---

## 8. Git Cherry-Pick (Selective Commit Transfer)

---

### What is Cherry-Pick?

Cherry-pick allows:

* Copying specific commit
* From one branch to another

---

### Cherry-Pick Example

```bash
git cherry-pick <commit-id>
```

---

### Use Case

* Hotfix from feature to main
* Apply specific patch

---
## 9. Handling Non-Fast-Forward Errors

---

### Common Error Message

```
non-fast-forward rejected
```

---

### Why It Happens

* Remote branch has new commits
* Local branch is outdated

---

### Fix Using Pull or Rebase

```bash
git pull --rebase
```

OR

```bash
git fetch
git rebase origin/main
```

Then push:

```bash
git push --force-with-lease
```

---

## 10. Fast-Forward vs Normal Merge

---

### Fast-Forward Merge

Occurs when:

* Main branch has no new commits
* Feature branch is ahead

No merge commit created.

---

### Normal Merge

Occurs when:

* Both branches changed

Creates merge commit.

---

## 11. Merge Commit & History Visualization

---

### Merge Commit

Merge commit:

* Has two parent commits
* Preserves branch history


---

## 12. Three-Way Merge Concept

Git compares:

* Base commit
* Current branch (HEAD)
* Incoming branch

If both branches change same line differently:

→ Conflict occurs.

---

## 13. Merge Conflict Detection & Resolution

---

### When Conflict Occurs

* Same file
* Same line
* Different changes

---

### Conflict Markers

```text
<<<<<<< HEAD
your code
=======
incoming code
>>>>>>> branch
```

---

### Resolution Steps

1. Open file
2. Decide correct code
3. Remove markers
4. Save file
5. Stage file
6. Commit merge

Commands:

```bash
git add .
git commit
```

---

## 14. Best Practices for Conflict Management

---

* Pull main branch frequently
* Keep PRs small
* Communicate with team
* Rebase feature branches regularly
* Avoid long-running branches

---



# 🔁 Merge vs Rebase – Clear Comparison

Both **merge** and **rebase** are used to integrate changes from one branch into another, but they work in **very different ways**.

---

## What is Merge?

### Definition

Merge combines two branches by creating a **merge commit** that joins both histories.

---

### Command Example

```bash
git merge feature
```

(while on main branch)

---

### What Happens Internally

* Git keeps both branch histories
* Creates a new merge commit
* Preserves branch structure

---

### Merge History Example

Before merge:

```
main:    A --- B --- D
feature:       C
```

After merge:

```
main:    A --- B --- D ---- M
                  \      /
                   C ----
```

`M` = merge commit (has two parents)

---

### Characteristics of Merge

* Does NOT rewrite history
* Safe for shared branches
* Preserves complete commit timeline
* Shows exactly when branches were merged

---

### When to Use Merge

Use merge when:

* Working with team branches
* Merging Pull Requests
* Updating main branch
* You want full history visibility

---

## What is Rebase?

---

### Definition

Rebase moves your branch commits **on top of another branch**, creating a **linear history**.

---

### Command Example

```bash
git rebase main
```

(while on feature branch)

---

### What Happens Internally

* Feature commits are removed
* Replayed on top of main
* New commit IDs are created
* History becomes straight line

---

### Rebase History Example

Before rebase:

```
main:    A --- B --- D
feature:       C
```

After rebase:

```
main:    A --- B --- D --- C'
```

`C'` = new commit (rewritten)

---

### Characteristics of Rebase

* Rewrites commit history
* Creates clean linear timeline
* No merge commit
* Makes history easier to read

---

### When to Use Rebase

Use rebase when:

* Working on personal feature branch
* Cleaning commit history
* Preparing branch before PR
* Branch is not shared

---

## Key Differences Table

| Feature                | Merge  | Rebase |
| ---------------------- | ------ | ------ |
| History rewrite        | ❌ No   | ✅ Yes  |
| Merge commit created   | ✅ Yes  | ❌ No   |
| Commit IDs change      | ❌ No   | ✅ Yes  |
| Safe for team branches | ✅ Yes  | ❌ No   |
| History readability    | Medium | High   |
| Rollback safety        | High   | Medium |

---

## Safety Rules (Very Important)

### Never Rebase These Branches

```
main
develop
release
shared branches
```

---

### Rebase Only These Branches

```
feature branches
local branches
personal branches
```

---

## Real Industry Usage

### Companies Use Merge For:

* Pull Requests
* Main branch integration
* Production merges

---

### Companies Use Rebase For:

* Cleaning feature branch history
* Syncing feature branch with main
* Removing unnecessary commits

---

## Interview Answer (Perfect)

Question: Difference between merge and rebase?

Answer:

> Merge preserves branch history by creating a merge commit, while rebase rewrites commit history by replaying commits on top of another branch, creating a linear history.

---

## Simple Memory Trick

Merge = Join histories
Rebase = Rewrite history

---

## Final Summary

* Merge is safe and preserves history
* Rebase creates clean history but rewrites commits
* Use merge for team work
* Use rebase for personal feature branches


## 15. Practical Demonstrations & Hands-On Labs

Suggested Labs:

* Create PR workflow demo
* Fork and contribute demo
* Simulate merge conflict
* Resolve conflict manually
* Use stash and cherry-pick
* Practice rebase

---


## 5. Squash Commits & Clean History Practices

---

### What is Squash Commit?

Squash means:

* Combine multiple commits
* Into single commit

---

### Why Squash?

* Cleaner history
* Easy rollback
* Better readability

---

### Example

Before squash:

```
fix typo
update UI
final fix
```

After squash:

```
Add login feature
```

---

### When to Squash

* Before merging PR
* Feature branch cleanup

---

## 6. Safe Force Push Techniques

---

### What is Force Push?

Force push overwrites remote history.

Command:

```bash
git push --force
```

---

### Why Dangerous?

* Deletes others' commits
* Breaks collaboration

---

### Safe Alternative

Always use:

```bash
git push --force-with-lease
```

---

### When Force Push Is Allowed

* Personal feature branch
* After rebase
* Never on main branch

---


## End of Day 4 Summary

You should now be able to:

* Create Pull Requests
* Participate in code reviews
* Use stash, revert, cherry-pick
* Handle merge conflicts
* Understand merge strategies
* Recover from common Git issues

