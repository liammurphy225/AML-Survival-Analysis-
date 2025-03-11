# Survival Analysis

## Overview
This project focuses on survival analysis using statistical and machine learning techniques. The analysis includes Kaplan-Meier estimations, Cox proportional hazards models, Aalen's additive regression models, and random survival forests. Data preprocessing and visualization are also integral parts of the workflow.

## Table of Contents
- [Overview](#overview)
- [Project Structure](#project-structure)
- [Dataset](#dataset)
- [Installation](#installation)
- [Usage](#usage)
- [Analysis Methods](#analysis-methods)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)

## Project Structure
```
├── Survival_Analysis.Rmd        # R Markdown file for the analysis
├── myeloid.csv                  # Dataset file (example data from the survival package)
├── README.md                    # Project documentation
├── results/                     # Directory for outputs and plots
└── models/                      # Directory for saved model objects
```

## Dataset
### Description
The dataset used in this analysis includes the following columns:
- **futime**: Follow-up time in days.
- **death**: Indicator variable for survival status (1 = event, 0 = censored).
- **trt**: Treatment group.
- **sex**: Gender of the individual.
- **flt3**, **txtime**, **crtime**, **rltime**: Covariates related to disease and treatment.

### Source
The dataset `myeloid.csv` is an example dataset provided in the `survival` R package. Ensure it is available in the working directory for analysis.

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/liammurphy225/survival-analysis.git
   ```
2. Install the required R packages:
   ```R
   install.packages(c("survival", "ranger", "ggplot2", "dplyr", "ggfortify", "broom", "gtsummary"))
   ```
3. Open `Survival_Analysis.Rmd` in your R IDE (e.g., RStudio).

## Usage
1. Load the dataset and preprocess the data:
   ```R
   myeloid <- na.omit(myeloid)
   ```
2. Run the R Markdown file to execute the analysis and generate results.
3. Outputs include:
   - Kaplan-Meier curves.
   - Cox proportional hazards model summaries.
   - Variable importance from random survival forests.
   - Combined survival curves using multiple models.

## Analysis Methods
- **Kaplan-Meier Estimation**:
  - Visualize survival probabilities over time.
  - Conduct log-rank tests to compare survival between groups.

- **Cox Proportional Hazards Model**:
  - Fit a semi-parametric survival model using covariates.
  - Evaluate significance of predictors and plot survival curves.

- **Aalen's Additive Regression Model**:
  - Analyze time-dependent covariate effects.
  - Visualize cumulative hazard functions.

- **Random Survival Forests (RSF)**:
  - Ensemble learning method for survival analysis.
  - Generate variable importance rankings.
  - Visualize survival curves for individual patients and averages.

- **Model Comparison**:
  - Combine Kaplan-Meier, Cox, and RSF survival estimates in a single plot.
  - Assess model fit using Harrell's c-index.

## Results
- Kaplan-Meier survival estimates provide insights into overall and group-specific           survival probabilities.
   - At 1 year the estimated survival probability is 79.4%  with a 95% CI: (0.729 – 0.865).
   - Number at risk: 108, with 28 events (deaths).
   - Treatment A: 60 patients, 43 deaths, expected = 34.2.
   -Treatment B: 76 patients, 46 deaths, expected = 54.8.
   - Chi-squared = 3.7, p = 0.05, suggesting borderline statistical significance.

- Cox proportional hazards model identifies significant covariates (e.g., `rltime`).
  Key Time Points:
   -At 191 days, survival drops to 97%.
   -At 518 days, survival is 66%.
   -At 1,000 days, survival is around 40%.
   -At 2,283 days, survival drops to ~25%.

-The Aalen model is a non-parametric additive model that assumes that the cumulative hazard H(t) for a subject can be expressed as a(t) + X * B(t) where a(t) is a time independent intercept term, X is a vector of covariates(could be time dependent) and B(t) is a time-dependent matrix of coefficients.

   Significant Predictors:
   -Intercept (p = 9.94e-07): Suggests an overall baseline hazard effect.
   -rltime (p = 1.11e-06): Highly significant, indicating a strong relationship with          survival.
   Non-Significant Predictors:
   -Treatment (trtB), sex (sexm), FLT3 mutation (flt3B, flt3C), txtime, and crtime have p-     values above 0.05, suggesting they are not significantly associated with survival in       this model.
   Overall Model Fit:
   -The model is statistically significant (Chisq = 40.71, p = 9.21e-07), meaning at least    one predictor significantly contributes to explaining survival.

- Random survival forests highlight variable importance and provide patient-specific
  survival predictions.
- Combined plots facilitate model comparison.

## Contributing
1. Fork the repository.
2. Create a new branch:
   ```bash
   git checkout -b feature-name
   ```
3. Commit your changes and push to the branch:
   ```bash
   git commit -m "Add new feature"
   git push origin feature-name
   ```
4. Open a pull request.

## License
This project is licensed under the [MIT License](LICENSE).

