# The Climate Inequality Paradox
### Responsibility vs. Climate Vulnerability in High- and Low-Income Nations
**COGS 108 — Data Science in Practice | UC San Diego | Winter 2026**

---

## Overview

This project investigates the **Climate Inequality Paradox**: the phenomenon where 
the nations least responsible for climate change suffer its consequences the most. 
Using three publicly available datasets spanning 2005–2023, we quantify the 
relationship between CO₂ emissions responsibility and climate disaster vulnerability 
across 164 countries and 1,932 country-year observations.

---

## Research Question

> *Were higher per-capita CO₂ emissions associated with greater climate-related 
> disaster impacts — in the form of higher mortality and reduced GDP growth — for 
> lower-income countries than for higher-income countries between 2005 and 2023?*

---

## Key Findings

- **19× Inequality Gap:** For every ton of CO₂ a low-income country emits, it 
  suffers nearly **19 times more human disaster loss** than a high-income country 
  for the same unit of emission
- **Emissions vs. Responsibility:** High-income nations emit an average of 11.6 
  tons CO₂/capita — over **31× more** than low-income nations at 0.37 tons
- **GDP Suppression:** Low-income nations experience a ~2 percentage point GDP 
  growth decline as disaster severity increases, while high-income economies remain 
  essentially flat
- **Geographic Concentration:** 75% of the top 20 most climate-injustice-affected 
  nations are Low Income or Lower-Middle Income

| Income Group | Avg CO₂ (Tons/Capita) | Avg Deaths per 100k | Avg Inequality Ratio |
|---|---|---|---|
| Low Income | 0.368 | 3.644 | 22.399 |
| Lower-Middle | 1.606 | 9.262 | 7.276 |
| Upper-Middle | 4.427 | 4.463 | 1.537 |
| High Income | 11.623 | 6.228 | 1.207 |

---

## The Inequality Ratio

A core contribution of this project is the **Inequality Ratio** metric:

$$\text{Inequality Ratio} = \frac{\text{Disaster Deaths \& Missing per 100k}}{\text{CO}_2 \text{ Tons per Capita}}$$

This normalizes disaster impact against emissions responsibility, enabling 
apples-to-apples comparison across countries with vastly different economic profiles. 
Rather than asking *"how many people died?"*, it asks *"how many people died per ton 
of CO₂ that country was responsible for emitting?"*

---

## Datasets

| Dataset | Source | Observations |
|---|---|---|
| CO₂ Emissions Per Capita | Our World in Data | 4,085 country-years |
| Disaster Death Rates | EM-DAT via Our World in Data | 1,966 country-years |
| GDP Per Capita (PPP) | World Bank via Our World in Data | 4,005 country-years |

All three datasets were merged on country code and year, restricted to 2005–2023, 
and filtered to real countries only (valid ISO 3-letter codes). Final merged dataset: 
**1,932 observations across 164 countries.**

---

## Methods

- **Exploratory Data Analysis (EDA)** across income quartiles defined by `pd.qcut` 
  on GDP per capita
- **Log-log scatter plots** to visualize wealth-emissions and wealth-inequality 
  relationships across several orders of magnitude
- **Median lines** per income group to surface structural patterns robust to 
  individual disaster outliers
- **OLS regression** on log-scaled axes to quantify the inequality ratio trend
- **GDP growth analysis** binned by disaster severity quintiles with 95% confidence 
  intervals
- **Choropleth mapping** via Plotly for geographic visualization of inequality ratios

---

## Stack

![Python](https://img.shields.io/badge/Python-3.11-blue)
![Pandas](https://img.shields.io/badge/Pandas-2.0-lightblue)
![Seaborn](https://img.shields.io/badge/Seaborn-0.12-green)
![Plotly](https://img.shields.io/badge/Plotly-5.0-purple)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)

- **Python 3.11**
- **Pandas** — data wrangling and merging
- **Seaborn / Matplotlib** — static visualizations
- **Plotly Express** — interactive choropleth map
- **NumPy** — numerical operations and log transforms

---

## Authors

This project was completed as part of COGS 108 at UC San Diego (Winter 2026).

| Author | Contributions |
|---|---|
| **Jacob Ortiz** | Analysis, Background research, Conceptualization, Data curation, Experimental investigation, Methodology, Project administration, Software, Writing |
| **Muhammed Abdalla** | Software, Writing — original draft, Writing — review & editing |
| **Katherine Chui** | Software, Visualization, Writing — review & editing |
| **Iha Gadiya** | Analysis, Methodology, Visualization, Writing — review & editing |
| **Jeanne Lee** | Background research, Conceptualization, Analysis, Methodology, Visualization, Writing, Project Administration |

---

## References

1. "Current GHG Levels," NOAA. https://www.climate.gov/ghg/current-levels
2. "CO₂ emissions per capita," Our World in Data. https://ourworldindata.org/grapher/co-emissions-per-capita
3. "Climate Change," Our World in Data. https://ourworldindata.org/climate-change
4. "Global natural disaster death rates," Our World in Data. https://ourworldindata.org/grapher/natural-disaster-death-rates
5. "Climate Inequality Report 2023," World Inequality Lab. https://wid.world/wp-content/uploads/2023/01/CBV2023-ClimateInequalityReport-2.pdf
6. Diffenbaugh & Burke, "Global warming has increased global economic inequality," *PNAS*, 2019.
7. Zahnow et al., "Climate change inequalities: A systematic review," *ScienceDirect*, 2025.