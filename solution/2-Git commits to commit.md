## Git Commits to Commit

Within the `work` directory, establish a subdirectory named `hello`. Inside this directory, generate a file titled `hello.sh` with the following content:

```bash
echo "Hello, World"
```

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
```

```bash
git commit -m "my first commit"
```

```bash
git status
```

### Modify hello.sh to Accept Argument

Change the content of `hello.sh` to:

```bash
#!/bin/bash

echo "Hello, $1"
```

```bash
git add hello.sh
```

```bash
git commit -m "Update hello.sh to accept argument"
```

### Final Modification Using Interactive Staging (`git add -p`)

Modify `hello.sh` to include comments and default value:

```bash
#!/bin/bash
# Default is "World"
name=${1:-"World"}
echo "Hello, $name"
```

Stage interactively:

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
```

```bash
git commit -m "Add default value logic for name"
```
