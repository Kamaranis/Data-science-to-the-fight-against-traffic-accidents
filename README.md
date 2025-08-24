# Data Science for Road Safety: Data Preparation & Analysis

## 📄 Project Overview

This project applies the initial, critical phases of the **CRISP-DM methodology** to analyze fatal traffic accidents in the United States. The primary goal is to perform a comprehensive data preparation and feature engineering process on the **Fatality Analysis Reporting System (FARS)** dataset from the NHTSA, building a robust foundation for future predictive modeling.

This repository covers the first three phases of the data science lifecycle:
1.  **Business Understanding:** Defining the problem of road safety and identifying key analytical goals, such as understanding temporal trends and geographical "black spots".
2.  **Data Understanding:** Exploring multiple raw data tables to assess their structure, quality, and relevance.
3.  **Data Preparation:** A deep dive into cleaning, transforming, and engineering features to create a single, analysis-ready dataset.

## ✨ Analysis Showcase & Methodology

The core of this project lies in its methodical and transparent data preparation pipeline, which transforms complex, multi-table raw data into a clean, feature-rich dataset.

*   **Multi-Source Data Integration:**
    *   Successfully merged over eight different tables from the FARS 2020 dataset (e.g., `accident`, `person`, `vehicle`, `weather`) into a unified analytical table.
    *   Integrated and harmonized datasets from three consecutive years (2018-2020) to enable time-series analysis.

*   **Advanced Feature Engineering & Transformation:**
    *   **Binary Feature Creation:** Converted multiple categorical variables into meaningful binary flags (0/1) to simplify complexity for machine learning models. Examples include:
        *   `DRINKING` & `DRUGS`: Transformed from multi-level codes into simple binary indicators of substance use, respecting the presumption of innocence for "unknown" or "unreported" cases.
        *   `VEHICLECC` & `DRIMPAIR`: Created binary features to represent the presence of mechanical failure or driver impairment.
        *   `NIGHT_HOUR`: Engineered a binary variable from timestamps to flag accidents occurring at night (6 PM - 6 AM).
    *   **Derived Features:** Created new variables from existing ones, such as calculating vehicle `AGE` from the model year and creating age groups (`AGE_GRUP`) from driver ages.

*   **Rigorous Data Cleaning and Imputation Strategy:**
    *   Methodically identified and handled thousands of missing (`NA`) and out-of-range values (e.g., `99`, `9999`) resulting from data merges and reporting gaps.
    *   Implemented a logical imputation for `MOD_YEAR`, filling missing values for a given vehicle with the model year of the primary vehicle in the same accident.
    *   Filtered out irrelevant records, such as those involving non-motorized vehicles (`VEH_NO = 0`) or specific non-causal driver roles (`DRIVERRF`), to create a focused dataset on primary causal factors.

*   **Dimensionality Reduction with PCA:**
    *   Conducted a **Principal Component Analysis (PCA)** on the final, cleaned numerical variables to identify the main drivers of variance in the data.
    *   The analysis revealed that the first three principal components explain approximately **37%** of the total variance, with strong contributions from variables like `DRINKING` and `DRUGS`. This confirms the relevance of the engineered features and prepares the data for more efficient modeling.

## 💻 Technologies Used

*   **Language:** R
*   **Core Libraries:**
    *   **Tidyverse** (`dplyr`, `readr`): For data manipulation, cleaning, and transformation.
    *   **`ggplot2`**: For data visualization (used in the full analysis).
    *   **`stats`**: For conducting the Principal Component Analysis (`prcomp`).
*   **Environment:** RStudio with R Markdown

## 🏆 Project Outcome: Analysis-Ready Datasets

This project delivers three clean and processed datasets, ready for the next phases of a data science project (modeling and evaluation):
1.  **`analysis18_20`**: A time-series table containing accident cases, year, and fatality counts from 2018-2020.
2.  **`accFacts20`**: The main feature-rich dataset containing over 25 engineered variables about accident factors (driver, vehicle, environment).
3.  **`accBpoint20`**: A geographical dataset containing location information (State, County, Lat/Lon) to identify and map accident "black spots".

## 🚀 Getting Started

To explore the data preparation process:
1.  Clone the repository.
2.  Ensure you have R and RStudio installed.
3.  Install the required packages as listed in the R Markdown file (e.g., `tidyverse`, `stats`).
4.  Run the `.Rmd` notebook to follow the entire step-by-step logic, from raw data loading to the final PCA.

## 👤 Author

**Antonio Barrera Mora**

*   **LinkedIn:** https://www.linkedin.com/in/anbamo/
*   **GitHub:** @Kamaranis
