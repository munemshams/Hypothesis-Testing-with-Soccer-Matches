# Hypothesis Testing: Goal Scoring in Men's vs Women's FIFA World Cup Matches

This project investigates whether women’s FIFA World Cup matches tend to produce more goals than men’s matches using official match results after January 1, 2002.

The analysis was conducted in **R**, combining exploratory data analysis and a formal statistical hypothesis test. The goal is to determine whether the apparent scoring difference between men's and women's international soccer matches is statistically significant.

All analysis outputs, including the knitted report and visualizations, are included in this repository.

---

# Project Overview

International soccer fans have often observed that women's matches appear to produce higher goal totals than men's matches. This project evaluates that observation using statistical methods.

The analysis compares goal totals from:

• Men's FIFA World Cup matches  
• Women's FIFA World Cup matches  

By examining match results after **2002**, the project focuses on the modern era of international soccer.

The project includes:

• Data cleaning and filtering  
• Exploratory visualization of goal distributions  
• A non-parametric statistical hypothesis test  
• Interpretation of statistical results  

---

# Research Question

**Are more goals scored in women’s FIFA World Cup matches than in men’s FIFA World Cup matches?**

This question is evaluated using a **one-sided hypothesis test**.

---

# Dataset

Two datasets are used in this project.

| Dataset | Description |
|-------|-------------|
| women_results.csv | Historical results for women's international soccer matches |
| men_results.csv | Historical results for men's international soccer matches |

For the analysis, only matches meeting the following criteria are included:

• Tournament equals **FIFA World Cup**  
• Match date occurs after **January 1, 2002**

This filtering ensures a fair comparison between modern World Cup matches.

---

# Project Workflow

The analysis follows a structured **statistical analysis workflow**.

## 1. Data Loading

The datasets are loaded into R using the **tidyverse** ecosystem.

The raw datasets contain match information such as:

• Match date  
• Home team  
• Away team  
• Home score  
• Away score  
• Tournament type  

---

## 2. Data Cleaning and Filtering

The datasets are filtered to retain only:

• FIFA World Cup matches  
• Matches played after **January 1, 2002**

A new variable is created:

goals_scored = home_score + away_score

This variable represents the **total number of goals scored in each match**.

---

## 3. Exploratory Data Analysis (EDA)

Histograms are generated for both men's and women's match datasets to examine the distribution of goals scored.

The visualizations are created using **ggplot2** and displayed side-by-side to compare scoring patterns.

These plots allow a visual assessment of whether the goal distributions follow a normal pattern.

The visualization generated during the analysis is named:

histogram.png

---

## 4. Distribution Assessment

The exploratory analysis revealed that both datasets exhibit **skewed distributions** and do not follow a normal distribution.

Because the assumptions required for a traditional **t-test** are violated, a non-parametric test is used instead.

---

## 5. Hypothesis Testing

The analysis uses the **Wilcoxon Rank-Sum Test (Mann–Whitney U Test)**.

This test is appropriate because it:

• Does not assume normally distributed data  
• Works with independent samples  
• Supports one-sided hypothesis testing  
---

# Hypotheses

The test uses a **10% significance level (α = 0.10)**.

### Null Hypothesis (H₀)

The mean number of goals scored in women's World Cup matches is **equal to** the mean number of goals scored in men's matches.

### Alternative Hypothesis (Hₐ)

The mean number of goals scored in women's World Cup matches is **greater than** the mean number of goals scored in men's matches.

This is a **one-sided test**.

---

# Decision Rule

If **p-value < 0.10** → Reject the null hypothesis  
If **p-value ≥ 0.10** → Fail to reject the null hypothesis

---

# Results

The Wilcoxon rank-sum test produced the following result.

| p_value | decision |
|--------|---------|
| 0.0051 | reject |

Because the p-value is **below the significance level of 0.10**, the null hypothesis is rejected.

This suggests that **women’s FIFA World Cup matches tend to produce more goals than men’s matches** in the analyzed dataset.

# Visualization

The analysis includes histogram visualizations comparing the goal distributions for men's and women's matches.

These plots demonstrate the skewed nature of the datasets and support the use of a **non-parametric statistical test**.

---

# Files Included

| File | Description |
|-----|-------------|
| README.md | Project documentation |
| hypothesis_testing_soccer.Rmd | Full R Markdown analysis |
| hypothesis_testing_soccer.docx | Knitted Word report containing the full analysis |
| hypothesis_testing_soccer.html | Knitted HTML version of the report |
| men_results.csv | Dataset containing men's international match results |
| women_results.csv | Dataset containing women's international match results |
| histogram.png | Visualization comparing goal distributions |

---

# R Libraries Used

| Library | Purpose |
|-------|--------|
| tidyverse | Data manipulation and cleaning |
| dplyr | Filtering and transforming match data |
| ggplot2 | Creating histogram visualizations |
| readr | Reading CSV datasets |
| lubridate | Handling date filtering |
| gridExtra | Displaying multiple plots side-by-side |

---

