## Restore Snapshots

### Restore first snapshot of `hello.sh`

```bash
git log --oneline
git checkout <first_commit_hash> -- hello.sh
```

### Restore second most recent snapshot of `hello.sh`

```bash
git log --oneline --all
git checkout <first_commit_hash> -- hello.sh
```

### Return to latest version

```bash
git checkout main -- hello.sh
```