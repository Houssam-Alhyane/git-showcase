## Branching

### Overview
It's time to do a major rewrite of the hello world functionality. Since this might take a while, you'll want to put these changes into a separate branch to isolate them from changes in the main branch.

---

## Create and Switch to New Branch

### 1. Create and Switch to Branch `greet`
Create a local branch named `greet` and switch to it:
```bash
git checkout -b greet
```

### 2. Create `lib/greeter.sh`
In the `lib` directory, create a new file named `greeter.sh` and add the following code:
```bash
#!/bin/bash

Greeter() {
    who="$1"
    echo "Hello, $who"
}
```

Commit these changes:
```bash
git add lib/greeter.sh
git commit -m "Add greeter function"
```

---

## Update Existing Files

### 3. Update `lib/hello.sh`
Update the `lib/hello.sh` file with the content below to use the greeter function:
```bash
#!/bin/bash

source lib/greeter.sh

name="$1"
if [ -z "$name" ]; then
    name="World"
fi

Greeter "$name"
```

Stage and commit the changes:
```bash
git add lib/hello.sh
git commit -m "Rewrite hello using greeter"
```

### 4. Update `Makefile`
Update the `Makefile` with the following comment:
```makefile
# Ensure it runs the updated lib/hello.sh file
TARGET="lib/hello.sh"

run:
	bash ${TARGET}
```

Commit the changes:
```bash
git add Makefile
git commit -m "Update Makefile comment"
```

---

## Compare Branches

### 5. Switch Back to Main Branch
```bash
git checkout main
```

### 6. Show Differences Between Branches
Compare and show the differences between the `main` and `greet` branches:
```bash
git diff main..greet -- Makefile
git diff main..greet -- lib/hello.sh
git diff main..greet -- lib/greeter.sh
```

---

## Add Documentation

### 7. Generate `README.md`
Create a `README.md` file for the project with the following content:
```markdown
This is the Hello World example from the git project.
```

Commit this file:
```bash
git add README.md
git commit -m "Add README"
```

---

## Visualize Branch History

### 8. Draw Commit Tree Diagram
Draw a commit tree diagram illustrating the diverging changes between all branches to demonstrate the branch history:
```bash
git log --all --graph  --oneline
```

**Visual representation:**
```
* (greet) Update Makefile comment
* Rewrite hello using greeter
* Add greeter function
| * (main) Add README
|/
* Add Makefile to run hello.sh
* Move hello.sh to lib/ directory
* Add author information
* ...
```