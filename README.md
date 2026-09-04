# Data-Quality-Radar
A beginner-friendly Claude Skill for detecting, safely cleaning, and reporting common data-quality issues in Excel datasets.
# 🔎 Data Quality Radar

> A beginner-friendly Claude Skill for detecting, safely cleaning, and reporting common data-quality issues in Excel datasets.

![Project Overview](https://github.com/Nitu-Singhz/Data-Quality-Radar/blob/main/Screenshot%202026-09-04%20005621.png?raw=true)

## 📌 About the Project

**Data Quality Radar** is a mini project I built as part of the **Codebasics "Claude in 60 Minutes" Challenge**.

The session introduced different Claude capabilities such as **Projects, Connectors, Skills, Workflows, and working with files and data**.

For the challenge, I chose to explore **Claude Skills** by building a small, practical data-quality workflow.

The goal was to take a messy Excel dataset, identify common quality problems, safely clean the issues that are clear, and flag anything that requires human review.

---

## 🎯 Problem

Messy datasets can contain issues that affect analysis and decision-making, such as:

* Duplicate records
* Inconsistent country names
* Mixed date formats
* Missing values
* Numbers stored as text
* Inconsistent categories
* Negative or suspicious values
* Ambiguous values such as `2.5k`

Manually checking these issues can be repetitive and time-consuming.

---

## 💡 Solution

I created a Claude Skill called **Data Quality Radar** that follows a simple workflow:

```text
Messy Excel Data
       ↓
     Inspect
       ↓
   Detect Issues
       ↓
  Safe Cleaning
       ↓
Flag Uncertain Issues
       ↓
Cleaned Dataset + Report
```

### Core principle

> **Automate what is certain. Flag what is uncertain. Never invent data.**

---

## ⚙️ What the Skill Does

The Skill can identify and handle:

| Data Issue               | Approach                          |
| ------------------------ | --------------------------------- |
| Duplicate rows           | Remove exact duplicates           |
| Country inconsistencies  | Standardize clear equivalents     |
| Date formats             | Normalize unambiguous dates       |
| Missing values           | Flag for review                   |
| Numbers stored as text   | Convert when clearly numeric      |
| Negative revenue         | Preserve and flag                 |
| Ambiguous shorthand      | Preserve/flag when uncertain      |
| Category inconsistencies | Standardize clear variations      |
| Column names             | Standardize when meaning is clear |

The original dataset is **never overwritten**. The workflow works on a separate copy and generates new output files.

---

## 🧪 Testing

I intentionally created a messy sales dataset containing multiple data-quality problems.

### Example issues

* Duplicate records
* `India`, `IND`, `IN`
* Different date formats
* Missing dates
* Text-based revenue values
* Negative revenue
* Values such as `2.5k`
* Inconsistent category capitalization

### Input

![messy dataset](https://github.com/Nitu-Singhz/Data-Quality-Radar/blob/main/messy%20dataset.png?raw=true)

---

## 📊 Results

The Skill generated two main outputs:

### 1. Cleaned Dataset

A separate Excel file containing the high-confidence corrections.

[View the cleaned dataset](outputs/Data_Quality_Radar_Cleaned.xlsx)

### 2. Data Quality Report

A report containing:

* Rows and columns inspected
* Exact duplicates removed
* Automatic cleaning performed
* Missing values
* Issues requiring manual review

[View the quality report](outputs/Data_Quality_Radar_Report.xlsx)

---

## 🔍 Example of Safe Data Handling

One of the most important parts of the project was handling uncertainty.

For example, a date such as:

`05/01/2024`

could represent different dates depending on whether the dataset uses day-first or month-first formatting.

Instead of guessing, the Skill flags the value for review.

Similarly, negative revenue values are not automatically changed because they could represent refunds, reversals, or legitimate adjustments.

---

## 🐛 Testing & Improvement

During testing, I discovered a potential issue where genuinely ambiguous dates could be interpreted incorrectly.

Instead of accepting the output, I reviewed the Skill logic and improved the date-handling approach so that ambiguous dates are **flagged for human review rather than silently guessed**.

This was one of my key learnings from the project:

> **AI automation should also be tested and validated — not just executed.**

![Testing and Improvement](screenshots/07-testing-and-improvement.png)

---

## 📸 Project Screenshots

### Skill Creation

![Skill Creation](screenshots/02-skill-creation.png)

### Skill Workflow

![Skill Workflow](screenshots/03-skill-workflow.png)

### Messy Input Data

![Messy Dataset](screenshots/04-messy-dataset.png)

### Cleaned Output

![Cleaned Dataset](screenshots/05-cleaned-dataset.png)

### Quality Report

![Quality Report](screenshots/06-quality-report.png)

---

## 📁 Repository Structure

```text
data-quality-radar/
│
├── skill/
│   └── SKILL.md
│
├── data/
│   ├── Data_Quality_Radar_Test_Data.xlsx
│   └── Data_Quality_Radar_Test_2.xlsx
│
├── outputs/
│   ├── Data_Quality_Radar_Cleaned.xlsx
│   └── Data_Quality_Radar_Report.xlsx
│
├── screenshots/
│   ├── 01-claude-session.png
│   ├── 02-skill-creation.png
│   ├── 03-skill-workflow.png
│   ├── 04-messy-dataset.png
│   ├── 05-cleaned-dataset.png
│   ├── 06-quality-report.png
│   └── 07-testing-and-improvement.png
│
├── presentation/
│   └── Data_Quality_Radar_Presentation.pptx
│
└── README.md
```

---

## 🛠️ Tools Used

* **Claude** — Skill creation and execution
* **ChatGPT** — Prompt and workflow planning
* **Microsoft Excel** — Dataset and output files
* **GitHub** — Project documentation and version control

---

## 📚 What I Learned

Through this project, I learned how a Claude Skill can turn a repeated task into a **reusable workflow**.

More importantly, I learned that AI automation should not blindly modify data. Clear issues can be automated, while uncertain cases should remain visible for human review.

### Key takeaway

> **Automate what is certain. Flag what is uncertain. Never invent data.**

---

## 🙌 Acknowledgement

This project was created as part of the **Codebasics "Claude in 60 Minutes" Challenge**.

The challenge gave me an opportunity to move from simply learning about Claude's capabilities to actually building and testing a small practical workflow.
