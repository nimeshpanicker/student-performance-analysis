# 🎓 Student Performance Analytics

![Python](https://img.shields.io/badge/Python-EDA-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-blue?logo=pandas)
![Excel](https://img.shields.io/badge/Excel-Data%20Analysis-green?logo=microsoftexcel)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-yellow?logo=powerbi)
![Data Analytics](https://img.shields.io/badge/Data%20Analytics-Project-orange)

A data analytics project analysing academic outcomes for **11,040 students** using Microsoft Excel, Python-based exploratory data analysis, and Power BI semantic modelling.

The project examines Math, Reading, and Writing performance alongside demographic, household, preparation, and engagement factors to identify measurable achievement gaps, actionable preparation levers, and factors that show limited practical effect.

---

# 📌 Project Overview

Educational institutions collect large amounts of student demographic, household, behavioural, and academic data. However, identifying which factors are actually associated with student performance requires structured data analysis.

This project uses an **11,040-student dataset** containing academic scores together with demographic, household, preparation, and engagement variables.

The analysis focuses on:

- Overall academic performance
- Lunch-programme achievement gaps
- Test-preparation completion
- Gender differences by subject
- Ethnic-group performance patterns
- Parental education
- Household composition
- Weekly study hours
- Sport participation
- Relationships between subject scores

The final solution combines **Python EDA, Excel review, Power BI semantic modelling, DAX measures, and dashboard-based data storytelling**.

---

# 🎯 Business Objective

The primary objective is to identify which demographic, household, and preparation factors are most strongly associated with student achievement and distinguish:

- Actionable factors that stakeholders can influence
- Descriptive factors useful for population monitoring
- Factors with relatively small observed effects
- Areas where demographic correlations should not be interpreted as causal relationships

The analysis is designed to support data-driven decisions regarding academic support, test-preparation access, and resource allocation.

---

# ❓ Key Business Questions

1. What is the overall academic performance across Math, Reading, and Writing?
2. Which student subgroup shows the widest achievement gap?
3. Does test-preparation completion correspond with higher academic scores?
4. How does performance differ by gender?
5. How does parental education relate to student achievement?
6. Do household factors such as marital status, birth order, or transport method materially affect scores?
7. Does weekly study time relate to academic performance?
8. Does sport participation relate to student performance?
9. How do academic outcomes differ across ethnic groups?
10. How strongly are Math, Reading, and Writing scores correlated?
11. What additional data would be required for meaningful trend analysis?

---

# 📊 Dataset Overview

**Dataset:** `Expanded_data_with_more_features.csv`

| Attribute | Details |
|---|---|
| Records | 11,040 students |
| Columns | 15 |
| Outcome Fields | MathScore, ReadingScore, WritingScore |
| Demographic Fields | Gender, EthnicGroup |
| Parental Fields | ParentEduc, ParentMaritalStatus |
| Preparation | TestPrep |
| Economic Access Proxy | LunchType |
| Engagement | WklyStudyHours, PracticeSport |
| Household | IsFirstChild, NrSiblings |
| Logistics | TransportMeans |

The dataset contains no date, academic-term, or school-identifier field. Therefore, the project focuses on cross-sectional analysis rather than time-series or school-level trend analysis. :contentReference[oaicite:1]{index=1}

---

# 🧹 Data Preparation & Validation

The data preparation workflow was performed using Python/pandas with supporting Excel review.

### Preparation steps

- Loaded and inspected the CSV dataset
- Reviewed structure using `.head()`, `.info()`, and `.describe()`
- Removed the redundant `Unnamed: 0` index column
- Analysed missing values using `.isnull().sum()`
- Standardised weekly study-hour labels
- Checked score ranges
- Validated sibling-count values
- Reviewed categorical fields for consistency
- Retained missing demographic records rather than removing complete rows unnecessarily

### Missing Values

| Field | Missing Records | Missing % |
|---|---:|---:|
| TransportMeans | 1,140 | 10.3% |
| EthnicGroup | 665 | 6.0% |
| TestPrep | 659 | 6.0% |
| ParentEduc | 658 | 6.0% |
| NrSiblings | 568 | 5.1% |
| ParentMaritalStatus | 435 | 3.9% |
| IsFirstChild | 362 | 3.3% |
| WklyStudyHours | 339 | 3.1% |
| PracticeSport | 224 | 2.0% |
| WritingScore | 1 | <0.1% |

The three primary academic outcome fields are complete or nearly complete, while missingness is concentrated mainly in demographic and household attributes. :contentReference[oaicite:2]{index=2}

---

# 📈 Key Performance Indicators

| KPI | Value |
|---|---:|
| Students | 11,040 |
| Average Math Score | 66.7 |
| Average Reading Score | 69.4 |
| Average Writing Score | 68.4 |
| Test-Preparation Completion | 34.1% |

### Academic Performance

Reading has the highest average score at **69.4**, followed by Writing at **68.4** and Math at **66.7**.

The standard deviation is approximately 15 points across the three subjects, indicating substantial variation in student performance. :contentReference[oaicite:3]{index=3}

---

# 🍽️ Achievement Gap Analysis — Lunch Programme

Lunch-programme enrolment was used as the closest available proxy for household economic access.

| Lunch Type | Students | Math | Reading | Writing |
|---|---:|---:|---:|---:|
| Standard | 7,225 | 70.83 | 72.21 | 71.52 |
| Free / Reduced | 3,815 | 58.84 | 64.19 | 62.63 |
| Gap | — | **11.99** | **8.02** | **8.89** |

The largest observed gap is in Math, where standard-lunch students score approximately **12 points higher** than free/reduced-lunch students.

This represents the widest and most consistent achievement gap examined in the dataset. :contentReference[oaicite:4]{index=4}

---

# 📚 Test-Preparation Impact Analysis

Test preparation represents one of the most directly actionable variables in the dataset.

| Test Prep | Students | Math | Reading | Writing |
|---|---:|---:|---:|---:|
| Completed | 3,538 | 69.45 | 73.65 | 74.62 |
| None | 6,843 | 65.16 | 67.21 | 65.22 |
| Lift | — | **+4.29** | **+6.44** | **+9.40** |

Students who completed test preparation recorded higher average scores across all three subjects.

The largest difference is in Writing, at approximately **+9.4 points**.

Only **34.1%** of students with a recorded test-preparation status completed the course. :contentReference[oaicite:5]{index=5}

---

# 👥 Gender & Demographic Analysis

## Gender

| Gender | Students | Math | Reading | Writing |
|---|---:|---:|---:|---:|
| Female | 5,591 | 64.13 | 72.80 | 72.73 |
| Male | 5,449 | 69.32 | 66.00 | 64.05 |

The pattern is subject-specific:

- Male students average **5.2 points higher in Math**
- Female students average **6.8 points higher in Reading**
- Female students average **8.7 points higher in Writing**

Therefore, the data does not show one gender consistently leading across all subjects. :contentReference[oaicite:6]{index=6}

---

# 🧑‍🎓 Ethnic Group Analysis

| Group | Students | Share | Math | Reading | Writing |
|---|---:|---:|---:|---:|---:|
| Group C | 3,277 | 31.6% | 64.37 | 68.16 | 66.77 |
| Group D | 2,659 | 25.6% | 67.95 | 70.50 | 71.01 |
| Group B | 2,111 | 20.3% | 63.52 | 67.42 | 65.90 |
| Group E | 1,489 | 14.3% | 75.76 | 74.67 | 73.09 |
| Group A | 839 | 8.1% | 63.61 | 67.18 | 65.45 |

Group E records the highest average scores across all three subjects.

However, the dataset does not establish why these differences exist. The report therefore treats ethnic group as a **monitoring signal rather than a standalone targeting variable**. :contentReference[oaicite:7]{index=7}

---

# 🎓 Parental Education Analysis

| Parent Education | Students | Math | Reading | Writing |
|---|---:|---:|---:|---:|
| Some high school | 2,007 | 62.81 | 65.81 | 63.93 |
| High school | 2,010 | 64.26 | 67.04 | 65.08 |
| Some college | 2,375 | 66.51 | 68.91 | 68.19 |
| Associate's degree | 1,994 | 68.66 | 71.44 | 70.55 |
| Bachelor's degree | 1,243 | 70.55 | 73.16 | 73.45 |
| Master's degree | 753 | 72.49 | 76.17 | 76.86 |

A near-monotonic relationship appears between parental education and student scores.

The difference between the lowest and highest education groups is approximately **11 points**, making parental education one of the clearest patterns in the dataset. :contentReference[oaicite:8]{index=8}

---

# 📖 Study Habits & Engagement

## Weekly Study Hours

| Study Band | Students | Average Score |
|---|---:|---:|
| < 5 hrs/week | 2,981 | 66.42 |
| 5–10 hrs/week | 5,797 | 68.49 |
| > 10 hrs/week | 1,923 | 69.78 |

Students studying more hours show higher average scores, although the overall difference is modest compared with lunch type, test preparation, and parental education.

The difference between the lowest and highest study-hour groups is approximately **3.4 points**. :contentReference[oaicite:9]{index=9}

## Sport Participation

| Practice Frequency | Students | Average Score |
|---|---:|---:|
| Never | 1,435 | 66.02 |
| Sometimes | 5,478 | 68.04 |
| Regularly | 3,903 | 69.16 |

The observed difference between students who never practise sport and those who practise regularly is approximately **3.1 points**.

The report frames sport participation primarily as a wellbeing indicator rather than a direct academic-performance lever. :contentReference[oaicite:10]{index=10}

---

# 🏠 Household Factors

Several household and logistical variables were evaluated.

### Parental Marital Status

Scores range approximately from **66.1 to 69.4** across categories.

### First-Child Status

First children show only approximately **0.7–0.9 point** differences compared with non-first children.

### Transport Method

Students using school buses and private transport differ by less than **0.4 points** across subjects.

These variables therefore show relatively small observed differences compared with the major factors identified in the analysis. :contentReference[oaicite:11]{index=11}

---

# 🔗 Subject Score Correlation Analysis

Pearson correlation was used to evaluate relationships between the three academic subjects.

| | Math | Reading | Writing |
|---|---:|---:|---:|
| Math | 1.00 | 0.82 | 0.81 |
| Reading | 0.82 | 1.00 | 0.95 |
| Writing | 0.81 | 0.95 | 1.00 |

### Key Finding

Reading and Writing have a very strong correlation of **0.95**.

Math has a lower correlation with Reading and Writing at approximately **0.81–0.82**.

This suggests that literacy-focused analysis can consider Reading and Writing together, while Math can be treated as a comparatively distinct skill domain. :contentReference[oaicite:12]{index=12}

---

# 💡 Key Business Insights

### 1. Lunch-programme gap

Free/reduced-lunch students trail standard-lunch students by up to **12 points**, representing the largest observed achievement gap.

### 2. Test preparation

Only **34.1%** of students with a recorded status completed test preparation, while completers show a **4–9 point** difference across subjects.

### 3. Parental education

Parental education shows an approximately **11-point gradient** across education categories.

### 4. Subject-specific gender differences

Gender differences move in opposite directions depending on the subject.

### 5. Literacy relationship

Reading and Writing demonstrate a **0.95 Pearson correlation**.

### 6. Study hours

Study time shows a positive but comparatively modest relationship with academic performance.

### 7. Household composition

Marital status, first-child status, and transport method show relatively small score differences.

### 8. Demographic interpretation

Ethnic-group differences should be treated cautiously because the dataset does not establish causal explanations.

---

# 📌 Business Recommendations

Based on the report's analysis:

1. Expand access to test-preparation programmes and track completion as a KPI.
2. Prioritise supplemental academic support for free/reduced-lunch students.
3. Use parental education as a segmentation variable when planning support outreach.
4. Consider combined Reading/Writing literacy support.
5. Treat Math support as a separate intervention area.
6. Use subject-specific rather than blanket gender analysis.
7. Monitor demographic patterns without treating them as standalone causal targeting variables.
8. Encourage healthy baseline study habits and sport participation without over-claiming academic effects.
9. Add an assessment date or academic-term field to future datasets to enable longitudinal analysis. :contentReference[oaicite:13]{index=13}

---

# 📊 Dashboard Details

The project includes a dashboard built around the Power BI semantic model.

### Dashboard Components

- KPI summary
- Lunch-programme achievement gap
- Test-preparation impact
- Gender performance
- Parental education gradient
- Ethnic-group analysis
- Weekly study-hour analysis
- Sport participation analysis
- Subject-score correlation matrix
- Parental marital-status comparison

The dashboard is designed to help stakeholders move from headline KPIs to subgroup comparisons and identify which factors should or should not influence resource-allocation decisions. :contentReference[oaicite:14]{index=14}

---

# 🖥️ Dashboard Preview

The project dashboard is available in:

```text
dashboard/Student_Performance_Dashboard.html
