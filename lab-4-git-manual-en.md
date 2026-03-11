# LAB 4
## Version Control System — Git

---

# 1. Introduction

Git is a **distributed version control system** used to track file changes and coordinate work among multiple developers.

Git allows developers to:

- Track project history
- Revert to previous versions
- Work on multiple features simultaneously
- Collaborate through platforms such as GitHub

Git is widely used in **software development, research, DevOps, and data science**.

---

# 2. Prerequisites

Before starting this laboratory work ensure that:

- Git is installed
- A code editor is installed (VS Code recommended)
- You know basic terminal commands
- You have a GitHub account

Recommended tools:

| Tool | Purpose |
|-----|------|
| Git | Version control |
| VS Code | Code editor |
| Terminal | Command execution |
| GitHub | Remote repositories |

---

# 3. Git Installation

## Windows

1. Go to:

```
https://git-scm.com
```

2. Download **Git for Windows**
3. Install using default settings

Verify installation:

```bash
git --version
```

---

## Linux

### Ubuntu / Debian

```bash
sudo apt update
sudo apt install git
```

### Fedora

```bash
sudo dnf install git
```

### Arch Linux

```bash
sudo pacman -S git
```

Verify installation:

```bash
git --version
```

---

## macOS

Using Homebrew:

```bash
brew install git
```

Or install Xcode tools:

```bash
xcode-select --install
```

Verify installation:

```bash
git --version
```

---

# 4. Git Configuration

Before using Git configure your identity:

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

Check configuration:

```bash
git config --list
```

---

# 5. Git Internals

Git stores project data as **snapshots**, not differences.

## Git Object Model

```
Commit
  │
  ├── Tree (directory)
  │      ├── File A (blob)
  │      └── File B (blob)
  │
  └── Parent Commit
```

Git object types:

| Object | Description |
|------|-------------|
| Blob | File data |
| Tree | Directory |
| Commit | Snapshot |
| Tag | Named reference |

---

# 6. Git Workflow

```
Working Directory
       │
       │ git add
       ▼
Staging Area
       │
       │ git commit
       ▼
Local Repository
       │
       │ git push
       ▼
Remote Repository
```

---

# 7. Lab 1 — Basic Git Workflow

## Create project folder

```bash
mkdir git_lab
cd git_lab
```

Initialize repository:

```bash
git init
```

---

## Create file

```bash
echo "Hello Git" > example.txt
```

Check status:

```bash
git status
```

---

## Add file to staging

```bash
git add example.txt
```

---

## Create commit

```bash
git commit -m "Initial commit"
```

---

## Modify file

```bash
echo "Second line" >> example.txt
```

View changes:

```bash
git diff
```

Commit changes:

```bash
git add example.txt
git commit -m "Update example file"
```

---

## View commit history

```bash
git log
```

---

# 8. Lab 2 — Branching and Merge Conflicts

## Create branch

```bash
git branch feature_branch
```

Check branches:

```bash
git branch
```

---

## Switch branch

```bash
git checkout feature_branch
```

or

```bash
git checkout -b feature_branch
```

---

## Add new file

```bash
echo "Feature file" > feature.txt
```

Commit:

```bash
git add feature.txt
git commit -m "Add feature file"
```

---

## Merge branch

Return to main branch:

```bash
git checkout master
```

Merge:

```bash
git merge feature_branch
```

---

# Merge Conflict Example

```
<<<<<<< HEAD
Master change
=======
Branch change
>>>>>>> feature_branch
```

Resolve conflict:

```bash
git add example.txt
git commit
```

---

# 9. Lab 3 — GitHub and Collaboration

## Create GitHub repository

1. Login to GitHub
2. Click **New Repository**
3. Enter repository name
4. Click **Create Repository**

---

## Clone repository

```bash
git clone https://github.com/username/repository.git
```

Enter project folder:

```bash
cd repository
```

---

## Create file

```bash
echo "GitHub project" > project.txt
```

Commit:

```bash
git add project.txt
git commit -m "Add project file"
```

---

## Push to GitHub

```bash
git push origin master
```

---

## Pull updates

```bash
git pull
```

---

# 10. Branch Visualization Graphs

## Basic history

```
A --- B --- C --- D
```

## Feature branch

```
A --- B --- C --- D
            \
             E --- F
```

## Merge example

```
A --- B --- C -------- G
            \        /
             D ---- E
```

---

# 11. Git Command Cheat Sheet

## Repository

| Command | Description |
|------|-------------|
| git init | Create repository |
| git clone | Download repository |
| git status | Show status |
| git log | Show history |

---

## File Tracking

| Command | Description |
|------|-------------|
| git add | Stage file |
| git diff | Show changes |
| git commit | Save snapshot |

---

## Branching

| Command | Description |
|------|-------------|
| git branch | List branches |
| git checkout | Switch branch |
| git merge | Merge branch |

---

## Remote

| Command | Description |
|------|-------------|
| git pull | Download updates |
| git push | Upload commits |
| git clone | Copy repository |

---

# 12. GitHub Workflow

```
Developer
   │
   ▼
Clone repository
   │
   ▼
Create branch
   │
   ▼
Commit changes
   │
   ▼
Push branch
   │
   ▼
Create Pull Request
   │
   ▼
Code Review
   │
   ▼
Merge to main
```

---

# 13. Screenshot Section

Add screenshots for students.

Example:

```
images/github_create_repo.png
images/github_clone.png
images/github_pull_request.png
```

Markdown example:

```
![Create Repository](images/github_create_repo.png)
```

---

# 14. Exercises for Students

Students must:

1. Install Git
2. Configure Git
3. Create repository
4. Commit files
5. Create branch
6. Merge branches
7. Resolve merge conflict
8. Push project to GitHub
9. Create Pull Request

---

# 15. Best Practices

Students should:

- Write clear commit messages
- Commit small logical changes
- Use branches for features
- Pull before pushing
- Avoid committing temporary files

Example good commit message:

```
Add login validation

- Added email validation
- Added password check
- Updated error messages
```

---

# 16. Expected Results

After completing the laboratory work students should be able to:

- install Git
- configure Git
- create repositories
- commit changes
- work with branches
- resolve merge conflicts
- collaborate using GitHub

---

# 17. Additional Resources

Git Documentation  
https://git-scm.com/docs

Pro Git Book  
https://git-scm.com/book

GitHub Learning Lab  
https://lab.github.com

---

# Conclusion

This laboratory work introduces students to **Git fundamentals, branching, and collaboration workflows**.  
Understanding Git is essential for modern software development and teamwork.
