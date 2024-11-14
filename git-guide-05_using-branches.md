# Git Branching Operations Guide

## Basic Branch Commands and Flags

### Creating and Switching Branches
The most common command for creating a new branch is:
```bash
git checkout -b feature-branch
```
This single command does two operations:
1. Creates a new branch named "feature-branch"
2. Switches to that branch immediately

It's equivalent to running these two commands:
```bash
git branch feature-branch    # Creates the branch
git checkout feature-branch  # Switches to the branch
```

### Modern Alternative: The `switch` Command
Newer versions of Git provide the `switch` command as a clearer alternative:
```bash
git switch -c feature-branch   # -c flag creates new branch
```

### Branch Management Flags
- `-d` (Safe Delete):
  ```bash
  git branch -d old-branch  # Deletes only if changes are merged
  ```

- `-D` (Force Delete):
  ```bash
  git branch -D abandoned-branch  # Deletes even if not merged
  ```

- `-m` (Rename):
  ```bash
  git branch -m new-name  # Renames current branch
  ```

- `-M` (Force Rename):
  ```bash
  git branch -M main  # Forces rename even if target exists
  ```

## Complete Branch Workflow Examples

### Local Development Workflow
```bash
# 1. Create and switch to a feature branch
git checkout -b new-feature

# 2. Do work and commit changes
# (make changes to files)
git add .
git commit -m "Added new feature"

# 3. Switch back to main branch
git checkout main

# 4. Get any recent updates from main
git pull origin main

# 5. Merge your feature branch into main
git merge new-feature

# 6. After successful merge, delete the feature branch
git branch -d new-feature
```

### Team-Based Workflow with Pull Requests
```bash
# 1. Create and switch to feature branch
git checkout -b new-feature

# 2. Do work and commit
git add .
git commit -m "Added new feature"

# 3. Push feature branch to GitHub
git push -u origin new-feature

# 4. Create Pull Request on GitHub
# 5. After PR is reviewed and merged...

# 6. Switch to main and get the merged changes
git checkout main
git pull origin main

# 7. Delete local feature branch
git branch -d new-feature

# 8. Delete remote feature branch (optional)
git push origin --delete new-feature
```

## Important Notes

- Always ensure your main branch is up to date before creating a new feature branch
- The `-d` flag will fail if you try to delete a branch that hasn't been merged
- Use `-D` with caution as it can delete unmerged work
- Pull Requests are recommended for team settings to facilitate code review
- Regular commits and pushes to your feature branch can serve as backups of your work

## Best Practices

1. Use descriptive branch names that indicate the purpose of changes
   - Good: `feature-user-authentication`
   - Bad: `new-stuff`

2. Regularly sync your feature branch with main to avoid major merge conflicts
   ```bash
   git checkout feature-branch
   git merge main
   ```

3. Delete branches after they're merged to keep repository clean

4. Always create a new branch for new features or fixes

---
*Note: Replace branch names (feature-branch, new-feature, etc.) with meaningful names related to your specific changes.*
