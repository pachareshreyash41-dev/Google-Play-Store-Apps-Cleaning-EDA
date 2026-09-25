# Google Play Store Apps: Data Cleaning & Exploratory Data Analysis (EDA)

## Overview
This repository contains a Data Analysis project focused on cleaning, transforming, and exploring dataset attributes from the Google Play Store. The main objective is to handle dataset anomalies (e.g., shifted rows, inconsistent data types, string formatting issues), preprocess numeric variables, and perform Exploratory Data Analysis (EDA) to uncover insights regarding app ratings, categories, pricing models, and download volumes.

---

## Project Structure & Features

### 1. Data Cleaning & Wrangling
- **Shifted Row Correction:** Filters and removes anomalous/shifted data rows (e.g., invalid category values like `'1.9'`).
- **Data Type Conversion & Formatting:**
  - `Installs`: Removed `+` and `,` symbols; converted to numeric format.
  - `Price`: Stripped `$` characters and converted to float values.
  - `Reviews`: Parsed strings into integer representations.
  - `Size`: Built custom size conversion function (`convert_size`) to standardize sizes from megabytes (`M`) and kilobytes (`k`) into numeric megabytes (`Size_MB`). Imputed missing values (`Varies with device`) using category-level medians.
- **Missing Value Imputation:** Handled missing `Rating` values by replacing them with the category-level median rating.
- **Deduplication:** Identified and removed duplicate app entries, prioritizing records with the highest review counts.

### 2. Visualizations & Exploratory Data Analysis
- **Category Counts:** Identified top app categories by overall count using Seaborn bar plots.
- **Free vs. Paid App Comparison:** Evaluated free vs. paid app proportions via pie charts and analyzed installation volume distributions using logarithmic scale boxplots.
- **Price vs. Rating Analysis:** Examined price distribution against app ratings, filtering out high-priced outlier apps.
- **App Size vs. Ratings:** Hexbin joint plots to measure density correlation between app size (`Size_MB`) and ratings.
- **Category Performance:** Ranked categories based on total install counts and analyzed distributions across target age groups (`Content Rating`).
- **Correlation Matrix:** Heatmap showing correlations between continuous variables (`Rating`, `Reviews`, `Size_MB`, `Installs`, `Price`).
- **High-Rated Top Apps Analysis:** Highlighted top-performing categories housing apps with ratings $\ge 4.5$ and installs $\ge 1,000,000$.

---

## Key Insights
1. **Reviews & Installs:** Strong positive correlation ($0.78$) between review volume and total installations.
2. **Pricing Impact:** Paid apps exhibit a negative correlation ($-0.71$) with ratings in this dataset, indicating higher user expectations for paid software.
3. **App Size:** App size (`Size_MB`) shows a moderate positive correlation ($0.53$) with install counts, suggesting users do not avoid downloading larger files if quality is maintained.
4. **Dominant Categories:** Categories like Games, Tools, and Family drive the highest average installation volumes on the Play Store.

---

## Requirements

```text
python >= 3.8
pandas
numpy
matplotlib
seaborn
jupyter
