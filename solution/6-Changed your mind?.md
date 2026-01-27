## Undoing Changes (Changed Your Mind?)

### Reverting Un-staged Changes
Modify `hello.sh` with unwanted comments and revert it back before staging:
```bash
#!/bin/bash
# This is a bad comment. We want to revert it.
name=${1:-"World"}
echo "Hello, $name"
```
```bash
git restore hello.sh
```

### Staging and Cleaning
Introduce unwanted changes, stage them, then discard staged changes:
```bash
#!/bin/bash
# This is an unwanted but staged comment
name=${1:-"World"}
echo "Hello, $name"
```
```bash
git restore --staged hello.sh
git restore hello.sh
```

### Committing and Reverting
Stage and commit unwanted changes, then revert the commit:
```bash
#!/bin/bash
# This is an unwanted but committed change
name=${1:-"World"}
echo "Hello, $name"
```
```bash
git add hello.sh
git commit -m "Add unwanted change"
git revert HEAD
```

### Tagging and Removing Commits
Tag latest commit as oops and reset to v1:
```bash
git tag oops
git reset --hard v1
```
### Displaying Logs with Deleted Commits
```bash
git reflog
```
### Cleaning Unreferenced Commits
```bash
git tag -d oops
git gc --prune=now
```

### Author Information
Add author comment and commit:
```bash
#!/bin/bash
# Default is World
# Author: Jim Weirich
name=${1:-"World"}
echo "Hello, $name"
```
```bash
git add hello.sh
git commit -m "Add author information"
```

### Update Author Email Without Creating New Commit
```bash
# Author: Jim Weirich <jim@ruby-lang.org>
git add hello.sh
git commit --amend --no-edit
```