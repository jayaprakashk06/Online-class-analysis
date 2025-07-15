# Online-class-analysis
A Power BI dashboard that analyzes online learning platform data to uncover insights on learner engagement, completion rates, subscription trends, and regional activity using over 20,000 records. Includes full documentation, data cleaning process, DAX measures, and interactive visuals for strategic decision-making.
# 📘 Documentation – Online Learning Analytics Dashboard

## 📁 Project Title:
**Online Learning Analytics – Power BI Dashboard**

## 👨‍💻 Author:
**Jayaprakash K**  
Artificial Intelligence & Data Science  
Kangeyam institutions

---

## 📝 Project Overview

This project focuses on analyzing user behavior and performance on an online learning platform. A simulated dataset containing over 20,000 learner records was cleaned, processed, and visualized using Microsoft Power BI. The dashboard provides insights into user engagement patterns, course completion performance, device usage, geographic distribution, and subscription types.

The key objective was to transform raw, unstructured learner data into a visual, interactive tool that aids data-driven decisions for improving content delivery, platform design, and strategic planning in the EdTech domain.

---

## 📊 Dataset Summary

The dataset simulates real-time online learning data and contains over **20,000+ rows** with **10+ attributes** such as:

- `User ID`
- `City`
- `Age Group`
- `Course Name`
- `Subscription Type` (Free / Paid)
- `Device Used`
- `Assessment Score`
- `Daily Watch Time`
- `Completion Status`
- `Enrollment Date`

Each row represents a unique learner’s daily learning log.

---

## 🧹 Data Preparation & Cleaning Process

Before building the dashboard, extensive cleaning was performed in **Power Query Editor**:

### ✅ Key Data Cleaning Steps:

1. **Missing Values Handling**:
   - Filled missing values in `Subscription Type` as "Free"
   - Filled blank `Daily Watch Time` with column average
   - For empty `Assessment Score`, filled with `0` (indicating not attempted)

2. **Date Formatting**:
   - Standardized `Enrollment Date` to proper `DateTime`
   - Extracted `Month`, `Year`, and `Month Name` for trend analysis

3. **Categorical Normalization**:
   - Cleaned inconsistent course names and device labels
   - Unified `City` names with proper case (e.g., `CHENNAI` → `Chennai`)

4. **Column Derivations**:
   - Created `Completion Rate %` using DAX:  
     `Completed Users / Total Users * 100`
   - Calculated average `Watch Time` using aggregation measures

---

## 📐 Dashboard Design Overview

The report contains multiple pages including:

- ✅ **Summary Overview**
- ✅ **Device & Subscription Analysis**
- ✅ **Completion Rate View**
- ✅ **Drillthrough Page (City Details)**

### 🔑 Visual Elements Used:
- KPI Cards
- Bar & Column Charts
- Donut Charts
- Line Chart (for trend)
- Gauge Visual
- Drillthrough Navigation
- Slicers for interaction

---

## 📌 Key Metrics Explained

| Metric                  | Purpose                                      |
|-------------------------|----------------------------------------------|
| Total Unique Learners   | Measures platform reach                      |
| Avg. Daily Watch Time   | Indicates user engagement                    |
| Course Completion Rate  | Reflects learning effectiveness              |
| Active Cities           | Shows geographic spread                      |
| Device Usage Share      | Supports content delivery optimization       |
| Subscription Type Share | Reveals user monetization opportunity        |

---

## 🧠 Key Insights Derived

1. **High Learner Activity in Tier 1 Cities**:  
   Cities like **Chennai**, **Bangalore**, and **Mumbai** show the highest number of active users.

2. **Dominance of Mobile Devices**:  
   Over 65% of users access the platform via mobile, indicating mobile-first optimization is necessary.

3. **Consistent Course Completion Rates**:  
   An average completion rate of **over 60%**, suggesting effective learner engagement.

4. **Subscription Imbalance**:  
   Nearly 70% of users are on free plans — revealing a strong need for user conversion strategies.

5. **Monthly Trends Show Academic Peaks**:  
   Spikes in engagement are seen during **March, April, and July**, likely linked to semester cycles or exam prep periods.

---

## 📈 DAX Measures Used

Here are a few important calculated fields used to enable deeper analytics:

```DAX
Completion Rate (%) = 
DIVIDE(
    CALCULATE(COUNTROWS('Online_Learning_Analytics_India'), 'Online_Learning_Analytics_India'[Completion Status] = "Completed"),
    COUNTROWS('Online_Learning_Analytics_India')
)

Average Watch Time = 
AVERAGE('Online_Learning_Analytics_India'[Daily Watch Time])

Month Name = 
FORMAT('Online_Learning_Analytics_India'[Enrollment Date], "MMMM")

EndOfMonth = 
EOMONTH('Online_Learning_Analytics_India'[Enrollment Date], 0)
