# Oral-B Retail Activation Scoring

A KNIME workflow that scores retail locations for Oral-B activation using
local demographic and geographic data, comparing Logistic Regression against
Random Forest to see which predicts better.

## What it does

Each location (`PdV Code` — Italian for "Punto di Vendita," point of sale)
comes with features like water hardness, number of nearby dental hygienists,
distance from a dentist, population breakdown by age/marital status,
education, and household income. The workflow:

1. Reads and cleans the raw Excel data (two source files, joined together)
2. Splits into train/test, normalizes the features
3. Trains **two models in parallel** — Logistic Regression and Random Forest
4. Evaluates both with a Scorer + ROC Curve to compare performance
5. Uses the winning model's probability output to calculate an
   `Expected_Profit` per location
6. Applies a rule to flag each location as a `Recommended_Activation` or not

## Output

The scored output (`PredictionOutput` sheet) includes, per location: the
predicted probability of a successful activation, the calculated expected
profit, and the final activation recommendation — so it's not just a model,
it's a ranked shortlist of where activation is worth the investment.

## Files

- `workflow.knime` — the KNIME workflow definition
- `workflow.svg` — visual diagram of the full pipeline
- Node folders (`Excel Reader`, `Logistic Regression Learner`,
  `Random Forest Learner`, `Scorer`, `ROC Curve`, etc.) — each node's
  settings and (where applicable) output data

## Tools

KNIME Analytics Platform · Logistic Regression · Random Forest

## Running it

Open `workflow.knime` in KNIME Analytics Platform (free download from
knime.com) — the whole folder is a self-contained workflow, just point
KNIME at this directory.
