## Conflicts, Merging and Rebasing

### Overview
This section demonstrates how to handle merge conflicts, understand the difference between merging and rebasing, and manage branch integration strategies.

---

## Merge Main into Greet Branch

### 1. Initial Merge from Main to Greet
Start by merging the changes from the `main` branch into the `greet` branch:
```bash
git checkout greet
git merge main
```

---

## Create a Conflicting Change

### 2. Modify `hello.sh` in Main Branch
Switch to `main` branch and make the changes below to the `hello.sh` file:
```bash
#!/bin/bash

echo "What's your name"
read my_name

echo "Hello, $my_name"
```

Save and commit the changes:
```bash
git checkout main
git add lib/hello.sh
git commit -m "Add interactive mode to hello.sh"
```

---

## Merging Main into Greet Branch (Conflict)

### 3. Attempt to Merge and Encounter Conflict
Attempt to merge the `main` branch into `greet`. Bingooo! There you have it, a **conflict**:
```bash
git checkout greet
git merge main
```

### 4. Resolve the Conflict
Resolve the conflict manually or using graphical merge tools. Accept changes from `main` branch:
```bash
# Option 1: Manually edit lib/hello.sh to resolve conflicts
# Option 2: Accept changes from main branch
git checkout --theirs lib/hello.sh

# Or accept changes from greet branch
git checkout --ours lib/hello.sh
```

After resolving, stage and commit:
```bash
git add lib/hello.sh
git commit -m "Resolve conflict: accept changes from main"
```

---

## Rebasing Greet Branch

### 5. Go Back Before the Merge
Go back to the point before the initial merge between `main` and `greet`:
```bash
git checkout greet
git reset --hard HEAD~2
```

### 6. Rebase Greet on Top of Main
Rebase the `greet` branch on top of the latest changes in the `main` branch:
```bash
git rebase main
```

conflicts occur during rebase:
```bash

git restore --ours lib/hello.sh
```

---

## Merging Greet into Main

### 7. Merge Greet into Main Branch
Merge the changes from the `greet` branch into the `main` branch:
```bash
git checkout main
git merge greet
```

---

## Understanding Fast-Forwarding and Differences

### Fast-Forwarding
**Fast-forward** occurs when the target branch hasn't diverged from the source branch. Git simply moves the branch pointer forward without creating a merge commit.

**Example:**
```
Before merge:
main:  A---B
greet:     B---C---D

After fast-forward merge:
main:  A---B---C---D
greet:     B---C---D
```


### Merging vs Rebasing

| Aspect | Merging | Rebasing |
|--------|---------|----------|
| **History** | Preserves complete history with merge commits | Creates linear history by replaying commits |
| **Commits** | Creates a new merge commit | Rewrites commit history |
| **Use Case** | Best for shared/public branches | Best for cleaning up local branches |

**Merging:**
```
Before Merging:
main:  A---B---E
greet: B---C---D

After Merging:
A --- B -------- E
       \          \
        C --- D --- M   (greet)

```

**Rebasing:**
```
Before rebase:
main:  A---B---E
greet:     C---D

After rebase:
 A --- B ---E --- C'--- D'
```

### Key Differences:
- **Merge** preserves the exact history of how changes were made
- **Rebase** rewrites history to create a cleaner, linear progression

### When to Use Each:

**Use Merge when:**
- Working on a public/shared branch
- You want to preserve the complete history
- Multiple people are working on the same branch

**Use Rebase when:**
- Cleaning up local commits before pushing
- Keeping feature branch up-to-date with main
- You want a linear, cleaner history