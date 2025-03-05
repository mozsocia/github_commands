Here’s a comprehensive list of **Git branch-related commands** that will help you create, manage, and work with branches in your repository:

---

### 1. **List All Branches**
To see all branches in your repository:
```bash
git branch
```
- Local branches will be listed, and the current branch will be highlighted with an asterisk (`*`).
- To include remote branches, use:
  ```bash
  git branch -a
  ```

---

### 2. **Create a New Branch**
To create a new branch:
```bash
git branch <branch-name>
```
For example:
```bash
git branch feature-login
```

---

### 3. **Switch to a Branch**
To switch to an existing branch:
```bash
git checkout <branch-name>
```
For example:
```bash
git checkout feature-login
```

---

### 4. **Create and Switch to a New Branch**
To create a new branch and switch to it in one command:
```bash
git checkout -b <branch-name>
```
For example:
```bash
git checkout -b feature-login
```

---

### 5. **Delete a Branch**
To delete a branch:
```bash
git branch -d <branch-name>
```
For example:
```bash
git branch -d feature-login
```
- Use `-D` (uppercase) to force delete a branch that hasn’t been merged:
  ```bash
  git branch -D <branch-name>
  ```

---

### 6. **Rename a Branch**
To rename the current branch:
```bash
git branch -m <new-branch-name>
```
To rename a specific branch:
```bash
git branch -m <old-branch-name> <new-branch-name>
```

---

### 7. **Merge a Branch**
To merge a branch into the current branch:
```bash
git merge <branch-name>
```
For example:
```bash
git checkout main
git merge feature-login
```

---

### 8. **Rebase a Branch**
To rebase the current branch onto another branch:
```bash
git rebase <branch-name>
```
For example:
```bash
git checkout feature-login
git rebase main
```

---

### 9. **Push a Branch to Remote**
To push a local branch to a remote repository:
```bash
git push -u <remote-name> <branch-name>
```
For example:
```bash
git push -u origin feature-login
```
- The `-u` flag sets the upstream tracking reference, so future pushes can be done with just `git push`.

---

### 10. **Track a Remote Branch**
To track a remote branch and create a local branch:
```bash
git checkout --track <remote-name>/<branch-name>
```
For example:
```bash
git checkout --track origin/feature-login
```

---

### 11. **Delete a Remote Branch**
To delete a remote branch:
```bash
git push <remote-name> --delete <branch-name>
```
For example:
```bash
git push origin --delete feature-login
```

---

### 12. **List Merged Branches**
To list branches that have been merged into the current branch:
```bash
git branch --merged
```

---

### 13. **List Unmerged Branches**
To list branches that have not been merged into the current branch:
```bash
git branch --no-merged
```

---

### 14. **Compare Branches**
To see the difference between two branches:
```bash
git diff <branch1>..<branch2>
```
For example:
```bash
git diff main..feature-login
```

---

### 15. **Stash Changes and Switch Branches**
If you have uncommitted changes and want to switch branches, you can stash your changes:
```bash
git stash
git checkout <branch-name>
```
To reapply the stashed changes later:
```bash
git stash pop
```

---

### 16. **Reset a Branch to a Specific Commit**
To reset a branch to a specific commit (use with caution):
```bash
git reset --hard <commit-hash>
```
For example:
```bash
git reset --hard abc1234
```

---

### 17. **Create a Branch from a Specific Commit**
To create a new branch from a specific commit:
```bash
git branch <new-branch-name> <commit-hash>
```
For example:
```bash
git branch hotfix-branch abc1234
```

---

### 18. **View Branch History**
To view the commit history of a branch:
```bash
git log <branch-name>
```
For example:
```bash
git log feature-login
```

---

### 19. **Checkout a Remote Branch**
To checkout a remote branch as a local branch:
```bash
git checkout -b <local-branch-name> <remote-name>/<remote-branch-name>
```
For example:
```bash
git checkout -b feature-login origin/feature-login
```

---

### 20. **Pull Latest Changes into a Branch**
To pull the latest changes from the remote branch into your current branch:
```bash
git pull <remote-name> <branch-name>
```
For example:
```bash
git pull origin main
```

---

### Summary of Common Branch Commands
| Command                                      | Description                                      |
|----------------------------------------------|--------------------------------------------------|
| `git branch`                                 | List local branches                              |
| `git branch -a`                              | List all branches (local and remote)             |
| `git branch <branch-name>`                   | Create a new branch                              |
| `git checkout <branch-name>`                 | Switch to a branch                               |
| `git checkout -b <branch-name>`              | Create and switch to a new branch                |
| `git branch -d <branch-name>`                | Delete a branch                                  |
| `git branch -D <branch-name>`                | Force delete a branch                            |
| `git branch -m <new-branch-name>`            | Rename the current branch                        |
| `git merge <branch-name>`                    | Merge a branch into the current branch           |
| `git rebase <branch-name>`                   | Rebase the current branch onto another branch    |
| `git push -u <remote> <branch>`              | Push a branch to a remote repository             |
| `git push <remote> --delete <branch>`        | Delete a remote branch                           |
| `git branch --merged`                        | List merged branches                             |
| `git branch --no-merged`                     | List unmerged branches                           |
| `git diff <branch1>..<branch2>`              | Compare two branches                             |
| `git stash`                                  | Stash changes before switching branches          |
| `git reset --hard <commit>`                  | Reset a branch to a specific commit              |
| `git log <branch>`                           | View commit history of a branch                  |

Let me know if you need further clarification or examples! 😊