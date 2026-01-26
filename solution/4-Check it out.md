## Restore Snapshots

### Restore first snapshot of `hello.sh`

```bash
git checkout <first_commit_hash> -- hello.sh
```

### Restore second most recent snapshot of `hello.sh`

```bash
git checkout HEAD~1 -- hello.sh
```

### Return to latest version

```bash
git checkout main -- hello.sh
```