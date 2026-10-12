# Graduate Admission Analysis | Statistical Modeling in R

A mathematical statistics research project investigating the relationship between applicants' academic profiles and the **Chance of Admit** variable in the *Graduate Admission 2* dataset. The analysis combines exploratory data analysis, multiple linear regression, diagnostic testing, interaction effects, backward model selection, and cross-validation.

**Authors:** Katia Russo and Matteo Zabban  
**Academic year:** 2024–2025  
**Language:** R

## Project overview

Using **500 applicant records**, the study examines GRE and TOEFL scores, university rating, statement of purpose (SOP), letters of recommendation (LOR), CGPA, and research experience. The outcome is the dataset's continuous *Chance of Admit* score; it should not be interpreted as a verified real-world admission probability for an individual applicant.

The workflow covers:

1. **Data preparation and exploration:** remove the serial-number identifier, inspect missing values and variable types, and visualize distributions, outliers, and predictor–outcome relationships.
2. **Multiple linear regression:** fit a baseline model and inspect residual plots, a Q–Q plot, the Shapiro–Wilk test, and predictor correlations.
3. **Interaction analysis:** investigate whether the association between university rating and the outcome differs by research experience; compare nested models using ANOVA.
4. **Model selection:** apply backward stepwise selection and compare model fit using adjusted R², AIC, and BIC.
5. **Validation:** evaluate the selected regression specification using **10-fold cross-validation**.

## Results reported in the project

| Metric / finding | Reported result |
| --- | --- |
| Baseline regression adjusted R² | **0.8194** |
| Model with research × university-rating interaction: adjusted R² | **0.8209** |
| Interaction comparison (ANOVA) | **F = 5.1605; p = 0.02354** |
| Backward-selected model adjusted R² | **0.8212** |
| 10-fold cross-validation mean R² | **≈ 0.820** |
| 10-fold cross-validation RMSE | **≈ 0.060** |

These figures are taken from the accompanying report; they are not newly reproduced here. The report also discusses limitations, including correlated predictors and deviations from residual normality. The dataset is observational and the findings should **not** be interpreted as causal effects or admission guarantees.

## Repository contents

```text
masters-admission-analysis/
├── README.md
├── src/
│   └── University_Admission.R
├── report/
│   └── Russo_Zabban.pdf
├── data/
│   └── README.md
└── .gitignore
```

- [`src/University_Admission.R`](src/University_Admission.R): original analysis script.
- [`report/Russo_Zabban.pdf`](report/Russo_Zabban.pdf): full academic report, figures, diagnostics, and bibliography.
- [`data/README.md`](data/README.md): dataset setup instructions.

## How to run

1. Install [R](https://www.r-project.org/) and optionally [RStudio](https://posit.co/products/open-source/rstudio/).
2. Obtain the **Graduate Admission 2** dataset (the 500-row version) and place the CSV at the project root with the filename `Admission_Predict_Ver1.1.csv`.
3. Open `src/University_Admission.R` in RStudio and run the script.

The original script installs and loads the `tidyverse` and `caret` packages. Installation requires an internet connection. It also uses `View(data)`, which is most convenient in an interactive R/RStudio session. **The CSV is not included** in this repository; follow the dataset provider's terms when downloading or redistributing it.

## Limitations

- The dataset is a teaching/research dataset inspired by graduate admissions and does not establish causal relationships.
- Regression assumptions are not fully satisfied; the report documents departures from residual normality.
- The provided R script and PDF are preserved as original project artifacts. Model-selection and validation procedures reflect the original academic workflow, not a newly audited production forecasting pipeline.

## Credits

Joint academic project by **Katia Russo** and **Matteo Zabban** (2024–2025). The underlying *Graduate Admission 2* dataset is credited to its original creators in the report's bibliography.
