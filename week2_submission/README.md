# Automotive Sales Data Analysis and Price Prediction

## Project Information

- **Organization:** WeIntern Pvt. Ltd.
- **Domain:** Data Science
- **Assignment:** Week 2 Internship Assignment
- **Project title:** Automotive Sales Data Analysis and Price Prediction
- **Objective:** Clean and preprocess automotive sales data, explore its patterns and relationships, and build and evaluate regression models to predict a sales-related numerical target.

## 1. Project Overview

This project is based on the Week 2 Data Science assignment, which covers three tasks:

1. **Data Cleaning Project** — identify and handle missing values, duplicate records, inconsistent formatting, data types, and outliers.
2. **Exploratory Data Analysis (EDA)** — summarize the dataset with statistics and visualizations to explore distributions, correlations, category-level differences, and time-based trends.
3. **Sales Prediction Model** — train and compare regression models, evaluate their predictions, and tune a model's hyperparameters.

The implementation uses an automotive sales dataset. It cleans the data, generates EDA summaries and charts, and compares Linear Regression with Random Forest Regression.

## 2. Dataset Description

The notebook loads the raw CSV file from:

```text
content/raw/raw_automotive_sales_data.csv
```

The dataset includes automotive sales and vehicle information such as:

- `original_mrp_inr` — original listed price in Indian rupees.
- `odometer_reading` — vehicle odometer reading.
- `sale_date` — date of sale.
- `powertrain_fuel` — fuel or powertrain category.
- `sales_region` — sales region or hub.
- `buyer_category` — buyer category.
- `final_selling_price` — final selling price.

The notebook cleans currency and odometer values, parses mixed-format sale dates, standardizes category labels, and handles missing values and duplicate rows.

**Note:** The dataset CSV is not included in this README. Check the actual CSV and notebook output for the final row count, column count, and any additional fields.

## 3. Tools and Libraries Used

- **Python** — main programming language.
- **Jupyter Notebook** — writing and running the analysis.
- **pandas** — data loading, cleaning, transformation, grouping, and summaries.
- **NumPy** — numerical processing and IQR-based outlier capping.
- **Matplotlib** — charts and plots.
- **Seaborn** — statistical visualizations and correlation heatmaps.
- **re** — standardizing column names and cleaning text-formatted numeric values.
- **scikit-learn** — train/test splitting, regression models, evaluation metrics, and hyperparameter tuning.

## 4. Key Steps Performed

### Task 1: Data Cleaning

1. Load the raw CSV using pandas and inspect the data.
2. Record the initial number of rows and columns, missing values, and duplicate rows.
3. Remove duplicate records.
4. Standardize column names to lowercase `snake_case`.
5. Clean currency values in `original_mrp_inr`.
6. Convert `odometer_reading` to numeric values.
7. Parse mixed-format values in `sale_date`.
8. Standardize fuel/powertrain and sales-region labels.
9. Remove records where `final_selling_price` is missing.
10. Fill missing buyer categories and sales regions; impute selected numerical fields with their median.
11. Use the IQR method to cap outliers in `odometer_reading` and `final_selling_price`.
12. Validate the cleaned data and prepare a raw-versus-cleaned quality comparison.

### Task 2: Exploratory Data Analysis (EDA)

The notebook performs descriptive and visual analysis, including:

- Numerical and categorical descriptive statistics.
- Histograms with KDE curves.
- A categorical count plot.
- A numerical correlation heatmap.
- Box plots for distributions and outlier inspection.
- Scatter plots to examine relationships between numerical variables.
- Monthly trend analysis when a date column is available.
- Grouped summaries using mean, median, and count.

### Task 3: Regression Modelling

1. Select a numerical target column.
2. Extract month and year from date-related columns where possible, then remove raw date columns.
3. Convert categorical features using one-hot encoding.
4. Split the data into 80% training and 20% testing sets.
5. Train a Linear Regression baseline model.
6. Train a Random Forest Regressor.
7. Compare the models using MAE, RMSE, and R².
8. Visualize Random Forest feature importance.
9. Plot actual versus predicted values for the model selected by test-set R².
10. Tune Random Forest hyperparameters with `RandomizedSearchCV` and 3-fold cross-validation.

