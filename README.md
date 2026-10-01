# Household Energy Usage Analysis

Clustering, regression, and classification applied to 2+ million household electricity
readings to uncover consumption patterns and segment usage behaviour.

## Overview

This project analyzes household energy usage data to uncover meaningful patterns
through regression, classification, and clustering. By exploring the relationship
between key metrics like Global Active Power and Global Intensity, the analysis groups
energy usage into behavioural segments — helping identify trends, anomalies, and
opportunities for optimization.

## Objective

- Identify patterns and trends in household energy consumption
- Predict power consumption from other readings using regression
- Classify consumption into Low / Medium / High usage bands
- Cluster households into distinct usage-pattern groups
- Surface actionable insights for energy optimization and anomaly detection

## Dataset

- **2,049,280 minute-level household power readings**
- Fields: Global Active Power (kW), Global Reactive Power, Voltage, Global Intensity,
  and three Sub-Metering channels (kitchen, laundry, and climate control/water heater)

## Methodology

1. **Data preprocessing** — handled missing values, corrected data types, scaled
   numerical features
2. **Exploratory Data Analysis** — examined relationships between power metrics,
   checked for outliers, compared average usage across sub-metering channels
3. **Regression** — trained Linear Regression and Random Forest Regressor models to
   predict Global Active Power from voltage, intensity, and sub-metering data
4. **Classification** — binned consumption into Low/Medium/High and trained Decision
   Tree and Random Forest classifiers to predict the usage band
5. **Clustering** — applied K-Means (k=3) to group consumption patterns, with cluster
   quality checked using the Calinski-Harabasz and Davies-Bouldin indices

## Key Findings

- **Weekend energy consumption exceeds weekday consumption**, driven largely by
  Sub-Metering 3 (climate control / water heating), which is higher at night than
  during midday
- **A strong positive correlation exists between Global Active Power and Global
  Intensity** — expected given their underlying relationship, and a useful sanity
  check on the data
- Consumption clusters separated into three clear usage bands (low, moderate, high),
  with a high Calinski-Harabasz score (527,253) indicating well-separated clusters
- Regression and classification models scored very highly (R² of 0.999, 99%
  classification accuracy) — a result of how directly related the input features
  are to the target by definition, rather than a claim of complex predictive skill

## Tools & Libraries

`Python` · `Pandas` · `NumPy` · `Matplotlib` · `Seaborn` · `Scikit-learn`

## Repository Structure

```
├── household_energy_usage_analysis.ipynb   # Full analysis notebook
├── Household_Energy_Usage_Analysis.docx    # Written project report
├── data/                                   # Raw / processed data (if shareable)
└── README.md
```

## Takeaway

The clustering and classification results were clean mainly because the underlying
features are physically related to the target — a useful reminder to check *why* a
model scores well before treating a high accuracy number as the headline result.
The more genuinely useful finding here was behavioural: weekend and nighttime spikes
tied to climate-control usage, which is the kind of pattern an energy provider could
actually act on.
