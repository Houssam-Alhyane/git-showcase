## Bare Repositories

### What is a Bare Repository?

A **bare repository** is a Git repository that contains only the version control information (`.git` contents) and no working directory (no actual files to edit). 

**Why is it needed?**

It is needed to act as a central "server" or "hub" for pushing and pulling changes, as you cannot push to a repository that has a currently checked-out working directory.

---

## Create Bare Repository

### 1. Create a Bare Repository Named `hello.git` from `hello`
```bash
git clone --bare hello hello.git
```

---

## Add Bare Repository as Remote

### 2. Add the Bare `hello.git` Repository as a Remote of `hello`
```bash
cd hello
git remote add shared ../hello.git
```

---

## Update and Push Changes

### 3. Change `README.md` in `hello` Repository

Make changes to the `README.md` file with the provided content:
```markdown
This is the Hello World example from the git project. (Changed in the original and pushed to shared)
```

### 4. Commit Changes and Push Them
```bash
git commit -am "Updated README for shared"
git push shared main
```

---

## Pull Changes in Cloned Repository

### 5. Pull Changes from Shared Repository

Switch to the cloned `cloned_hello` repository and pull the changes just pushed to the shared repository:
```bash
cd ../cloned_hello
git remote set-url origin ../hello.git
git pull origin main
```