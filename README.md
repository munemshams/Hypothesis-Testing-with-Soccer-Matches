**Hypothesis Testing: Do Women’s World Cup Matches Have More Goals?**
Statistical Comparison of Goal Scoring in FIFA World Cup Matches (Post-2002)

This project investigates whether more goals are scored in women’s FIFA World Cup matches compared to men’s, using official match results after 2002-01-01. The analysis was conducted in R, using exploratory visualizations and a formal hypothesis test.

The knitted report (Word document) and all generated outputs are included in this repository.

**Research Question**

Are more goals scored in women’s international soccer matches than in men’s?

This question is motivated by long-standing observations that women’s international matches often appear higher-scoring.
To evaluate this scientifically, we use two independently collected datasets of match results.

**Files Included**
- README.md

- hypothesis_testing_soccer.Rmd        - The full R Markdown analysis

- hypothesis_testing_soccer.docx       - Knitted Word file

- men_results.csv                      - Raw Dataset  

- women_results.csv                    - Raw Dataset

- histogram_output.png                 - Visualization generated from R

**Hypotheses**

We assume a 10% significance level (α = 0.10).

Null Hypothesis (H₀)

The mean number of goals scored in women’s World Cup matches is the same as men’s.

Alternative Hypothesis (Hₐ)

The mean number of goals scored in women’s World Cup matches is greater than men’s.

This is a one-sided test.

**Dataset Description**

This project uses two CSV files:

women_results.csv	All recorded women’s international match results

men_results.csv	All recorded men’s international match results

Only FIFA World Cup matches after 2002-01-01 are included in the analysis. Friendlies and qualifiers are excluded.

**Methods**

1️. Data Cleaning & Filtering

For both men and women:

Keep matches where tournament == "FIFA World Cup"

Keep only dates after 2002-01-01

Compute a goals_scored variable as:

goals_scored = home_score + away_score

2️. Exploratory Data Analysis (EDA)

To assess distribution shape, histograms were generated for both men’s and women’s matches:

- Using ggplot2
- Displayed side-by-side
- Used to evaluate normality

Result:
Both distributions showed skewness and non-normal behavior, making traditional t-tests inappropriate.

3️. Hypothesis Test

Since normality was violated for both groups, we use the:

Wilcoxon–Mann–Whitney U Test (Rank-Sum Test)

Properties:

Non-parametric

Does not assume normality

Suitable for independent samples

Supports one-sided testing

Test performed as:

wilcox.test(women_wc$goals_scored,
            men_wc$goals_scored,
            alternative = "greater")
            
4️. Decision Rule

If:

p-value < 0.10 → Reject H₀
p-value ≥ 0.10 → Fail to reject H₀

**Visualizations**

Histogram Comparison of Goals Scored

This graphic helps justify the use of a non-parametric test by showing visible skewness in both datasets.

**Results**

The final output was stored in:

result_df

Containing:

Variable	Meaning
p_val	p-value from the Wilcoxon test
result	“reject” or “fail to reject”

Example structure:

      p_val        result
1   0.0XXX   "reject" / "fail to reject"

➡ The interpretation of this result is included in the knitted report.




