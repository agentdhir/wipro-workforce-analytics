# Workforce Attendance Analytics & Office Footfall Forecasting

Analytics work from my Data Analyst internship (Workforce Analytics, summer training) at **Wipro Technologies**, Gurugram, June–July 2026.

The project turns 7M+ raw employee attendance records into a clean, traceable dataset. It then answers three business questions:

1. **How reliable is the attendance data?** Duplicates, missing values, and what each status actually means.
2. **Who is working on non-working days, and is it real work?** Separating genuine full-day work on week-offs and holidays from short check-ins.
3. **How many people will be on each campus on a given day?** An explainable footfall forecast for facilities planning.

> **Data notice:** the raw attendance data is Wipro-internal and is **not** in this repository. Every notebook output has been cleared, and no employee identifiers are included. The notebooks show the method and the code. Results below are aggregates only.

## Notebooks

| # | Notebook | What it does |
|---|---|---|
| 01 | [Data understanding](notebooks/01_data_understanding.ipynb) | Combines multiple raw CSV extracts into one staging table. Profiles columns and record counts. |
| 02 | [Data quality & duplicates](notebooks/02_data_quality_duplicate_investigation.ipynb) | Finds exact and near-duplicate rows that were hiding true presence patterns. Checks data types, missing values and the business meaning of each attendance status. |
| 03 | [Non-working-day PRESENT analysis](notebooks/03_non_working_day_analysis.ipynb) | Investigates employees marked PRESENT on week-offs and holidays. Uses swipe hours (TIC/TOF/TOTAL) to tell full-day work from short visits. Builds a Frequency × Intensity risk segmentation. |
| 04 | [Workday pattern analysis](notebooks/04_workday_pattern_analysis.ipynb) | Sets the normal-workday baseline across contexts: office, home, client site, leave, training and travel. Groups locations into campus-intensity tiers. |
| 05 | [Office footfall forecasting](notebooks/05_Office_Footfall_Forecasting.ipynb) | Builds a forecasting-ready daily campus dataset that counts unique employees, so nobody is double-counted. Compares explainable baselines with a time-based train/test split. |

## Key results (aggregate)

- **One traceable pipeline.** 7.2M+ attendance records from multiple raw CSV sources were consolidated in Python (Pandas), with duplicates removed and documented.
- **Risk framework.** A Frequency–Intensity segmentation narrowed 7M+ records down to **889 employees** with repeated, high-intensity presence on non-working days. These were flagged for HR review and cross-checked against each person's normal workday behaviour.
- **Workday baseline.** 5M+ workday records were grouped into behaviour categories (Office, Remote, Client Site, Leave) and campus-intensity tiers. This showed clear differences between sites.
- **Footfall forecasting.** Three explainable baselines were compared:
  - weekday average
  - same day of the previous week
  - weighted historical blend

  Each of the **9 major locations** got its own best ("champion") baseline.

## Approach

- **Explainability over complexity.** The audience was HR and facilities teams, so every flag and forecast had to be easy to explain.
- **Validate before concluding.** Every segment was cross-checked against normal-workday behaviour before being treated as a finding.
- **Honest scope.** Data limitations are written down in the notebooks instead of being glossed over.

## Tech

Python · Pandas · NumPy · Matplotlib · Seaborn · Jupyter

## Author

**Raghav Dhir**, B.Tech CSE, Jaypee University of Information Technology. [LinkedIn](https://www.linkedin.com/in/raghavdhirr)
