# Bayesian Update of Student Test Scores

A short Python notebook that visualizes a Bayesian normal-normal update: how a prior belief about an average test score is combined with observed data to produce a posterior estimate.

## Overview

The notebook `Untitled10__2_.ipynb` takes eight student test scores, compares three quantities, and plots them in a single chart:

- the **prior mean** (belief before seeing data)
- the **sample mean** (what the data say)
- the **posterior mean** (the Bayesian compromise between the two)

The chart is saved as `chart.png`, intended for use in a Word document or report. The notebook's comments refer to the posterior calculation as coming from "Question 3", so it appears to accompany a coursework or assignment problem.

## Data and Assumptions

| Item | Value |
|---|---|
| Observed scores | 68, 72, 75, 70, 78, 74, 76, 71 (n = 8) |
| Prior mean | 70 |
| Prior variance | 16 (SD = 4) |
| Data (likelihood) variance | 25 (SD = 5), assumed known |
| Sample mean | 73.0 |

These variances are inferred from the formula in the code: the `1/16` and `8/25` terms are the prior precision and the data precision for n = 8 observations.

## Method

For a normal prior with a normal likelihood of known variance, the posterior is also normal:

```
posterior variance = 1 / (1/σ₀² + n/σ²)
posterior mean     = posterior variance × (μ₀/σ₀² + n·x̄/σ²)
```

With σ₀² = 16, σ² = 25, n = 8, μ₀ = 70 and x̄ = 73:

- Posterior variance ≈ 2.614 (SD ≈ 1.62)
- Posterior mean ≈ **72.51**

The posterior mean sits between the prior (70) and the sample mean (73), and is pulled closer to the data because eight observations carry more weight than the prior.

## Output

A bar chart of the eight student scores with three dashed horizontal lines marking the prior mean (70), sample mean (73) and posterior mean (72.51). Output is saved to `chart.png` at 200 dpi.

## Getting Started

### Requirements

- Python 3.8+
- matplotlib
- jupyter

```bash
pip install matplotlib jupyter
```

### Run

```bash
jupyter notebook Untitled10__2_.ipynb
```

Run all cells. The figure appears on screen and `chart.png` is written to the working directory.

## Project Structure

```
.
├── Untitled10__2_.ipynb    # Calculation and plot
├── chart.png               # Generated figure
└── README.md
```

## Notes and Possible Extensions

- Consider renaming the notebook to something descriptive, such as `bayesian_normal_update.ipynb`.
- Plot the prior, likelihood and posterior as normal density curves to show how the distribution narrows after the update.
- Add a 95% credible interval for the posterior mean (about 72.51 ± 1.96 × 1.62).
- Wrap the update in a reusable function so different priors and datasets can be tried.
