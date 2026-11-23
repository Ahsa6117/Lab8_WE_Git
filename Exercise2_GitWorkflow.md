# Exercise 2: Complete Terminal Workflow for Git Local & GitHub Remote Setup
## Web Engineering — Laboratory # 08 (Pages 9–15)

**Student Name:** Ahsan Choudhry  
**Registration Number:** 24-SE-80  
**Email:** `ahsanchoudhry490@gmail.com`  
**GitHub Account:** [Ahsa6117](https://github.com/Ahsa6117)  
**Remote Repository:** [https://github.com/Ahsa6117/Lab8_WE_Git](https://github.com/Ahsa6117/Lab8_WE_Git)  

---

### 1. Conceptual Architecture & State Model (Pages 8–9)

| Git State / Term | Description | Primary Command |
| :--- | :--- | :--- |
| **Working Directory** | Local workspace containing untracked and modified files. | `git status` |
| **Staging Area (Index)** | Intermediate buffer where changes are selected before committing. | `git add <file>` / `git add .` |
| **Local Repository** | Local database storing committed history (`.git` folder). | `git commit -m "msg"` |
| **Branching** | Isolated line of development for features or bug fixes. | `git branch` / `git checkout -b` |
| **Remote Repository** | Cloud-hosted repository on GitHub for team collaboration. | `git push` / `git pull` |

```
Local Repository ----push----> origin (GitHub)
Local Repository <---pull----- origin (GitHub)
```

---

### 2. Guided Terminal Command Solutions (Page 9)

```bash
# 1. Configure Global User Identity
$ git config --global user.name "Ahsan Choudhry"
$ git config --global user.email "ahsanchoudhry490@gmail.com"

# 2. Initialize Git Repository in Project Folder
$ cd C:\Users\User\Desktop\SCD_Lab06\WE_Lab08
$ git init

# 3. Create .gitignore File to Exclude Temporary Files
$ echo "node_modules/.DS_Store" > .gitignore

# 4. Check Tracking Status & Stage Files
$ git status
$ git add .

# 5. Commit Staged Files with Descriptive Message
$ git commit -m "Feat: Initial commit for responsive CSS Grid dashboard"

# 6. Rename Main Branch & Connect to GitHub Remote
$ git branch -M main
$ git remote add origin https://github.com/Ahsa6117/Lab8_WE_Git.git

# 7. Push Local Commit to GitHub Remote
$ git push -u origin main
```

---

### 3. Step-by-Step Executed & Verified Workflow (Pages 10–15)

#### Step 1: Create New Public Repository on GitHub
Created public repository `Lab8_WE_Git` on GitHub account `Ahsa6117`.

#### Step 2: Configure Username and Email
```bash
git config --global user.name "Ahsan Choudhry"
git config --global user.email "ahsanchoudhry490@gmail.com"
```

#### Step 3: Local Project Folder Navigation
```bash
cd C:\Users\User\Desktop\SCD_Lab06\WE_Lab08
```

#### Step 4: Initialize Git Repository
```bash
git init
# Output: Initialized empty Git repository in C:/Users/User/Desktop/SCD_Lab06/WE_Lab08/.git/
```

#### Step 5: Add Project Files
```bash
git add .
```

#### Step 6: Commit Staged Files
```bash
git commit -m "Initial commit: Responsive E-Commerce Product Gallery with CSS Grid & Auto-Fit"
```

#### Step 7: Rename Default Branch to Main
```bash
git branch -M main
```

#### Step 8: Link Remote GitHub Repository
```bash
git remote add origin https://github.com/Ahsa6117/Lab8_WE_Git.git
git remote -v
# Output:
# origin  https://github.com/Ahsa6117/Lab8_WE_Git.git (fetch)
# origin  https://github.com/Ahsa6117/Lab8_WE_Git.git (push)
```

#### Step 9: Pull Remote Changes with Unrelated Histories (if initialized with README)
```bash
git pull origin main --allow-unrelated-histories
```

#### Step 10: Push Code to GitHub
```bash
git push -u origin main
# Output:
# branch 'main' set up to track 'origin/main'.
# To https://github.com/Ahsa6117/Lab8_WE_Git.git
#  * [new branch]      HEAD -> main
```

#### Step 11: Verify Upload Status via Terminal
```bash
git status
# Output:
# On branch main
# Your branch is up to date with 'origin/main'.
# nothing to commit, working tree clean
```

#### Step 12: Verify Branch Settings & Incremental Commits (Pages 13–14)
Adding `style.css` / updates incrementally:
```bash
git status
git add style.css
git commit -m "style.css"
git push origin main
git log --oneline
```

#### Feature Branching Workflow (Page 15)
```bash
# Creating a new branch and switching to it:
git checkout -b lab9_WE
git status
git branch
# Push branch to remote:
git push -u origin lab9_WE
# Switch back to main:
git switch main
git branch
```

---

### 4. Verification Checkpoints Summary

1. `git status` &rarr; Working tree clean.
2. `git log --oneline` &rarr; Full descriptive commit log present.
3. `git remote -v` &rarr; Linked to `https://github.com/Ahsa6117/Lab8_WE_Git.git`.
4. `git branch -a` &rarr; Both `main` and `lab9_WE` synchronized with origin.
