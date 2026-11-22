# Web Engineering — Laboratory # 08
## CSS Grid Layouts & Git/GitHub Version Control

**University of Engineering and Technology (UET) Taxila**  
**Department of Software Engineering**  
**Course Instructor:** Engr. Sidra Shafi  

### 👤 Student Information
* **Student Name:** Ahsan Choudhry
* **Registration Number:** 24-SE-80
* **Email:** ahsanchoudhry490@gmail.com
* **GitHub Profile:** [https://github.com/Ahsa6117](https://github.com/Ahsa6117)
* **GitHub Repository:** [https://github.com/Ahsa6117/Lab8_WE_Git](https://github.com/Ahsa6117/Lab8_WE_Git)

---

## 📋 Course Learning Outcomes (CLOs) Mapping

| CLO No. | Learning Outcome | BT Level | PLO | Assessment Item |
| :---: | :--- | :---: | :---: | :--- |
| **CLO 1** | Design web pages for given scenarios. | P2 | 3 | Lab Task, Mid Exam, Semester Project |
| **CLO 2** | Use latest tools and techniques for solving given scenarios. | P3 | 5 | Lab Task, Mid Exam, Final Exam, Semester Project |
| **CLO 3** | Demonstrate an original solution for given scenarios. | A3 | 8 | Lab Task, Semester Project |

---

## 📁 Repository & Project File Structure

```text
WE_Lab08/
├── Ecommerce_header.html       # Primary Lab Task 1 Submission: Responsive E-Commerce Product Gallery
├── index.html                  # Main Web Portal & Live Showcase for VS Code Live Server
├── style.css                   # Custom Stylesheet: CSS Grid Auto-Fit & 3D Card Hover Animations
├── dashboard.html              # Guided Exercise 1: CSS Grid Template Areas Dashboard
├── dashboard_style.css         # Stylesheet for Guided Exercise 1 (Named Areas)
├── dashboard_line_based.html   # Approach 2: Line-Based Spanning Grid (Pages 7-8)
├── .gitignore                  # Git Ignore configuration for clean repository tracking
└── README.md                   # Complete Documentation, Mathematical Breakdown & Git Verification
```

---

## 🎯 Lab Tasks Breakdown (Marks: 6 + 4 = 10)

### 🛒 Lab Task 1: Responsive E-Commerce Product Gallery with CSS Grid & Auto-Fit (6 Marks)

#### Task Description
> Create an auto-responsive product grid (**mincard width 250px**) using `minmax()` and `auto-fit` **without using explicit media queries**. Include cards with **hover animations**.

#### Technical Implementation & Mathematical Logic:
1. **Container Activation & Track Sizing:**
   ```css
   .product-grid {
     display: grid;
     grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
     gap: 26px;
   }
   ```
2. **Why Auto-Fit without Media Queries Works:**
   * `auto-fit`: Calculates how many tracks of minimum size `250px` fit into the parent container's current width.
   * `minmax(250px, 1fr)`: Ensures each card never shrinks below `250px`. If extra horizontal space remains after placing columns, the `1fr` (fractional unit) stretches every column equally to fill the entire container row.
   * **Zero Media Queries:** Because the browser recalculates the number of tracks automatically upon window resize, no `@media (max-width: ...)` rules are needed for the product grid layout.
3. **Card Hover Animations:**
   * **3D Elevation Lift:** `transform: translateY(-8px);`
   * **Layered Dynamic Box Shadow:** `box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.12), 0 8px 10px -6px rgba(0, 0, 0, 0.08);`
   * **Image Scale Zoom:** `transform: scale(1.08);` with `overflow: hidden;` on the parent image wrapper.
   * **Animated Quick View Button:** Slides up into view smoothly with `transform: translate(-50%, 0); opacity: 1;`.
   * **Interactive Add-to-Cart Buttons:** Micro-interaction lift with glowing shadow.

---

### 🐙 Lab Task 2: Git & GitHub Remote Setup (4 Marks)

#### Task Description
> Upload the above created web page to a GitHub Repository using Git and Local Repository.  
> *Note: Your GitHub repository must contain an Html page, a style sheet and Readme File.*

#### Complete Terminal Command History:

```bash
# 1. Configure Global Git Identity
git config --global user.name "Ahsan Choudhry"
git config --global user.email "ahsanchoudhry490@gmail.com"

# 2. Initialize Local Git Repository
cd C:\Users\User\Desktop\SCD_Lab06\WE_Lab08
git init

# 3. Create .gitignore File
echo "node_modules/.DS_Store" > .gitignore

# 4. Check Tracking Status & Stage Files
git status
git add .

# 5. Commit Staged Files with Descriptive Message
git commit -m "Initial commit: Responsive E-Commerce Product Gallery with CSS Grid & Auto-Fit"

# 6. Rename Default Branch to Main
git branch -M main

# 7. Create Remote Repository on GitHub & Link
gh repo create Ahsa6117/Lab8_WE_Git --public --source=. --remote=origin --push

# 8. Feature Branching Workflow (as taught on Page 15)
git checkout -b lab9_WE
git push -u origin lab9_WE
git switch main

# 9. Verify Final Upload Status
git status
git log --oneline
```

---

## 📊 In-Lab Guided Exercises (Pages 2–8)

### Guided Exercise 1: Responsive Dashboard Layout
* **HTML Structure:** Uses semantic elements: `<header>`, `<aside>`, `<main>`, `<section>`, `<footer>`.
* **CSS Grid Template Areas:**
  ```css
  .dashboard-container {
    display: grid;
    grid-template-columns: 240px 1fr 1fr;
    grid-template-rows: 70px minmax(300px, auto) 180px 50px;
    grid-template-areas:
      "header header header"
      "sidebar main main"
      "sidebar widget-a widget-b"
      "footer footer footer";
    gap: 15px;
  }
  ```
* **Mobile Responsive Breakpoint (`@media (max-width: 768px)`):** Stacks all named areas into a single column (`grid-template-columns: 1fr`).

### Guided Exercise 2: Line-Based Positioning & Spanning (Pages 7–8)
* Demonstrates alternative grid alignment using explicit line numbers:
  * `.header { grid-column: 1 / 4; }`
  * `.sidebar { grid-column: 1 / 2; grid-row: 2 / 4; }`
  * `.main-content { grid-column: 2 / 4; }`
  * `.widget-a { grid-column: 2 / 3; }`
  * `.widget-b { grid-column: 3 / 4; }`
  * `.footer { grid-column: 1 / 4; }`

---

## 🚀 How to Run in Visual Studio Code

1. **Open Folder in VS Code:**
   * Launch Visual Studio Code.
   * Go to **File &rarr; Open Folder...** and select `C:\Users\User\Desktop\SCD_Lab06\WE_Lab08`.
2. **Launch with Live Server:**
   * Right-click on `Ecommerce_header.html` or `index.html`.
   * Click **"Open with Live Server"** (or press `Alt + L, Alt + O`).
   * The web page will automatically open in your default browser at `http://127.0.0.1:5500`.
3. **Test Responsive Auto-Fit:**
   * Drag your browser window from full screen (1920px) down to mobile width (375px).
   * Observe how the product grid seamlessly adjusts from 4 columns to 3, 2, and 1 column without any sudden media query jumps.
