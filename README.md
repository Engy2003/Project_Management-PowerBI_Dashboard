# Project Management Power BI Dashboard

![Dashboard Screenshot](https://github.com/Engy2003/Project_Management-PowerBI_Dashboard/blob/main/Images/Project%20Details.png)

This repository contains the complete Power BI project for a comprehensive Project Management Dashboard. This solution is designed to provide a 360-degree view of project performance, enabling project managers, stakeholders, and teams to track tasks, monitor timelines, and manage budgets effectively.

## 🚀 Business Value & Key Insights

In today's fast-paced environment, data-driven decision-making is critical for project success. This dashboard moves beyond simple spreadsheets to provide actionable insights, solving several key business challenges:

* **Unified Vision:** Consolidates all project data into a single source of truth, eliminating information silos.
* **Proactive Issue Detection:** Instantly identifies blocked tasks, potential delays, and budget risks, allowing teams to take corrective action *before* problems escalate.
* **Financial Accountability:** Provides real-time tracking of `Amount Spent` vs. `Total Budget` at both the project and task level, ensuring financial control.
* **Performance Monitoring:** Empowers managers to assess team workload and project progress through dynamic filters and detailed status breakdowns.
* **Stakeholder Communication:** Simplifies complex project data into clear, easy-to-understand visuals for reports and meetings.

## Interactive Dashboard Tour

The dashboard is organized into three distinct pages, all interconnected and filterable by **Team Member** and **Date**.

### 1. 🗓️ Timeline (Gantt Chart)

This page provides a high-level overview of the project schedule.
* **Gantt Chart:** Visualizes the start, end, and duration of every task within each project, offering a clear map of project timelines and dependencies.

### 2. 📊 Project Details

This page dives deep into task-level metrics and performance analysis.
* **Task Status KPIs:** Donut charts displaying the overall project health via `% Completed`, `% In progress`, and `% Not started` (including blocked tasks).
* **Task Performance Over Time:** A line and stacked column chart showing the volume of total tasks vs. completed tasks by month, quarter, or year.
* **Project Task Breakdown:** A stacked column chart comparing `Total Tasks`, `Completed`, `In Progress`, `Blocked`, and `Not Started` tasks for each project.
* **Root Cause Analysis:** A decomposition tree allows for dynamic analysis of `Total Tasks`, breaking them down by `Project Name`, `Priority`, and `Task Status`.

### 3. 💰 Budget

This page is dedicated to financial health and resource allocation.
* **Top-Level KPIs:** Five key metrics provide an instant financial summary:
    1.  `Total Budget`
    2.  `Amount Spent`
    3.  `Balance` (Remaining Budget)
    4.  `Budget Utilization %`
    5.  `% Remaining Budget`
* **Financial Analysis by Project:** A clustered bar chart detailing `Total Budget`, `Amount Spent`, and `Balance` for each individual project.
* **Financial Analysis by Task:** A clustered bar chart providing a granular view of `Total Budget`, `Amount Spent`, and `Balance` for specific tasks.
* **Budget Trend:** A line chart tracks `Total Budget` vs. `Amount Spent` over time (by month).
* **Cumulative Spending:** An area chart visualizes the `Cumulative Budget` vs. `Cumulative Amount Spent`, clearly showing the spending trajectory throughout the project lifecycle.

## 🛠️ Technical Implementation

### Data Source
* **Excel File:** `ProjectManagementDataset.xlsx` containing all raw project data.

### Data Transformation (Power Query)
* Standard data cleaning procedures were applied.
* Removed columns with 100% null values.
* Corrected the `Progress %` column by creating a new, accurately formatted `Progress %2` column to ensure correct calculations in DAX.

### Data Model
* **`Dataset` Table:** The primary fact table containing all project and task information.
* **`Calendar` Table:** A calculated date table created using `CALENDARAUTO()` to enable robust time-intelligence analysis.
* **Relationship:** A one-to-many relationship is established between `Calendar[Date]` and `Dataset[Start Date]`.

### Key DAX Measures

The report is powered by a robust set of DAX measures, including:

**1. Project Details:**
* `Total Tasks`: A simple `COUNTROWS` of the dataset.
* Status Percentages: `[% Completed]`, `[% In progress]`, `[% Not started]` (calculated using `DIVIDE` and `CALCULATE` to find the ratio against `Total Tasks`).
* Remaining Percentages: `[R % Completed]`, `[R % In progress]`, `[R % Not started]` (calculated as `1.0 - [Status %]`).
* Task Status Counts: `[Total Completed Tasks]`, `[Total InProgress Tasks]`, `[Total Blocked Tasks]`, `[Total NotStarted Tasks]`.

**2. Budget:**
* Core Metrics: `[Total Budget]`, `[Amount Spent]`, `[Balance]`.
* Utilization Metrics: `[Budget Utilization %]`, `[% Remaining Budget]`.
* Cumulative Metrics: `[Cumulative Budget]`, `[Cumulative Amount Spent]` to track running totals over time.
* **Conditional Formatting (CF):** Several measures (`CF Budget`, `CF Remaining Budget`, `CF Balance`) were created using `IF` logic to dynamically color visuals based on performance thresholds (e.g., highlighting red if spending exceeds 50% or if the balance is negative).

## 📂 Repository Structure
-    ├── Icons/ # All icons used in the dashboard UI 
-    ├── Images/ # Screenshots and visuals of the dashboard 
-    ├── ProjectManagementDataset/ │ ├── ProjectManagementDataset.xlsx # The raw data source │ ├── Gantt 2.2.3.0.pbiviz # The custom Gantt chart visual 
-    ├── important columns.txt # DAX code for the 'Expected Days' calculated column 
-    ├── important measures.txt # DAX code for all measures used in the report 
-    ├── important tables.txt # DAX code for the 'Calendar' table 
-    ├── ProjectManagement_Report.pbix # The main Power BI project file └── README.md # This file

## 🚀 How to Use

1.  Clone this repository to your local machine.
2.  Ensure you have **Microsoft Power BI Desktop** installed.
3.  Open the `ProjectManagement_Report.pbix` file.
4.  If prompted, you may need to update the data source path to point to the `ProjectManagementDataset.xlsx` file in the `ProjectManagementDataset` folder.
5.  If the Gantt chart visual does not load, import the custom visual (`.pbiviz`) from the `ProjectManagementDataset` folder.

## 🔧 Technologies Used

* **Microsoft Power BI Desktop**
    * **Power Query** (for M queries)
    * **DAX** (for measures and calculated columns)
* **Microsoft Excel** (as the data source)

## 📞 Contact

I am passionate about leveraging data to build insightful solutions. Let's connect!

* **LinkedIn:** [https://www.linkedin.com/in/engy-saeed2003/](https://www.linkedin.com/in/engy-saeed2003/)
* **Email:** engysead498@gmail.com
