### Initialize Git Repository

```bash
git init
```

### Check Status

```bash
git status
```

### First Commit (Initial Script)

```bash
git add hello.sh
git commit -m "my first commit"
git status
```

### Modify hello.sh to Accept Argument

```bash
git add hello.sh
git commit -m "Update hello.sh to accept argument"
```

### Final Modification Using Interactive Staging (`git add -p`)

```bash
git add -p hello.sh
```

* Use `e` to edit the hunk
* Stage only the comment line `# Default is "World"`

### First Commit (Comment Only)

```bash
git commit -m "Add default name comment"
```

### Stage Remaining Logic and Commit

```bash
git add hello.sh
git commit -m "Add default value logic for name"
```
