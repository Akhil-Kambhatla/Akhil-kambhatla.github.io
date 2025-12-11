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

**Platform:**
- Google Colab (required)
- Google Account
- Stable internet connection

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

**Total: 10 data files**

### Step 2: Download Files to Your Computer

1. Click the Google Drive link above
2. Select all files (click first file, hold Shift, click last file)
3. Right-click → Download
4. A ZIP file will be created and downloaded
5. Extract the ZIP file on your computer

### Step 3: Upload to Your Personal Google Drive

1. Open your Google Drive: https://drive.google.com

2. Create this folder structure:
   ```
   My Drive/
   └── 602_project/
       └── Data/
   ```

3. Upload all 10 files:
   - Navigate to `My Drive/602_project/Data/`
   - Click "+ New" → "File upload"
   - Select all 10 CSV files
   - Wait for upload to complete

4. Your final structure should be:
   ```
   My Drive/
   └── 602_project/
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
   ```

---

## Running the Notebooks

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

**Step 2: Set Runtime (Recommended)**

1. Click "Runtime" → "Change runtime type"
2. Hardware accelerator: "GPU" → Select "T4 GPU"
3. Click "Save"

**Step 3: Mount Google Drive**

1. Run Cell 10 (Google Drive mount cell)
2. Click "Connect to Google Drive"
3. Allow permissions
4. Wait for "Mounted at /content/drive"

**Step 4: Run All Cells**

1. Click "Runtime" → "Run all"
2. The notebook will execute all sections in order
3. Expected time: ~10-15 minutes

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

**Step 3: Mount Google Drive**

Same as Notebook 1 - run the Drive mount cell

**Step 4: Run All Cells**

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

## Troubleshooting

### Issue 1: FileNotFoundError

**Error**: `FileNotFoundError: [Errno 2] No such file or directory`

**Solution**:
1. Check that all 10 files are in `My Drive/602_project/Data/`
2. Verify file names match exactly (case-sensitive)
3. Re-mount Google Drive (run the mount cell again)
4. Check folder structure: `My Drive/602_project/Data/` (not `MyDrive` or other variations)

---

### Issue 2: ModuleNotFoundError

**Error**: `ModuleNotFoundError: No module named 'package_name'`

**Solution**:
Install the missing package in a code cell:

```python
!pip install package_name
```

Example for common packages:
```python
!pip install xgboost catboost transformers folium
```

Then restart runtime:
- Runtime → Restart runtime
- Re-run all cells

---

### Issue 3: Out of Memory / Session Crashed

**Error**: "Your session crashed after using all available RAM"

**Solution**:
This is why we split into 2 notebooks. If you still get this error:

1. Make sure you're running the correct notebook (1 or 2, not combined)
2. Use GPU runtime: Runtime → Change runtime type → GPU (T4)
3. Restart runtime and try again: Runtime → Restart runtime
4. Close other browser tabs to free memory

---

### Issue 4: Google Drive Won't Mount

**Error**: Can't connect to Google Drive

**Solution**:
1. Click the folder icon in left sidebar
2. Click "Mount Drive" button
3. Allow permissions when prompted
4. Wait for "Mounted at /content/drive" message
5. If still failing, restart runtime and try again

---

### Issue 5: Slow BERT Embedding Generation

**Issue**: Cell generating BERT embeddings taking very long

**Solution**:
1. Make sure you're using T4 GPU runtime
2. Check GPU is active: Runtime → View runtime type (should show "GPU T4")
3. If on CPU, expect 20-30 minutes (this is normal)
4. Progress bar will show you it's working

---

### Issue 6: Minimum Wage Data Not Loading

**Error**: Error when scraping minimum wage data

**Solution**:
1. Check internet connection
2. Retry the cell (sometimes temporary network issue)
3. The code scrapes from: https://www.dol.gov/agencies/whd/mw-consolidated
4. If website is down or changed structure, open a GitHub issue

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
