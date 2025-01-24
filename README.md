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
   git clone https://github.com/your-username/survival-analysis.git
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
- Kaplan-Meier survival estimates provide insights into overall and group-specific survival probabilities.
- Cox proportional hazards model identifies significant covariates (e.g., `rltime`).
- Random survival forests highlight variable importance and provide patient-specific survival predictions.
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

