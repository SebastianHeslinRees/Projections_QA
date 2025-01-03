# 📊 **QA Script for Population Projections**

## 📝 **Introduction**
This repository contains a script and resources for analysing the Greater London Authority (GLA) population projection data. The primary objective is to identify outliers in the population data and present the findings through tables, visualisations and Dash applications within an HTML report.  

### 🎯 **Goals**
The project focuses on the following key objectives:  
1. **Data Loading**: Load the GLA population projections dataset.  
2. **Utility Functions**: Define reusable functions to support data analysis and reporting.  
3. **Data Processing**:  
    - Perform **basic checks** on the dataset:
      - Determine the range of years covered.
      - Identify missing values, duplicates, and negative values.
      - Analyse descriptive statistics.
      - Perform a breakdown by components.
      - Validate age group ranges.  
4. **Outlier Detection**:
    - Analyse **population consistency over time** for each component:
      - Use **Z-scores** and **Robust Z-scores** to detect outliers.
      - Evaluate data by **component**, **ward**, and **borough**.
      - Address **infinite values** separately.  
    - Identify **total population outliers**:
      - Perform **cross-sectional comparisons**: Analyse differences between boroughs and wards in a given year.
      - Conduct **temporal comparisons**: Measure percentage changes in population over time for boroughs and wards.  
    - Investigate **gender outliers**:
      - Identify anomalies in **gender ratios**.
      - Adjust **outlier thresholds** based on specific components as needed.  
5. **Key Visualisations**: Create meaningful visualisations:
    - Component-wise population distributions.
    - Grouped data by age ranges.
    - Yearly total population trends over time (with breakdowns by component).  
    - Dash applications:
      - **Population Pyramid App**: Display demographic breakdowns.
      - **Line Graph Ward App**: Show trends for individual wards.
      - **Ward Distribution App**: Visualise the distribution of population values across wards.  
6. **HTML Report**:
    - Format tables and charts for inclusion in the HTML report.
    - Produce a user-friendly report layout.
    - Use of some Javascript to enhance table interaction and speed

---

## 📂 **Datasets**
This project analyses two key datasets:  

### **Dataset 1**: Population Projections  
The primary dataset includes borough and ward-level population projections. It is structured as follows:  

#### Main Columns:  
- **gss_code**: Borough geocode (e.g., GSS code).  
- **la_name**: Local Authority name.  
- **Year**: The year of the population data.  
- **Sex**: Gender (male/female).  
- **Age**: Age group or specific age.  
- **Value**: Population count for the given category.  
- **gss_code_ward**: Geocode for the ward.  
- **ward_name**: Name of the ward.  

#### Components:  
This column includes key metrics such as:  
- **net-flow**: Net migration (inflow minus outflow).  
- **popn**: Total population.  
- **birth**: Number of births.  
- **deaths**: Number of deaths.

Below is an example schema for the Dataset 1 table.

**Dataset 1: Population Projections**

| gss_code   | la_name         | year  | sex    | age   | value | component | gss_code_ward | ward_name       |
|------------|-----------------|-------|--------|-------|-------|-----------|---------------|-----------------|
| E09000001  | City of London  | 2012  | female | 0     | 32    | births    | E09000001     | City of London  |
| E09000001  | City of London  | 2012  | male   | 0     | 24    | births    | E09000001     | City of London  |
| E09000001  | City of London  | 2013  | female | 0     | 36    | births    | E09000001     | City of London  |
| E09000001  | City of London  | 2013  | male   | 0     | 35    | births    | E09000001     | City of London  |
| E09000001  | City of London  | 2014  | female | 0     | 26    | births    | E09000001     | City of London  |

### **Dataset 2**: Average Household Size (AHS)  
This dataset includes the average household size (AHS) from 2021 to 2050, aggregated by ward. The outlier detection function, `find_ahs_outliers_with_context`, is applied to this dataset.

Below is an example schema for the Dataset 2 table.

**Dataset 2: Average Household Size (AHS)**

| gss_code_ward | 2021     | 2022     | 2023     | ... | 2048     | 2049     | 2050     |
|---------------|----------|----------|----------|-----|----------|----------|----------|
| E09000001     | 1.729055 | 2.141426 | 2.087426 | ... | 1.950291 | 1.953340 | 1.956169 |
| E05014053     | 2.813790 | 2.548360 | 2.275661 | ... | 2.213891 | 2.224858 | 2.235705 |
| E05014054     | 2.909020 | 2.883138 | 2.922277 | ... | 2.879492 | 2.890862 | 2.901789 |
| E05014055     | 2.951577 | 2.634936 | 2.445635 | ... | 2.375091 | 2.388186 | 2.400488 |
| E05014056     | 3.048425 | 2.873637 | 2.762628 | ... | 2.608712 | 2.606719 | 2.604483 |

---

## 🛠️ **Project Structure**
1. **Load Data**: Import the population projections dataset.  
2. **Define Utility Functions**: Create reusable code for consistent analysis.  
3. **Process Data**: Clean and transform the data for further analysis.  
4. **Basic Checks**: Validate the dataset’s integrity.  
5. **Population Consistency Over Time**: Identify trends and outliers for each component.  
6. **Total Population Outliers**: Detect deviations in total population values across wards and boroughs.  
7. **Gender Outliers**: Analyse anomalies in gender ratios.  
8. **Key Visualisations**: Generate interactive and static charts, including Dash apps for dynamic exploration.  
9. **Average Household Size Outliers**: Identify outliers in the AHS dataset.  
10. **HTML Report**: Collate findings and visualisations into an HTML report.

---

## 🔧 **Required Packages**
Below are the required packages used in this project:  
```python
import pandas as pd
import numpy as np
import pyreadr
import os
import matplotlib.pyplot as plt
import seaborn as sns
from scipy import stats
import dash
from dash import dcc, html
from dash.dependencies import Input, Output
import plotly.express as px
import dash_bootstrap_components as dbc
from scipy.stats import zscore, skew
from typing import Dict
import plotly.io as pio
```

---

## 🛠️ Installation and Usage

To use this script:

1. Clone the repository:
   ```bash
   git clone https://github.com/SebastianHeslinRees/Projections_QA.git
   cd Projections_QA
   ```

2. Install the required packages:
   ```bash
   pip install -r requirements.txt
   ```

3. Open the Jupyter Notebook or your chosen IDE:
   ```bash
   jupyter notebook
   ```

4. Run the notebook to QA population projections dataset.

---

## 📫 Contact

For questions or feedback, please reach out to [sebastian.heslin-rees@london.gov.uk].

---

## 📄 License
Shield: [![CC BY-NC 4.0][cc-by-nc-shield]][cc-by-nc]

This work is licensed under a
[Creative Commons Attribution-NonCommercial 4.0 International License][cc-by-nc].

[![CC BY-NC 4.0][cc-by-nc-image]][cc-by-nc]

[cc-by-nc]: https://creativecommons.org/licenses/by-nc/4.0/
[cc-by-nc-image]: https://licensebuttons.net/l/by-nc/4.0/88x31.png
[cc-by-nc-shield]: https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg

please email [sebastian.heslin-rees@london.gov.uk] for license infomation.

---

## 📄 Acknowledgements

- [GLA Population Projection]([https://www.gla.gov.uk](https://www.london.gov.uk/)) for the dataset.
