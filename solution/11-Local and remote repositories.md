## Local and Remote Repositories

### Overview
This section demonstrates how to work with remote repositories, clone repositories, fetch and merge changes, and manage remote branches.

---

## Clone the Repository

### 1. Clone `hello` Repository
In the `work/` directory, make a clone of the repository `hello` as `cloned_hello`. (Do not use `copy` command):
```bash
git clone hello cloned_hello
```

---

## Inspect the Cloned Repository

### 2. Show Logs for the Cloned Repository
```bash
cd cloned_hello
git log --oneline
```

### 3. Display Remote Repository Information
Show the name of the remote repository and provide more information about it:
```bash
git remote -v
git remote show origin
```

### 4. List All Remote and Local Branches
List all remote and local branches in the `cloned_hello` repository:
```bash
# List local branches
git branch

# List remote branches
git branch -r

# List all branches (local + remote)
git branch -a
```

---

## Make Changes to Original Repository

### 5. Update `README.md` in Original Repository
Make changes to the original repository, update the `README.md` file with the provided content:
```markdown
This is the Hello World example from the git project. (changed in the original)
```

Commit the changes:
```bash
cd ../hello
git add README.md
git commit -m "Update README in original repository"
```

---

## Fetch and Merge Changes

### 6. Fetch Changes from Remote Repository
Inside the cloned repository (`cloned_hello`), fetch the changes from the remote repository:
```bash
cd ../cloned_hello
git fetch
```

Display the logs and ensure that commits from the `hello` repository are included:
```bash
git log --oneline --all --graph
```

### 7. Merge Remote Changes into Local Branch
Merge the changes from the remote `main` branch into the local `main` branch:
```bash
git merge origin/main
```

---

## Track Remote Branches

### 8. Add Local Branch Tracking Remote Branch
Add a local branch named `greet` tracking the remote `origin/greet` branch:
```bash
git checkout -b greet origin/greet
```

---

## Add Remote and Push Branches

### 9. Add Remote and Push Branches
Add a `remote` to your Git repository and push the `main` and `greet` branches to the remote:
```bash
git remote add github <remote-url>
git push -u github main
git push -u github greet
git push -tags -u origin
```

---

## Audit Question

### Single Command Equivalent
**Question:** What is the single git command equivalent to what you did before to bring changes from remote to local `main` branch?

**Answer:**
```bash
git pull
```

**Explanation:**

The `git pull` command is equivalent to running `git fetch` followed by `git merge`:
```bash
# Instead of doing:
git fetch
git merge origin/main

# You can simply do:
git pull
```
