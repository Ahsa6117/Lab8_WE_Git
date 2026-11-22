# University of Engineering and Technology (UET), Taxila
## Department of Software Engineering
### Web Engineering (WE) — Laboratory Report # 08

---

* **Laboratory Title:** CSS Grid Layouts & Git/GitHub Version Control
* **Course Instructor:** Engr. Sidra Shafi
* **Student Name:** Ahsan Choudhry
* **Registration Number:** 24-SE-80
* **Section / Semester:** SE / 4th Semester
* **Chrome / Git Email:** `ahsanchoudhry490@gmail.com`
* **GitHub Username:** `Ahsa6117`
* **GitHub Repository URL:** [https://github.com/Ahsa6117/Lab8_WE_Git](https://github.com/Ahsa6117/Lab8_WE_Git)
* **Date of Completion:** November 23, 2026

---

## 📋 Table of Contents
1. [Course Learning Outcomes (CLOs) Mapping](#1-course-learning-outcomes-clos-mapping)
2. [Laboratory Objectives & Core Competencies](#2-laboratory-objectives--core-competencies)
3. [Lab Task 1: Responsive E-Commerce Product Gallery with CSS Grid & Auto-Fit (6 Marks)](#3-lab-task-1-responsive-e-commerce-product-gallery-with-css-grid--auto-fit-6-marks)
   - [Architectural Design & CSS Grid Math](#architectural-design--css-grid-math)
   - [Zero-Media-Query Fluid Responsiveness](#zero-media-query-fluid-responsiveness)
   - [Interactive Card Hover Animations](#interactive-card-hover-animations)
   - [Core Code Implementation (`Ecommerce_header.html` & `style.css`)](#core-code-implementation)
4. [Lab Task 2: Git & GitHub Remote Setup (4 Marks)](#4-lab-task-2-git--github-remote-setup-4-marks)
   - [Git State Model & Architecture](#git-state-model--architecture)
   - [Step-by-Step Terminal Execution History](#step-by-step-terminal-execution-history)
   - [Branch Management & Remote Verification](#branch-management--remote-verification)
5. [In-Lab Guided Exercises Analysis (Pages 2–8)](#5-in-lab-guided-exercises-analysis)
   - [Exercise 1: Named Grid Template Areas (`dashboard.html`)](#exercise-1-named-grid-template-areas)
   - [Approach 2: Line-Based Positioning & Spanning (`dashboard_line_based.html`)](#approach-2-line-based-positioning--spanning)
6. [Visual Studio Code Workflow & Verification](#6-visual-studio-code-workflow--verification)
7. [Conclusion & Learning Attainment](#7-conclusion--learning-attainment)

---

## 1. Course Learning Outcomes (CLOs) Mapping

| CLO No. | Learning Outcome | BT Level | PLO | Assessment Item |
| :---: | :--- | :---: | :---: | :--- |
| **CLO 1** | Design web pages for given scenarios. | P2 | 3 | Lab Task, Mid Exam, Semester Project |
| **CLO 2** | Use latest tools and techniques for solving given scenarios. | P3 | 5 | Lab Task, Mid Exam, Final Exam, Semester Project |
| **CLO 3** | Demonstrate an original solution for given scenarios. | A3 | 8 | Lab Task, Semester Project |

---

## 2. Laboratory Objectives & Core Competencies

By completing this laboratory, the following key competencies are attained:
1. **CSS Grid Layout Mastery:**
   - 2D grid container activation using `display: grid;`.
   - Dynamic track definition using fractional units (`fr`), `minmax()`, and automatic placement algorithms (`auto-fit` vs. `auto-fill`).
   - Named template areas (`grid-template-areas` & `grid-area`) vs. line-based numerical spanning (`grid-column: 1 / 4;`).
   - Gutter control using modern shorthand `gap`.
2. **Git & GitHub Version Control Competency:**
   - Understanding Git states: Working Directory &rarr; Staging Area (Index) &rarr; Local Repository (.git) &rarr; Remote Repository (GitHub).
   - Global identity configuration (`user.name` and `user.email`).
   - Local repository initialization (`git init`), staging (`git add`), and committing (`git commit`).
   - Branch renaming (`git branch -M main`) and feature branching (`git checkout -b lab9_WE`).
   - Remote linking (`git remote add origin`), tracking upstream (`git push -u origin main`), and upload status verification (`git status`, `git log --oneline`).

---

## 3. Lab Task 1: Responsive E-Commerce Product Gallery with CSS Grid & Auto-Fit (6 Marks)

### Task Specification:
* **Task Description:** Create an auto-responsive product grid (**mincard width 250px**) using `minmax()` and `auto-fit` **without using explicit media queries**. Include cards with **hover animations**.

### Architectural Design & CSS Grid Math:
The core requirement of Lab Task 1 is achieving responsive, multi-column adaptability strictly through the CSS Grid layout engine without writing any `@media` breakpoint rules for the product grid columns.

```css
.product-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 26px;
}
```

#### Detailed Mathematical Breakdown:
* **`repeat(auto-fit, ...)`:** Tells the browser engine to dynamically determine how many tracks of minimum size `250px` can fit across the available row width. If the viewport allows 4 tracks of 250px plus gaps ($4 \times 250\text{px} + 3 \times 26\text{px} = 1078\text{px}$), 4 columns are created.
* **`minmax(250px, 1fr)`:** 
  - **Minimum bound (`250px`):** Guarantees that no product card is ever compressed narrower than 250px. When the container width shrinks such that 4 columns cannot fit, the 4th card automatically wraps to the next row, leaving 3 columns.
  - **Maximum bound (`1fr`):** The fractional unit causes the remaining unused space in the row to be distributed equally across all active columns, preventing empty gaps and ensuring full edge-to-edge alignment.
* **`auto-fit` vs `auto-fill`:**
  - `auto-fill` creates empty virtual ghost tracks if space permits even if no cards exist.
  - `auto-fit` collapses any empty tracks to 0px, causing existing cards to stretch nicely across the full width.

### Zero-Media-Query Fluid Responsiveness:
| Viewport Width Range | Calculated Columns | Card Width Behavior | Media Queries Used |
| :--- | :---: | :--- | :---: |
| **Large Desktop (> 1200px)** | 4 Columns | ~280px – 320px (stretched equally via 1fr) | **0 (None)** |
| **Laptop / Small Desktop (900px – 1199px)** | 3 Columns | ~280px – 340px (stretched equally via 1fr) | **0 (None)** |
| **Tablet / Phablet (600px – 899px)** | 2 Columns | ~280px – 410px (stretched equally via 1fr) | **0 (None)** |
| **Mobile (< 599px)** | 1 Column | 100% container width (>= 250px) | **0 (None)** |

### Interactive Card Hover Animations:
Each `.product-card` features a synchronized set of hardware-accelerated animations:
1. **3D Elevation Lift:** `transform: translateY(-8px);` using `cubic-bezier(0.34, 1.56, 0.64, 1)` for an elastic physical lift.
2. **Deep Dynamic Drop Shadow:** Shifts from `var(--shadow-sm)` to `0 20px 25px -5px rgba(0, 0, 0, 0.12), 0 8px 10px -6px rgba(0, 0, 0, 0.08)`.
3. **Card Border Highlight:** Border transitions smoothly from `#e2e8f0` to `#cbd5e1`.
4. **Image Scale Zoom:** The product illustration scales smoothly (`transform: scale(1.08);`) within an `overflow: hidden;` container.
5. **Quick-View Action Slide:** An overlay pill slides up into view from beneath (`transform: translate(-50%, 0); opacity: 1;`).
6. **Button Micro-Interactions:** The "Add to Cart" button features a distinct hover elevation (`translateY(-2px)`) and focused colored shadow (`0 4px 10px rgba(37, 99, 235, 0.35)`).

---

## 4. Lab Task 2: Git & GitHub Remote Setup (4 Marks)

### Git State Model & Architecture:
Git operates on four primary data zones:
1. **Working Directory:** Local workspace holding active project files (`Ecommerce_header.html`, `style.css`, `README.md`, etc.).
2. **Staging Area (Index):** Intermediate preparation zone where modified files are indexed using `git add .`.
3. **Local Repository (`.git/`):** Permanent database storing compressed tree objects and commit history created via `git commit`.
4. **Remote Repository (GitHub):** Cloud-hosted repository (`https://github.com/Ahsa6117/Lab8_WE_Git`) for collaboration, evaluation, and backup.

### Step-by-Step Terminal Execution History:

```powershell
# Step 1: Configure Git User Identity (Ahsan Choudhry / ahsanchoudhry490@gmail.com)
$ git config --global user.name "Ahsan Choudhry"
$ git config --global user.email "ahsanchoudhry490@gmail.com"

# Step 2: Initialize Git Repository in Project Folder
$ cd C:\Users\User\Desktop\SCD_Lab06\WE_Lab08
$ git init
Initialized empty Git repository in C:/Users/User/Desktop/SCD_Lab06/WE_Lab08/.git/

# Step 3: Create .gitignore File to Exclude Temporary Files
$ echo "node_modules/.DS_Store" > .gitignore

# Step 4: Check Tracking Status & Stage Files
$ git status
$ git add .

# Step 5: Commit Staged Files with Descriptive Message
$ git commit -m "Initial commit: Responsive E-Commerce Product Gallery with CSS Grid & Auto-Fit"
[master (root-commit) edbf171] Initial commit: Responsive E-Commerce Product Gallery with CSS Grid & Auto-Fit
 8 files changed, 2072 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 Ecommerce_header.html
 create mode 100644 README.md
 create mode 100644 dashboard.html
 create mode 100644 dashboard_line_based.html
 create mode 100644 dashboard_style.css
 create mode 100644 index.html
 create mode 100644 style.css

# Step 6: Rename Default Branch to 'main'
$ git branch -M main

# Step 7: Create Remote GitHub Repository and Push Local Commit
$ gh repo create Ahsa6117/Lab8_WE_Git --public --source=. --remote=origin --push
✓ Created repository Ahsa6117/Lab8_WE_Git on GitHub
  https://github.com/Ahsa6117/Lab8_WE_Git
* [new branch]      HEAD -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.

# Step 8: Create Feature Branch and Push to Remote (as demonstrated on Page 15)
$ git checkout -b lab9_WE
Switched to a new branch 'lab9_WE'
$ git push -u origin lab9_WE
* [new branch]      lab9_WE -> lab9_WE
$ git switch main
Switched to branch 'main'
Your branch is up to date with 'origin/main'.

# Step 9: Verify Upload & Working Tree Status
$ git status
On branch main
Your branch is up to date with 'origin/main'.
nothing to commit, working tree clean

$ git remote -v
origin  https://github.com/Ahsa6117/Lab8_WE_Git.git (fetch)
origin  https://github.com/Ahsa6117/Lab8_WE_Git.git (push)
```

---

## 5. In-Lab Guided Exercises Analysis (Pages 2–8)

### Exercise 1: Named Grid Template Areas (`dashboard.html`)
The guided exercise illustrates how complex dashboard layouts can be mapped semantically using named template areas:
```css
.dashboard-container {
  display: grid;
  grid-template-columns: 240px 1fr 1fr;
  grid-template-rows: 70px minmax(300px, auto) 180px 50px;
  grid-template-areas:
    "header  header   header"
    "sidebar main     main"
    "sidebar widget-a widget-b"
    "footer  footer   footer";
  gap: 15px;
}
```
* **Header:** Spans all 3 columns across row 1.
* **Sidebar:** Spans column 1 vertically across rows 2 and 3.
* **Main Content:** Occupies columns 2 and 3 in row 2 with `minmax(300px, auto)`.
* **Widgets A & B:** Split columns 2 and 3 in row 3 with a fixed height of `180px`.
* **Footer:** Spans all 3 columns across row 4 (`50px`).
* **Mobile Breakpoint (`@media (max-width: 768px)`):** Transforms the grid into `grid-template-columns: 1fr` with single-column vertical stacking.

### Approach 2: Line-Based Positioning & Spanning (`dashboard_line_based.html`)
Demonstrates how the same visual grid can be constructed using explicit coordinate lines:
```css
.header      { grid-column: 1 / 4; }
.sidebar     { grid-column: 1 / 2; grid-row: 2 / 4; }
.main-content{ grid-column: 2 / 4; }
.widget-a    { grid-column: 2 / 3; }
.widget-b    { grid-column: 3 / 4; }
.footer      { grid-column: 1 / 4; }
```

---

## 6. Visual Studio Code Workflow & Verification

1. **Workspace Integration:**
   * Both `C:\Users\User\Desktop\SCD_Lab06\WE_Lab08` and `C:\Users\User\Desktop\WE_Lab08` are created and synchronized.
2. **Execution via Live Server:**
   * In VS Code, open `Ecommerce_header.html` or `index.html`.
   * Click the **"Go Live"** button in the VS Code status bar (or right click &rarr; **"Open with Live Server"**).
   * The live application runs at `http://127.0.0.1:5500`.
3. **Responsive Verification:**
   * Open Developer Tools (`F12` or `Ctrl + Shift + I`).
   * Toggle the Device Toolbar (`Ctrl + Shift + M`).
   * Test across various simulated devices:
     - 4K / Desktop (1920px &rarr; 4+ columns)
     - Laptop (1024px &rarr; 3 columns)
     - Tablet (768px &rarr; 2 columns)
     - Mobile (375px &rarr; 1 column)

---

## 7. Conclusion & Learning Attainment

Through the execution of Web Engineering Laboratory # 08:
* Mastery of modern CSS Grid architecture was achieved, particularly utilizing `repeat(auto-fit, minmax(250px, 1fr))` to deliver fluid, mathematically sound responsive layouts without cumbersome media query chains.
* Professional interactive UX was implemented through smooth CSS transitions and transforms on product cards.
* Complete Git version control proficiency was demonstrated by configuring student credentials (`Ahsan Choudhry` / `ahsanchoudhry490@gmail.com`), establishing clean commits, managing branches, and pushing code to the remote repository on GitHub (`https://github.com/Ahsa6117/Lab8_WE_Git`).
