# Inference of COVID-19 Vaccine Efficacy & Uncertainty via Bayesian Methods

[![R](https://img.shields.io/badge/R-276DC3?style=for-the-badge&logo=r&logoColor=white)](https://www.r-project.org/)
[![JAGS](https://img.shields.io/badge/JAGS-Bayesian%20MCMC-purple.svg)](https://mcmc-jags.sourceforge.io/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![University](https://img.shields.io/badge/University-Padova%20%7C%20Physics-navy.svg)](https://www.unipd.it/)

A Bayesian statistical inference project analyzing clinical trial data for major COVID-19 vaccines (Pfizer-BioNTech, Moderna, AstraZeneca, etc.), quantifying efficacy point estimates, 95% Credible Intervals, and age-stratified effectiveness using **JAGS** (Just Another Gibbs Sampler) and **MCMC sampling**.

---

## 📌 Overview & Mathematical Formulation

Estimating vaccine efficacy ($\epsilon$) from Phase III clinical trial data requires robust uncertainty quantification, particularly across small demographic sub-samples.

### 1. Efficacy Parameter Definition
Vaccine efficacy $\epsilon$ is defined as the relative reduction in infection risk between the vaccinated group and placebo group:

$$\epsilon = 1 - \frac{\theta_{\text{vac}}}{\theta_{\text{placebo}}}$$

where $\theta_{\text{vac}}$ and $\theta_{\text{placebo}}$ represent the attack rates (infection probabilities per person-year) in the respective trial arms.

### 2. Bayesian Hierarchical Likelihood & Priors
Infection counts in each arm are modeled using Binomial or Poisson likelihoods:

$$k_{\text{vac}} \sim \text{Binomial}(N_{\text{vac}}, \theta_{\text{vac}}), \quad k_{\text{placebo}} \sim \text{Binomial}(N_{\text{placebo}}, \theta_{\text{placebo}})$$

Uninformative or informative Beta/Gamma conjugate priors are assigned to infection parameters:

$$\theta_{\text{vac}} \sim \text{Beta}(\alpha_1, \beta_1), \quad \theta_{\text{placebo}} \sim \text{Beta}(\alpha_2, \beta_2)$$

Using **JAGS MCMC Gibbs sampling**, posterior distributions $P(\epsilon | \text{Data})$ are generated to evaluate posterior mean efficacy and **95% Highest Posterior Density (HPD) Credible Intervals**.

---

## 🔬 Key Analytical Features

- **JAGS Bayesian Model Definition**: Custom JAGS scripts modeling clinical trial data across different vaccine manufacturers.
- **MCMC Convergence Diagnostics**: Trace plots, autocorrelation analysis, and Gelman-Rubin diagnostics ($\hat{R}$).
- **Posterior Probability Density Estimation**: Full posterior distribution density curves highlighting 95% Credibility Intervals.
- **Age-Stratified Efficacy Analysis**: Demographic breakdown exploring efficacy variations between younger ($<65$) and older ($\ge 65$) age cohorts.

---

## 📁 Repository Structure

```
Advance-Statistics-in-Physics_Project/
├── Final.ipynb             # Main Jupyter Notebook containing JAGS models & MCMC analysis
├── covid19w.pdf            # Written research paper / report
├── project description.pdf # Course assignment guidelines
├── data/                   # Clinical trial datasets (Pfizer, Moderna, AstraZeneca, etc.)
├── README.md               # Project documentation
└── .gitignore              # Git ignore rules
```

---

## 🛠️ Setup & Requirements

### Prerequisites
- Python 3.8+ & R environment
- JAGS (Just Another Gibbs Sampler) installed on your system (`brew install jags` on macOS or `apt install jags` on Linux).

### R & Python Packages
Required statistical packages:
- **R**: `rjags`, `coda`, `ggplot2`, `tidyverse`, `bayesplot`
- **Python**: `numpy`, `scipy`, `pandas`, `matplotlib`, `seaborn`, `rpy2`

---

## 🚀 How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/mojee13/Advance-Statistics-in-Physics_Project.git
   cd Advance-Statistics-in-Physics_Project
   ```

2. Open the analysis notebook:
   ```bash
   jupyter notebook Final.ipynb
   ```

3. Execute cells to run JAGS Gibbs sampling chains, plot posterior density distributions, and display 95% Credibility Interval tables.

---

## 📚 References & Paper

For full narrative analysis and tables, consult the included report:
📄 [`covid19w.pdf`](./covid19w.pdf)
