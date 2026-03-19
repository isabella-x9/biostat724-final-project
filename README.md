# Bayesian Analysis of Used Car Prices

## Overview

This project investigates how vehicle characteristics influence the price of used cars using a Bayesian regression framework.

The analysis focuses on estimating the effects of variables such as mileage, model year, accident history, transmission type, fuel type, and brand on vehicle price. A Bayesian linear regression model is implemented using Gibbs sampling to estimate posterior distributions for model parameters and to quantify uncertainty in the estimated effects.

The outcome variable is the logarithm of car price, which reduces skewness in the price distribution and improves model stability. 

---

## Data

The dataset contains listings of used vehicles with information including:

- Price
- Brand
- Model year
- Mileage
- Transmission type
- Fuel type
- Accident history

For computational and interpretability purposes, the analysis restricts attention to a subset of the most common vehicle brands.

Continuous variables (mileage and model year) are standardized before modeling.

The dataset used for the analysis is located in: 
```
data/train.csv
```

---

## Model

We use a Bayesian linear regression model:

$$
y \sim N(X\beta, \sigma^2)
$$

where

- $y$ is the log price
- $X$ is the design matrix of predictors
- $\beta$ are regression coefficients
- $\sigma^2$ is the residual variance

### Priors

Weakly informative priors are used:

- $\beta \sim N(0, \tau^2 I)$
- $\sigma^2 \sim \text{Inverse-Gamma}(a,b)$

with

- $\tau^2 = 100^2$
- $a = 0.01$
- $b = 0.01$

Posterior samples are generated using a Gibbs sampler.

---

## Repository Structure 

```
project-root/
│
├── analysis/
│ └── bayesian_model_izzi.Rmd # Bayesian model analysis
│
├── data/
│ └── train.csv # Used car dataset
│
├── 724 Final Project.Rproj # RStudio project file
│
└── README.md
```

---

## Running the Analysis

1. Open the project in RStudio using the `.Rproj` file.

2. Install required packages if necessary:

```r
install.packages(c(
  "tidyverse",
  "janitor",
  "forcats",
  "MASS",
  "coda"
))
```

3. Run the analysis by knitting the R Markdown file:

```
analysis/bayesian_model_izzi.Rmd
```





