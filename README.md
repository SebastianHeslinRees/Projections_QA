# 📊 QA Script for Population Projections

---

## 📝 Introduction

This repository contains a notebook designed to identify outliers in the Greater London Authority (GLA) population projection data. The analysis involves loading the dataset, preprocessing the data, defining utility functions, performing outlier detection, and presenting the results through visualisations.

### 🎯 Goals

The analysis focuses on the following objectives:

- **Load and preprocess** the population projections dataset.
- Define utility functions for effective use.
- Perform **basic checks** on the dataset, including:
  - Range of years covered.
  - Missing values.
  - Duplicates.
  - Descriptive statistics.
  - Breakdown by components.
  - Detecting negative values.
  - Age group ranges.
- **Outlier Detection** over time for each component:
  - Identify outliers using **Z-scores** and **Robust Z-scores**.
  - Analyse by **component**, **ward**, and **borough**.
  - Handle **infinite values** separately.
- **Total Population Outliers**:
  - Compare outliers using Z-scores and Robust Z-scores.
  - Perform **cross-sectional comparisons**: Examine changes between boroughs and wards for a given year.
  - Conduct **temporal comparisons**: Measure percentage changes between years for both boroughs and wards.
  - Handle **infinite values** separately.
- **Gender Outliers**:
  - Investigate abnormal **gender ratios**.
  - Analyse by component.
  - Adjust the **outlier standard deviation thresholds** as needed based on different components.
- **Key Visualisations**:
  - Display the distribution of components.
  - Group data by **age ranges**.
  - Visualise **yearly totals**.
  - Show yearly total trends over time, broken down by components.
  - Create **population pyramids**.
- **Collate Outliers**: Summarise and determine the key outlier rows.

---

## 📂 Dataset

The functions in this notebook are designed to work with datasets produced by the GLA Population Projection Workflow. The current iteration of this workflow contains several key columns and components as outlined below:

### Main Columns

- **gss_code**: Borough geocode (e.g., GSS code).
- **la_name**: Local Authority name.
- **gss_code_ward**: Geocode for the ward.
- **ward_name**: Name of the ward.
- **Year**: The year of the population data.
- **Sex**: The gender (male/female).
- **Age**: The age group or specific age.
- **Value**: Count of the population in the given category.

### Components Column

This column includes specific population-related metrics:
- **net-flow**: Population migration inflow minus migration outflow.
- **popn**: Total population.
- **birth**: Number of births.
- **deaths**: Number of deaths.

---

## 🛠️ Structure

This notebook is structured as follows:

1. [Load and Preprocess](#load-and-preprocess) the population projections dataset.
2. [Define Utility Functions](#define-utility-functions) for effective use.
3. [Process Data](#process-data).
4. [Basic Checks](#basic-checks) on the dataset.
5. [Population Consistency Over Time](#population-consistency-over-time) for each component.
6. [Total Population Outliers](#total-population-outliers).
7. [Gender Outliers](#gender-outliers).
8. [Key Visualisations](#key-visualisations).
9. [Collate Outliers](#collate-outliers) to determine key outlier rows.

---

## 🛠️ Installation and Usage

To use this script:

1. Clone the repository:
   ```bash
   [git clone https://github.com/your-username/repo-name.git](https://github.com/SebastianHeslinRees/Projections_QA.git)
   cd repo-name
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

please email [sebastian.heslin-rees@london.gov.uk] for license infomation.

---

## 📄 Acknowledgements

- [GLA Population Projection]([https://www.gla.gov.uk](https://www.london.gov.uk/)) for the dataset.
