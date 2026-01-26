## Moving Files

### Moving hello.sh
Using Git commands, move the program `hello.sh` into a `lib/` directory, and then commit the move.

#### Move Script to lib/ Directory
```bash
git mv hello.sh lib/
git commit -m "Move hello.sh to lib/ directory"
```

### Create Makefile
Create a `Makefile` in the root directory of the repository with the following content and commit it to the repository:
```makefile
TARGET="lib/hello.sh"

run:
	bash ${TARGET}
```

#### Add and Commit Makefile
```bash
git add Makefile
git commit -m "Add Makefile to run hello.sh"
```