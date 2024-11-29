# Git Commands Guide

This guide provides a comprehensive list of Git commands, from initializing a repository to collaboration and deployment. It includes both basic and advanced workflows for managing and pushing your code to GitHub.

---

### **1. Setting Up the Project (First Time Initialization)**

#### a. **Initialize a New Git Repository**

```bash
git init
```

- Creates a new Git repository in the current directory.

#### b. **Configure Git (First Time)**

```bash
git config --global user.name "Your Name"
git config --global user.email "youremail@example.com"
```

- Set your username and email for commits.

#### c. **Create and Stage Files**

```bash
touch README.md  # or any file you want to create
git add README.md
```

- `git add` stages the file for the next commit.

#### d. **Make the First Commit**

```bash
git commit -m "Initial commit"
```

- Commits the staged files with a message.

#### e. **Link to GitHub Remote Repository**

```bash
git remote add origin https://github.com/yourusername/yourproject.git
```

- Links your local repository to a remote repository on GitHub.

#### f. **Push to GitHub**

```bash
git push -u origin master
```

- Pushes changes to the remote repository.

---

### **2. Working on Your Project (Making Changes)**

#### a. **Check the Status of the Repository**

```bash
git status
```

- Shows changes made in the working directory and staging area.

#### b. **Stage Changes**

```bash
git add .             # Add all changes
git add <file>        # Add a specific file
```

#### c. **Make a Commit**

```bash
git commit -m "Description of the changes"
```

- Commits the staged changes.

#### d. **View Commit History**

```bash
git log
```

- Shows the commit history.

#### e. **View Differences (Before Committing)**

```bash
git diff
```

- Shows differences between working directory and the last commit.

---

### **3. Branching (Feature Development)**

#### a. **Create and Switch to a New Branch**

```bash
git checkout -b feature-branch
```

- Creates and switches to a new branch.

#### b. **Switch Between Branches**

```bash
git checkout master        # Switch to master branch
git checkout feature-branch  # Switch to feature branch
```

#### c. **List All Branches**

```bash
git branch
```

- Lists all branches in the repository.

#### d. **Delete a Branch**

```bash
git branch -d feature-branch  # Delete after merging
git branch -D feature-branch  # Force delete
```

---

### **4. Merging Changes**

#### a. **Merge a Branch into Another**

```bash
git checkout master        # Switch to the branch you want to merge into
git merge feature-branch   # Merge feature branch into master
```

#### b. **Resolve Merge Conflicts**

```bash
# Manually resolve conflicts in files
git add <file>  # After resolving conflicts
git commit -m "Resolved merge conflicts"
```

---

### **5. Collaborating with Others**

#### a. **Fetch Changes from Remote**

```bash
git fetch origin
```

- Fetches changes from the remote repository.

#### b. **Pull Changes and Merge**

```bash
git pull origin master
```

- Fetches and merges the latest changes from `master` branch.

#### c. **Push Your Changes**

```bash
git push origin feature-branch  # Push your current branch
```

- Push your local changes to the remote repository.

---

### **6. Pull Requests (GitHub)**

#### a. **Create a Pull Request (PR)**

1. Push your feature branch to GitHub.
2. Navigate to the repository on GitHub, open a PR.
3. Review and merge the PR once approved.

#### b. **Merge a Pull Request Locally**

```bash
git checkout master
git pull origin master
```

- Merges the latest changes from `master` into your local branch.

---

### **7. Tagging Versions**

#### a. **Create a Tag for a Release**

```bash
git tag -a v1.0 -m "First release"
```

- Tags a commit with a version label.

#### b. **Push Tags to Remote**

```bash
git push origin v1.0
git push --tags
```

- Pushes a specific tag or all tags to the remote repository.

---

### **8. Undoing Changes**

#### a. **Undo Changes in a File (Before Committing)**

```bash
git checkout -- <file>
```

- Discards changes in a specific file.

#### b. **Unstage Files**

```bash
git reset <file>
```

- Removes a file from the staging area.

#### c. **Amend the Last Commit**

```bash
git commit --amend
```

- Modify the previous commit (message or files).

#### d. **Remove the Last Commit (Soft Reset)**

```bash
git reset --soft HEAD~1
```

- Removes the last commit but keeps the changes in your working directory.

#### e. **Discard All Local Changes (Dangerous!)**

```bash
git reset --hard
```

- Discards all local changes and resets to the last commit.

---

### **9. Cloning an Existing Repository**

```bash
git clone https://github.com/username/project.git
cd project
```

- Clones an existing repository to your local machine.

---

### **10. Removing a Remote Repository**

```bash
git remote remove origin
```

- Removes the link to the remote repository.

---

### **Summary of Key Git Commands**

| **Operation**          | **Command**                                  |
| ---------------------- | -------------------------------------------- |
| **Initialize Repo**    | `git init`                                   |
| **Set Username/Email** | `git config --global user.name`              |
| **Add Files**          | `git add <file>`                             |
| **Commit Changes**     | `git commit -m "message"`                    |
| **Create Branch**      | `git checkout -b <branch>`                   |
| **Switch Branch**      | `git checkout <branch>`                      |
| **Merge Branches**     | `git merge <branch>`                         |
| **Push Changes**       | `git push origin <branch>`                   |
| **Pull Changes**       | `git pull origin <branch>`                   |
| **Fetch Changes**      | `git fetch origin`                           |
| **View Log**           | `git log`                                    |
| **Tag Release**        | `git tag -a <tag> -m "message"`              |
| **View Status**        | `git status`                                 |
| **Undo Changes**       | `git reset --hard`, `git checkout -- <file>` |
| **Remove Remote**      | `git remote remove origin`                   |

---
