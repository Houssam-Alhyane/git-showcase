## History and Logs

### Show Full Commit History

```bash
git log
```

### Show One-Line Condensed History

```bash
git log --oneline
```

### Show Last 2 Commits Only

```bash
git log -n 2 --oneline
```

### Show Commits from Last 5 Minutes

```bash
git log --since="5 minutes ago" --oneline
```

### Show Personalized Log Format

```bash
git log --pretty=format:"%h %ad | %s %d [%an]" --date=short
```

**Explanation:**

* `%h` → short commit hash (7 characters)
* `%ad` → commit date
* `%s` → commit message
* `%d` → ref names (branches, tags)
* `%an` → author name
