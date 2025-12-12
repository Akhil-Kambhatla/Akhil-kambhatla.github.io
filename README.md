# The Geography of Fast Food Pricing: Economic Determinants of Menu Prices Across America

A comprehensive data science tutorial analyzing how local economic conditions, minimum wages, and business models influence fast-food menu pricing across 6,717 restaurants in the United States.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [System Requirements](#system-requirements)
3. [Installation](#installation)
4. [Data Files Setup](#data-files-setup)
5. [Running the Notebooks](#running-the-notebooks)
6. [Troubleshooting](#troubleshooting)
7. [Expected Results](#expected-results)

---

## Project Overview

This tutorial demonstrates the complete data science lifecycle:
- **Data Collection**: Web scraping from Chipotle, Domino's, Papa John's, and minimum wage data
- **Data Integration**: Merging with US Census income data, DOL minimum wage data, and BLS regional food prices
- **Statistical Analysis**: 5 hypothesis tests using ANOVA and regression
- **Machine Learning**: 5 predictive models (Linear Regression, Ridge, XGBoost, CatBoost, Neural Network)

---

## System Requirements

**Hardware Requirements:**
- **RAM**: 15GB minimum required
- **Storage**: 2GB free space in Google Drive
- **GPU**: T4 GPU recommended (available in Google Colab free tier)

**Important Note About RAM:**
Because Google Colab's free tier RAM is not sufficient to run the entire analysis in one notebook, we have split the project into 2 separate notebooks:

1. **Notebook 1**: Data Collection → Preprocessing → EDA → Hypothesis Testing
2. **Notebook 2**: Machine Learning Model Training and Deployment

This split ensures smooth execution without memory errors.

---

## Installation

**No manual installation needed.** Google Colab comes with most libraries pre-installed.

If you encounter an error saying a library is not installed (e.g., `ModuleNotFoundError: No module named 'xgboost'`), install it directly in Colab:

```python
!pip install xgboost
```

Or for multiple packages:

```python
!pip install xgboost catboost transformers
```

Common packages that may need installation:
- `xgboost` (gradient boosting)
- `catboost` (gradient boosting with categorical handling)
- `transformers` (BERT embeddings)
- `folium` (interactive maps)

---

## Data Files Setup

### Step 1: Access the Shared Google Drive

All required data files are available in this shared Google Drive folder:

**Link**: https://drive.google.com/drive/u/0/folders/13Qsasbw_tvR5IzkeL9_DdrsE2OzAg60d

This folder contains:
- **Restaurant data** (4 files): Chipotle, Domino's, Papa John's menus and locations
- **USDA rural-urban codes** (1 file)
- **Regional food retail prices** (4 files): West, South, Midwest, Northeast regions
- **US ZIP codes** (1 file): All ZIP codes for mapping
- **All Dataset** file that we store post processing.
**Total: 11 data files**

### Step 2: Add files to your Drive

1. Click the Google Drive link above
2. Right click on folder, then Organize and then Add shortcut to your Drive


***IMP***
4. Your final structure should be:
   ```
   My Drive/
   └── [folder_name(if any)]/
       └── Data/
           ├── ChipotleMenuByLocation.csv
           ├── ChipotleLocations.csv
           ├── Dominos_ALL_USA.csv
           ├── papajohns_menu_USA.csv
           ├── Ruralurbancontinuumcodes2023.csv
           ├── Food_retail_prices_Midwest_region_US.csv
           ├── Food_retail_prices_Northeast_region_US.csv
           ├── Food_retail_prices_South_region_US.csv
           ├── Food_retail_prices_West_region_US.csv
           └── zip_income_data.csv
           └──all_dataset.csv
   ```

---

## Running the Notebooks

***Note: Please add the path to your Drive folder after mounting it to the colab in the First Cell of both files***
```
base_location = "/content/drive/MyDrive/[folder where you add Data]"
```

### Important: Two-Notebook Structure

Due to RAM limitations in Colab free tier, the project is split into two notebooks:

**Notebook 1: Data Collection through Hypothesis Testing**
- Sections: Data Collection → Preprocessing → EDA → Hypothesis Testing
- Time: ~10-15 minutes
- RAM: Fits within free tier limits

**Notebook 2: Machine Learning Models**
- Sections: ML Model Training → Performance Comparison → Deployment
- Time: ~20-30 minutes with T4 GPU
- RAM: Fits within free tier limits

Both notebooks can be downloaded from the GitHub repository:
**https://github.com/Akhil-Kambhatla/Akhil-kambhatla.github.io**

---

### Running Notebook 1: Data Collection through Hypothesis Testing

**Step 1: Open in Google Colab**

1. Download `Notebook_1_Data_Analysis.ipynb` from GitHub
2. Go to https://colab.research.google.com
3. Click "File" → "Upload notebook"
4. Select the notebook file


**Step 2: Run all code**
1. Change the first cell according to your drive ```base_location = "/content/drive/MyDrive/[folder where you add Data]"```
2. Click "Runtime" → "Run all"
3. The notebook will execute all sections in order
4. While running Google Drive mount cell
5. Click "Connect to Google Drive"
6. Allow permissions
7. Wait for "Mounted at /content/drive"
8. Expected time: ~10-15 minutes

**What You'll See:**
- Dataset statistics (6,717 restaurants, 3,077 cities)
- Brand price comparisons
- Geographic visualizations
- Correlation analysis
- 5 hypothesis test results

---

### Running Notebook 2: Machine Learning Models

**Step 1: Open in Google Colab**

1. Download `Notebook_2_Machine_Learning.ipynb` from GitHub
2. Upload to Colab (same process as Notebook 1)

**Step 2: Set Runtime with GPU**

1. Click "Runtime" → "Change runtime type"
2. Hardware accelerator: "GPU" → Select "T4 GPU"
3. **Important**: GPU is highly recommended for this notebook
4. Click "Save"

**Step 3: Run All Cells**

Same as Notebook 1 - run the Drive mount cell

1. Click "Runtime" → "Run all"
2. The notebook will:
   - Load pre-processed data
   - Generate BERT embeddings (~5 minutes)
   - Train 5 ML models (~15-20 minutes with GPU)
   - Create performance comparison

**What You'll See:**
- Progress bars for BERT embeddings
- Model training progress
- Performance metrics (MAE, RMSE, R²)
- Accuracy comparison table
- XGBoost inference example

**Expected Time:**
- With T4 GPU: ~20-30 minutes
- Without GPU: ~60-90 minutes (not recommended)

---

## Expected Results

### Notebook 1: Data Collection through Hypothesis Testing

**Section 4: EDA**
- Dataset: 6,717 restaurants, 3,077 cities, 1,265 menu items
- Total observations: 1.72 million
- Brand averages: Chipotle $11.44, Domino's $14.32, Papa John's $13.88
- 8 of top 10 expensive cities in California
- Interactive geographic heatmap

**Section 5: Hypothesis Testing**
- H1: Restaurant brand effect (F = 67,318, p < 0.001)
- H2: Item type effect (mains > sides > drinks)
- H3: Regional differences (West: $14.34, Midwest: $12.91)
- H4: Economic variables explain only 7.7% variance (R² = 0.077)
  - Income coefficient: 2.465e-06
  - Min wage coefficient: 0.160
  - Brand effects: Domino's +$5.89, Papa John's +$6.69 vs Chipotle
- H5: Paradoxical competition effect (+$0.042, R² = 0.019)

### Notebook 2: Machine Learning Models

**Model Performance:**
- Linear Regression: MAE $3.31, R² 0.796
- Ridge Regression: MAE $3.31, R² 0.796
- **XGBoost (Best)**: MAE $0.75, R² 0.986
- CatBoost: MAE $0.93, R² 0.979
- Neural Network: MAE $0.84, R² 0.981

**Key Insight**: ML models achieve 98.6% R² (XGBoost), which is 12.7× better than hypothesis testing's 7.7%. This proves that product identity (menu item + brand) matters far more than location economics.

---

## Data Sources

All data sources are publicly available:

**Restaurant Data** (provided in Google Drive):
- Chipotle: https://www.chipotle.com
- Domino's: https://www.dominos.com
- Papa John's: https://www.papajohns.com
- Collected: July 2024

**Minimum Wage** (auto-scraped by code):
- Department of Labor: https://www.dol.gov/agencies/whd/mw-consolidated

**ZIP Code Income** (provided in Google Drive):
- US Census Bureau: https://data.census.gov/map?q=Income+by+Zip+code+tabulation+area&layer=VT_2023_860_Z2_PY_D1
- American Community Survey (2022)

**USDA Rural-Urban Codes** (provided in Google Drive):
- USDA Economic Research Service: https://www.ers.usda.gov/data-products/rural-urban-continuum-codes/
- Rural-Urban Continuum Codes (2023)

**Regional Food Prices** (provided in Google Drive):
- Bureau of Labor Statistics - Average Retail Food Prices by Region:
  - West: https://www.bls.gov/regions/mid-atlantic/data/averageretailfoodandenergyprices_usandwest_table.htm
  - South: https://www.bls.gov/regions/mid-atlantic/data/averageretailfoodandenergyprices_usandsouth_table.htm
  - Midwest: https://www.bls.gov/regions/mid-atlantic/data/averageretailfoodandenergyprices_usandmidwest_table.htm
  - Northeast: https://www.bls.gov/regions/mid-atlantic/data/averageretailfoodandenergyprices_usandnortheast_table.htm

---

## Project Repository

GitHub: https://github.com/Akhil-Kambhatla/Akhil-kambhatla.github.io

Contents:
- Notebook 1: Data Collection through Hypothesis Testing
- Notebook 2: Machine Learning Models
- Data files (link to Google Drive)
- README documentation

---

## Citation

If you use this project for academic work:

```
Akhil Kambhatla, Mokshda Gangrade, Vyom Agarwal. (2025).
The Geography of Fast Food Pricing: Economic Determinants of Menu Prices Across America. 
GitHub: https://github.com/Akhil-Kambhatla/Akhil-kambhatla.github.io
```

---

## Contact

For questions or issues:
- GitHub Issues: https://github.com/Akhil-Kambhatla/Akhil-kambhatla.github.io/issues

---

**Last Updated**: December 2025
