Emergency Room Analytics Dashboard

A self-contained Power BI project for Emergency Room (ER) analytics, including a single dataset and a single PBIX report file.

📂 Repository Structure

/                          # Project root
├── Hospital_ER_Data.csv   # ER patient dataset (source of truth)
├── Hospital.pbix           # Power BI report containing all dashboard pages
└── README.md               # This documentation file

🚀 Overview

This project delivers a unified, interactive dashboard for Emergency Room analytics at a hospital. It empowers stakeholders—such as department heads, operations managers, and quality teams—to:

Monitor Real-Time ER Performance: Track daily and hourly patient arrivals, wait times, and admission rates to identify peak periods and resource needs.

Analyze Patient Demographics: Visualize age, gender, and race distributions to support targeted community outreach and equity analyses.

Understand Referral Patterns: See which departments refer the most patients to the ER, helping optimize interdepartmental workflows.

Measure Patient Experience: Monitor average wait times and satisfaction scores to drive quality improvement initiatives.

Drill Down to Individual Cases: Filter and inspect single patient visits, supporting root-cause analysis for delays or readmissions.

All analytics are powered by a single source dataset (Hospital_ER_Data.csv) and a single PBIX file (Hospital.pbix). This lightweight repository makes it easy to share, version, and maintain your ER reporting solution.

🛠 Prerequisites & Setup

Power BI Desktop (April 2024 release or later)

Download: https://powerbi.microsoft.com/desktop/

Git (optional, to clone this repo)

To get started:

Clone or download this repository.

Open Hospital.pbix in Power BI Desktop.

In Power BI’s Transform Data window, ensure the data source points to Hospital_ER_Data.csv in the same folder.

Click Refresh to load the dataset.

Explore the slicers and drill into any visual.

📊 Power BI Report (Hospital.pbix)

The single Hospital.pbix file contains three interactive report pages, each focused on a critical aspect of ER analytics:

1. ER Operations Overview

KPIs: Total Patients, Average Wait Time, Average Satisfaction Score, Referred Patients.

Admission Status: Chart showing admitted vs. discharged/transferred counts.

Visit Heatmap: Matrix of Hour of Day × Weekday colored by visit volume to highlight peaks.

Daily Arrivals Trend: Line chart of daily patient counts for trend analysis.

Slicers: Date range, Year, Month filters.

2. Demographics & Department Insights

Age × Gender Bar Chart: Stacked bars showing patient counts by age group and gender.

Race Distribution Donut: Visual breakdown of patient race/ethnicity percentages.

Department Referral Tree Map: Sizes departments by referral count, spotlighting top referrers.

Cross-Filtering & Slicers: Gender, Age Group, Race, Department Referral, Date range.

3. Patient Information

Detailed Table: Lists Patient Id, AdmissionDate, Age, Gender, Race, Department Referral, Wait Time, Satisfaction Score, Admission Status.

Filters: Date range, demographics, and referrals to isolate cohorts.

Drillthrough/Export: Supports right-click drillthrough (if configured) and data export to CSV.

Tip: Navigate between pages using the bottom tabs inside Power BI Desktop.

🔗 Data Model & Important Fields

Fact Table: Hospital_ER_Data.csv

Key columns: Patient Admission Date, Patient Age, Patient Gender, Patient Race, Department Referral, Patient Waittime, Patient Satisfaction Score.

Date Table: A dedicated date dimension table that we create manually in Power BI according to our reporting requirements. It includes fields for Year, Month, Month Number, Month & Year, Weekday, and Weekday Number to support slicers and time-intelligence measures.

Measures:

Total Patients = COUNTROWS('Hospital_ER_Data')

Average Wait Time = AVERAGE('Hospital_ER_Data'[Patient Waittime])

Avg. Satisfaction = AVERAGE('Hospital_ER_Data'[Patient Satisfaction Score])

Referred Patients = CALCULATE(COUNTROWS(), 'Hospital_ER_Data'[Department Referral] <> "None")

Tip: After creating the Date table, mark it as the official date table (Modeling → Mark as date table) to enable all time-intelligence features in Power BI.

🤝 Contributing

This is a single-file project. If you find issues or want to suggest improvements:

Fork the repo and open an issue or pull request.

Describe any changes to visuals, metrics, or underlying data fields.

📜 License

This project is licensed under the MIT License. See LICENSE for details.

“Turn data into insights—then insights into actions.” 🚑