## 5. Major Findings

Run `notebook/tasks.ipynb` to generate the dataset-specific findings. The notebook is set up to report:

- Data-quality changes between the raw and cleaned datasets.
- Distributions, category counts, correlations, and grouped or time-based patterns.
- A comparison of Linear Regression and Random Forest using MAE, RMSE, and R².
- The top 10 Random Forest feature-importance values.
- Actual-versus-predicted values for the selected model.
- The best hyperparameters and evaluation metrics for the tuned Random Forest.

The final numerical findings are not included here because the dataset outputs and model metrics were not available to verify when this README was prepared. After running the notebook, add the actual results below.

- **Final cleaned dataset size:** [Add result]
- **Best-performing model:** [Add result]
- **MAE:** [Add result]
- **RMSE:** [Add result]
- **R²:** [Add result]
- **Most important features:** [Add top features]
- **Key EDA insights:** [Add at least three insights supported by the charts and summaries]

**Target-column note:** The notebook selects `sales` if that column exists; otherwise, it uses the last numerical column. Confirm that this is the intended target for your dataset before interpreting the model as a sales prediction model.

## 6. Folder Structure

The project directory shown for this submission is organized as follows:

```text
week2_submission/
├── content/
│   ├── raw/
│   │   └── raw_automotive_sales_data.csv
│   └── processed/
│       └── cleaned_automotive_sales_data.csv
├── exports/
│   └── (exported charts, reports, or submission files)
├── notebook/
│   └── tasks.ipynb
├── .venv/
│   └── (local Python virtual environment)
└── README.md
```

The raw and processed CSV paths above are the paths expected for the project. Ensure the `content/raw/` and `content/processed/` folders exist and that the raw dataset is in the expected location before running the notebook.

## 7. Execution Instructions

### Prerequisites

- Python 3.9 or newer recommended
- Jupyter Notebook
- The raw automotive sales CSV at the path listed above

### Step 1: Open a terminal in the project root

```bash
cd week2_submission
```

### Step 2: Create and activate a virtual environment (recommended)

**Windows PowerShell:**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**Windows Command Prompt:**

```bat
python -m venv .venv
.venv\Scripts\activate.bat
```

### Step 3: Install the required libraries

```bash
python -m pip install --upgrade pip
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

### Step 4: Check the data folders

Place the source dataset here:

```text
content/raw/raw_automotive_sales_data.csv
```

Ensure this output folder exists:

```text
content/processed/
```

### Step 5: Run the notebook

From the project root, start Jupyter:

```bash
jupyter notebook
```

Open `notebook/tasks.ipynb` and run the cells in order from top to bottom. The first cells install packages in the notebook environment; installing dependencies in the terminal beforehand is also supported.

### Expected outputs

- Cleaned dataset: `content/processed/cleaned_automotive_sales_data.csv`
- Raw-versus-cleaned data-quality comparison table.
- EDA charts and grouped summary tables.
- Regression model comparison table.
- Random Forest feature-importance chart.
- Actual-versus-predicted plot.
- Tuned Random Forest parameters and evaluation metrics.

## 8. Limitations and Notes

- The analysis and model results depend on the dataset provided.
- The model's target column should be checked before reporting conclusions.
- IQR capping changes extreme values; consider the impact of this step when interpreting the data.
- The current workflow uses a random 80/20 split. For genuine future forecasting with time-dependent data, a chronological split may be more appropriate.
- The notebook's output directory must exist before saving the cleaned CSV.
- Export a PDF of the completed notebook if required by the Week 2 assignment handbook.

## 9. Author Details

- **Author name:** Vedant Dilip Gadade
- **Internship organization:** WeIntern Pvt. Ltd.
- **Domain:** Data Science
- **Assignment:** Week 2

Replace the author placeholder with your details before submission.
