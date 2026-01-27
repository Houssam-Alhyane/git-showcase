## Blobs, Trees and Commits

### Exploring `.git/` Directory
Navigate to the `.git/` directory in your project and examine its contents. You will need to explain the purpose of each subdirectory, including `objects/`, `config`, `refs/`, and `HEAD` in the audit.

### `.git/` Directory Overview

| Subdirectory/File | Purpose |
|-------------------|---------|
| `objects/` | Stores all Git objects: blobs (file content), trees (folders), commits (snapshots) |
| `refs/` | Stores references to branches and tags |
| `HEAD` | Points to the current branch or commit |
| `config` | Repository configuration |
| `index` | Staging area for files added with `git add` |

---

## Exploring Git Objects

### 1. Find the Latest Object Hash
Find the latest object hash within the `.git/objects/` directory and print the type and content:
```bash
git log --pretty=format:"%H" -n 1
```

### 2. Show the Type of the Commit
```bash
git cat-file -t <commit-hash>
```

### 3. Display Commit Content
```bash
git cat-file -p <commit-hash>
```

## Dumping Directory Tree

### 5. List Files in the Tree Recursively
Use Git commands to dump the directory tree referenced by this commit:
```bash
git ls-tree -r <tree-hash>
```

### 6. Dump Contents of `lib/` Directory and `hello.sh`
To explore the `lib/` directory structure:
```bash
git cat-file -p <lib-tree-hash>
```
Show content of a file (hello.sh):
```bash
git cat-file -p <blob-hash-of-hello.sh>
```
