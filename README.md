# Panic-Attack-Data-Analysis-Power-BI-Project

## **📊 Project Overview**

This project provides an in-depth analysis of panic attack patterns using Power BI, with data sourced directly from Snowflake. The report explores relationships between demographic factors, medical history, lifestyle habits, and panic attack characteristics.

The analysis aims to uncover insights that can assist healthcare professionals and researchers in understanding triggers, frequency, and severity of panic attacks across different population segments.

## **🧾 Data Source**

* Database: Snowflake

* Dataset Name: panic_attack_dataset.csv

* Data Type: Clinical and lifestyle records of individuals who experienced panic attacks

* Size: ~1,200 records

* Key Columns:

  1. AGE_GROUP (Adolescent, Adult, Senior)

  2. GENDER (Male, Female, Non-binary)

  3. TRIGGER_REASON (Caffeine, Phobia, PTSD, Social Anxiety)

  4. PANIC_SCORE (Low, Medium, High)

  5. SLEEP_HOURS

  6. DRINKS_PER_WEEK

  7. PANIC_ATTACK_DURATION (in minutes)

  8.PANIC_ATTACK_FREQUENCY

## **🧩 Project Objectives**

  1. Identify common symptoms among panic attack patients.

  2. Analyze the impact of lifestyle factors (sleep, caffeine, alcohol) on panic severity.

  3. Explore trigger correlations with panic attack duration and frequency.

  4. Visualize demographic differences in panic attack patterns.

  5. Provide actionable insights through interactive Power BI dashboards.

## **📈 Key Visualizations**

**Based on the PDF report, the Power BI dashboard includes:**

  1. Symptoms Overview:

  * Number of patients exhibiting Dizziness, Trembling, Sweating, Chest Pain, and Shortness of Breath.

  2. Lifestyle Insights:

  * Relationship between Number of Drinks per Week and Panic Scores.

  * Correlation between Sleep Hours and Panic Attack Frequency.

  3. Demographic Analysis:

  * Average Sleep Hours, Panic Score, and Frequency segmented by Age Group and Trigger Reason.

  4. Panic Attack Duration:

  * Distribution of panic attack duration (10, 20, 30, 40 minutes).

  5. Filter Options:

  * Gender, Trigger Reason, Medical History, and Panic Score (High/Medium/Low).

## **⚙️ Power BI Design and ETL Process**

Following good Power BI practices outlined in the “Good Practices to Get Started” document:

  * ETL Process: Data was extracted from Snowflake, transformed in Power Query, and loaded into Power BI for modeling.

  * Calendar Table: Created using DAX to support time intelligence and improve report interactivity.

  * Data Model: Star schema with clean relationships between patient demographic, lifestyle, and symptom tables.

  * Measures & KPIs: Implemented using DAX to calculate averages, counts, and frequency rates.

## **🧠 Insights & Findings**

  * Sweating and Shortness of Breath were the most common symptoms (seen in ~70% of patients).

  * Adults with Caffeine or Phobia as triggers had higher panic scores on average.

  * Sleep deprivation (less than 6 hours) was strongly associated with higher panic frequency.

  * Patients with anxiety or depression history reported longer panic attack durations.

## **🧩 Files Included**
| File                                               | Description                          |
| -------------------------------------------------- | ------------------------------------ |
| `panic_attack_dataset.csv`                         | Cleaned dataset used for analysis    |
| `Panic Attack Data Analysis Power BI Project.pbix` | Power BI report file                 |
| `Panic Attack Data Analysis Power BI Project.pdf`  | Exported report (visual summary)     |
| `Good practices to get started.docx`               | Power BI modeling and ETL guidelines |

## **🧠 Tools & Technologies**

1. Power BI Desktop

2. Snowflake (Data Source)

3. DAX (Data Analysis Expressions)

4. Power Query

5. Microsoft Excel / CSV

6. ETL Best Practices

## **🚀 How to Use**

1. Open the .pbix file in Power BI Desktop.

2. Ensure you have Snowflake credentials configured if using live connection mode.

3. Explore interactive filters and slicers to analyze by gender, trigger reason, and medical history.

4. Export dashboards or visuals as PDF for reporting or presentations.

## **📚 Future Enhancements**

1. Integrate real-time Snowflake streaming data using DirectQuery.

2. Apply predictive modeling (R/Python integration) for panic risk prediction.

3. Implement automated alerts for abnormal panic frequency trends.

## **🧑‍💻 Author**

1. **Project Title:** Panic Attack Data Analysis
2. **Developer:** Vishal Londhekar
3. **Tools:** Power BI, Snowflake, DAX, Power Query
4. **Date:** October 2025
