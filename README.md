# Financial Strain and Emergency Department Use
### ASA DataFest 2026 | University of Missouri

**Team:** The Standard Deviants — Adrian Cantrell, Colin Arbuckle, and Derek Dembinsky  
**Tools:** R, RStudio, `dplyr`, `tidyr`, `ggplot2`, logistic regression  
**Focus:** Healthcare analytics · Social determinants of health · Statistical modeling

## Project overview

For ASA DataFest 2026, our team was given a healthcare dataset and tasked with finding a meaningful question to investigate within a single weekend. After exploring potential directions, we focused on whether **financial and material hardship was associated with emergency department (ED) use**.

We analyzed **32,079 patients** from the Storrs Valley Hospital dataset, using social determinants of health (SDOH) screening questions to investigate patterns in ED utilization. Our project combined open-ended problem formulation, data preparation, exploratory analysis, logistic regression, visualization, and communication of findings.

**Research question:** Are patients who report financial or material hardship more likely to have at least one emergency department visit?

## Approach

### 1. Define the question
We explored the provided data, brainstormed possible research directions, and selected five dimensions of financial and material hardship from the SDOH questionnaire:

- Utility shutoff threats
- Rent or mortgage instability
- Food insecurity
- Homelessness
- Transportation barriers

### 2. Prepare the predictors
We examined correlations between related questionnaire items. Two pairs were strongly correlated: **food insecurity questions (r = 0.86)** and **transportation questions (r = 0.84)**. We combined each pair into a single binary indicator, resulting in five hardship predictors.

### 3. Model emergency department use
Using **RStudio**, we fit a **binary logistic regression** with the five hardship indicators as predictors and **any recorded ED visit (yes/no)** as the outcome.

We also created a **hardship burden score from 0 to 5** by summing the five binary indicators, then calculated ED-visit proportions at each score level.

## Key findings

- All five hardship indicators had **positive estimated logistic-regression coefficients** in our fitted model.
- **Transportation barriers** had the largest estimated coefficient (**0.390**), followed by utility shutoff threats (**0.282**), rent instability (**0.133**), homelessness (**0.119**), and food insecurity (**0.060**).
- The share of patients with at least one ED visit increased across the hardship burden score:

| Hardship score | Patients with an ED visit |
| --- | ---: |
| 0 | ~41% |
| 1 | ~55% |
| 3 | ~65% |
| 5 | ~77% |

**Takeaway:** Patients reporting more forms of financial or material hardship were more likely to have an ED visit in this dataset. Transportation access emerged as a potentially important area for further investigation and intervention.

> **Interpretation note:** These are observational associations, not evidence that hardship caused an ED visit. The outcome was whether a patient had **any** ED visit, not the number of repeat visits. Coefficients describe the fitted model and are not, by themselves, evidence of statistical significance or causality.

## Repository contents

The repository contains R analysis files from the team's exploratory work and final modeling:

- [`final.code_ac`](final.code_ac) — ED-visit flags, hardship-score summaries and visualization, and the five-predictor logistic regression.
- [`Log_ression.ervisits`](Log_ression.ervisits) — additional logistic-regression analysis.
- [`er_model`](er_model), [`overall code`](overall%20code), [`scores`](scores), and [`visittypes`](visittypes) — supporting analyses and exploratory work.

These are project working files rather than a packaged, one-command reproducible pipeline. The original DataFest patient data are not included in this repository; reproducing the analysis requires access to the event dataset and the relevant objects used by the scripts.

## Why this matters

SDOH screening data can help healthcare organizations identify patterns that clinical variables alone may miss. Our findings suggest that **transportation, housing, utility costs, and food access** are useful considerations when examining ED utilization. Further study would be needed before using these associations to target interventions.

## Team and acknowledgments

**The Standard Deviants**  
Adrian Cantrell · Colin Arbuckle · Derek Dembinsky

Completed for **ASA DataFest 2026 at the University of Missouri**. This was a collaborative team project; the analysis and findings are credited to the team rather than to any one individual.
