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
├── index.html                           # Central Navigation Hub & Showcase for VS Code Live Server
├── Ecommerce_header.html                # Lab Task 1 (6 Marks): Responsive E-Commerce Product Gallery
├── style.css                            # Custom Stylesheet: CSS Grid Auto-Fit & 3D Card Hover Animations
├── Exercise1_Dashboard.html             # Guided Exercise 1 (Pages 2–4): Named Grid Template Areas
├── dashboard.html                       # Alternate entry for Guided Exercise 1 Dashboard
├── dashboard_style.css                  # Stylesheet for Guided Exercise 1 (Template Areas)
├── Exercise1_Approach2_LineBased.html   # Exercise 1 Approach 2 (Pages 7–8): Line-Based Grid Spanning
├── dashboard_line_based.html            # Alternate entry for Line-Based Grid Spanning
├── style2.css                           # 2nd Style Sheet (Grid-column & Grid-row as taught on Page 7)
├── Exercise_Grid_Architecture.html      # Part A Architecture & Mathematical Calculation Simulator
├── Exercise2_GitWorkflow.md             # Guided Exercise 2 (Pages 9–15): Terminal Workflow Documentation
├── LAB_REPORT.md                        # Formal Laboratory Report matching UET Taxila standards
├── .gitignore                           # Git exclusion rules for clean repository tracking
└── README.md                            # Comprehensive Readme documentation
```

---

## 🎯 Lab Tasks & Exercises Breakdown

### 🛒 Lab Task 1: Responsive E-Commerce Product Gallery with CSS Grid & Auto-Fit (6 Marks)
* **Task Description:** Create an auto-responsive product grid (**mincard width 250px**) using `minmax()` and `auto-fit` **without using explicit media queries**. Include cards with **hover animations**.
* **Technical Implementation:**
  ```css
  .product-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 26px;
  }
  ```
* **Cards with Hover Animations:**
  * 3D Elevation Lift: `transform: translateY(-8px);`
  * Dynamic Box Shadow: `box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.12);`
  * Product Image Zoom: `transform: scale(1.08);` with `overflow: hidden;`
  * Interactive Quick View Slide & Cart Button Micro-interactions.

---

### 🐙 Lab Task 2: Git & GitHub Remote Setup (4 Marks)
* **Task Description:** Upload the above created web page to a GitHub Repository using Git and Local Repository.
* **Account Used:**
  * **User Name:** Ahsan Choudhry
  * **Email:** `ahsanchoudhry490@gmail.com`
  * **GitHub Handle:** `Ahsa6117`
  * **Repository:** `https://github.com/Ahsa6117/Lab8_WE_Git`
* **Branching Workflow:**
  * `main` &mdash; Production stable branch.
  * `lab9_WE` &mdash; Feature development branch (as demonstrated on Page 15).

---

### 📊 In-Lab Guided Exercises (Pages 2–8)

#### Exercise 1: Responsive Dashboard Layout with CSS Grid (Pages 2–4)
* **HTML Structure:** Header, Sidebar, Main Content Area, Widget A, Widget B, Footer.
* **Grid Template Areas:**
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
* **Mobile Breakpoint:** Stacks all areas vertically via `@media (max-width: 768px)`.

#### Exercise 1: Approach 2 &mdash; Line-Based Positioning & Spanning (Pages 7–8)
* Implemented in `Exercise1_Approach2_LineBased.html` and `style2.css`:
  * `.header { grid-column: 1 / 4; }`
  * `.sidebar { grid-column: 1 / 2; grid-row: 2 / 4; }`
  * `.main-content { grid-column: 2 / 4; }`
  * `.widget-a { grid-column: 2 / 3; }`
  * `.widget-b { grid-column: 3 / 4; }`
  * `.footer { grid-column: 1 / 4; }`

#### Exercise 2: Terminal Workflow for Git Local & GitHub Remote Setup (Pages 9–15)
* Documented with exact command logs in `Exercise2_GitWorkflow.md`.

---

## 🚀 How to Run in Visual Studio Code

1. Open folder `C:\Users\User\Desktop\SCD_Lab06\WE_Lab08` in VS Code.
2. Right-click [index.html](file:///C:/Users/User/Desktop/SCD_Lab06/WE_Lab08/index.html) or [Ecommerce_header.html](file:///C:/Users/User/Desktop/SCD_Lab06/WE_Lab08/Ecommerce_header.html).
3. Click **"Open with Live Server"** (or press `Alt + L, Alt + O`).
4. Resize your browser window to test the fluid auto-fit columns and hover animations!
