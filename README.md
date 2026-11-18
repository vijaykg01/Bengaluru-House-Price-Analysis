# Bengaluru House Price Analysis 🏠

An end-to-end **Data Analytics and Business Intelligence project** exploring residential property listings in Bengaluru, Karnataka, using **Python, Pandas, Exploratory Data Analysis (EDA), and Power BI**.

The project covers data cleaning, feature engineering, statistical exploration, and an interactive Power BI dashboard to understand listing prices, property configurations, location-level listing patterns, area types, and availability categories.

---

## 📌 Project Overview

The objective is to transform raw Bengaluru housing data into a structured dataset and derive useful descriptive insights from property listings.

The workflow includes:

1. Data inspection and quality assessment.
2. Data cleaning and preprocessing with Python.
3. Feature engineering, including bedroom extraction and price per square foot.
4. Exploratory data analysis and visualization.
5. Interactive dashboard development in Power BI.
6. Documentation of findings, assumptions, and limitations.

> **Scope:** This is a descriptive analysis of property listing data. It is not a verified record of completed property transactions, a live availability feed, or a formal property valuation.

## 🎯 Project Objectives

- Clean and preprocess residential property data.
- Handle missing values, duplicate records, and inconsistent text formatting.
- Convert property area values into a consistent numerical format.
- Extract bedroom counts from the original property size field.
- Calculate price per square foot.
- Analyze listing prices across bedroom configurations.
- Identify locations with the highest listing counts.
- Explore relationships between property features and listed prices.
- Build an interactive Power BI dashboard with useful filters.
- Communicate findings through clear visualizations and project documentation.

## 🛠️ Tools and Technologies

| Tool / Library | Purpose |
|---|---|
| Python | Data cleaning and analysis |
| Pandas | Data manipulation, cleaning, and aggregation |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Seaborn | Statistical visualization |
| Jupyter Notebook | Reproducible analysis workflow |
| Power BI Desktop | Interactive dashboard and business intelligence |

## 📂 Repository Structure

```text
Bengaluru-House-Price-Analysis/
│
├── README.md
├── Project_Documentation.pdf
├── Price_Analysis_Dashboard.pbix
├── Bengaluru_House_Data_Clean.csv
│
└── notebooks/
    ├── Data_Cleansing.ipynb
    └── Exploratory_Data_Analysis.ipynb
```

Keep the actual filenames in GitHub consistent with this structure, or update the names above to match your repository. If you also publish the original raw CSV, add it to the structure and document its source and license.

## 📊 Dataset Description

The cleaned dataset contains **12,733 property records and 10 columns**, covering **1,293 distinct locations** in Bengaluru.

### Dataset Fields

| Column | Description |
|---|---|
| `area_type` | Property area classification |
| `availability` | Availability label recorded in the source listing |
| `location` | Property locality / location |
| `size` | Original property configuration label, such as `2 BHK` |
| `total_sqft` | Property area in square feet |
| `bath` | Number of bathrooms |
| `balcony` | Number of balconies |
| `price` | Listed property price; expressed in lakhs in the analysis |
| `bedrooms` | Numeric bedroom count extracted from `size` |
| `price_per_sqft` | Derived price per square foot |

The `bedrooms` and `price_per_sqft` fields are derived during data preparation. The price-per-square-foot calculation converts price from lakhs to rupees:

```python
price_per_sqft = (price * 100000) / total_sqft
```

### Data Quality Snapshot

| Check | Result |
|---|---:|
| Rows | 12,733 |
| Columns | 10 |
| Missing cells in cleaned CSV | 0 |
| Exact duplicate rows in cleaned CSV | 0 |
| Unique locations | 1,293 |
| Unique availability labels | 80 |

## 🧹 Data Cleaning and Preprocessing

The data-cleaning notebook documents the following workflow:

1. **Data inspection:** Loaded the dataset and reviewed its shape, columns, data types, descriptive statistics, and missing values.
2. **Duplicate handling:** Checked and removed duplicate records.
3. **Text standardization:** Trimmed leading and trailing spaces and standardized repeated whitespace in categorical fields.
4. **Bedroom extraction:** Extracted the numeric bedroom count from the original `size` column into `bedrooms`.
5. **Configuration standardization:** Standardized bedroom labels to the `BHK` format.
6. **Missing-value handling:** Removed records with missing location or bedroom information; filled missing bathroom and balcony values using their respective median values.
7. **Area conversion:** Converted supported area units into square feet. Area ranges were represented using their midpoint.
8. **Feature engineering:** Calculated `price_per_sqft` using the price and area fields.
9. **Validation:** Checked data types, missing values, and duplicates after transformation.
10. **Export:** Saved the prepared data as `Bengaluru_House_Data_Clean.csv`.

The original dataset contained **13,320 rows and 9 columns**; the final cleaned dataset contains **12,733 rows and 10 columns**.

## 🔍 Exploratory Data Analysis

The EDA notebook investigates the following business questions:

### 1. What does the property price distribution look like?

Used descriptive statistics and a distribution plot to examine the spread and skew of listed prices.

### 2. Which locations have the highest number of listings?

Ranked locations by listing count to identify the most represented areas in the dataset.

### 3. How do listings vary by bedroom configuration?

Compared the number of listings across BHK configurations and examined price distributions by bedroom count.

### 4. How are property size and listed price related?

Used a scatter plot to inspect the relationship between total square feet and listed price, including unusual observations.

### 5. How are numerical property attributes related?

Calculated correlations among price, price per square foot, total area, bedrooms, bathrooms, and balconies.

### EDA Visualizations

- Property price distribution
- Property counts by bedroom configuration
- Property price distribution by bedroom count
- Top locations by number of listings
- Property size versus listed price
- Correlation heatmap of numerical variables

## 📈 Key Findings

The following values are calculated from the **current cleaned CSV included with this project**.

### 1. Property Price and Area

| Metric | Result |
|---|---:|
| Median listed price | 73.0 lakhs |
| Mean listed price | 114.52 lakhs |
| Median property area | 1,282 sq. ft. |
| Median price per sq. ft. | ₹5,489.77 |

The mean listed price is higher than the median, indicating a right-skewed distribution in which higher-priced records influence the average.

### 2. Most Represented Locations

| Location | Number of Listings |
|---|---:|
| Whitefield | 523 |
| Sarjapur Road | 377 |
| Electronic City | 288 |
| Kanakpura Road | 242 |
| Thanisandra | 232 |

Whitefield has the highest listing count in the cleaned dataset.

### 3. Bedroom Configuration

| Configuration | Number of Listings |
|---|---:|
| 1 BHK | 638 |
| 2 BHK | 5,216 |
| 3 BHK | 4,642 |
| 4 BHK | 1,398 |
| 5 BHK | 350 |
| 6 BHK | 221 |

Two- and three-bedroom properties together account for approximately **77.4%** of the cleaned records.

### 4. Availability Labels

- **Ready To Move:** 10,137 listings (approximately 79.6%).
- **Other availability labels:** 2,596 listings (approximately 20.4%).

These are source dataset labels and should not be interpreted as confirmation of current real-time availability.

### 5. Area Type Distribution

| Area Type | Number of Listings |
|---|---:|
| Super built-up Area | 8,277 |
| Built-up Area | 2,396 |
| Plot Area | 1,973 |
| Carpet Area | 87 |

### 6. Correlation Analysis

Correlation values recalculated from the current cleaned CSV:

| Variable | Correlation with Price |
|---|---:|
| Price per square foot | 0.024 |
| Total area | 0.048 |
| Bathrooms | 0.451 |
| Bedrooms | 0.395 |
| Balconies | 0.124 |

The values above are raw Pearson correlations on the supplied cleaned dataset. Extreme observations and the underlying distribution can influence these statistics. Correlation does not establish causation.

> **Data note:** Earlier exploratory notebook commentary contains different correlation figures. This README reports values recalculated from the current cleaned CSV so that the published summary matches the dataset supplied with this project.

## 📊 Power BI Dashboard

The project includes an interactive Power BI report:

**File:** `Price_Analysis_Dashboard.pbix`

The report is designed as a single-page real estate intelligence dashboard and includes:

| Dashboard Component | Purpose |
|---|---|
| KPI cards | Summarize property count and price metrics |
| Location price chart | Compare aggregated listed price across locations |
| Area type donut chart | Show listing distribution by area type |
| BHK chart | Compare property counts by bedroom configuration |
| Scatter chart | Explore property area and price relationships |
| Location matrix | Compare listing count and price metrics by location |
| Availability Treemap | Show the distribution of availability labels |
| Slicers | Filter the dashboard interactively |

### Dashboard Filters

- **Area Type**
- **BHK**
- **Availability**

Use the slicers to explore how the dashboard changes across property categories and availability labels.

**Interpretation note:** An aggregated location price chart can be influenced by the number of listings in each location. For typical price comparisons, use median price and consider the number of records behind each location.

### Dashboard Preview

Add a screenshot of the final Power BI report to the repository, for example:

```text
images/
└── powerbi-dashboard.png
```

Then display it here:

```md
![Bengaluru Real Estate Intelligence Dashboard](images/powerbi-dashboard.png)
```

## ⚙️ How to Run the Project

### Prerequisites

- Python 3.x
- Jupyter Notebook
- Power BI Desktop (to open and interact with the `.pbix` report)

### 1. Clone the Repository

```bash
git clone <your-github-repository-url>
```

### 2. Navigate to the Project Folder

```bash
cd Bengaluru-House-Price-Analysis
```

### 3. Install Python Dependencies

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 4. Run the Data Cleaning Notebook

```bash
jupyter notebook
```

Open `Data_Cleansing.ipynb` and run the cells in sequence. Update the input CSV path in the notebook if your raw dataset is stored in a different location.

The notebook exports:

```text
Bengaluru_House_Data_Clean.csv
```

### 5. Run the EDA Notebook

Open `Exploratory_Data_Analysis.ipynb` and run the cells in order. Ensure the cleaned CSV is available at the path referenced in the notebook.

**Execution order:** Data Cleaning → Exploratory Data Analysis.

### 6. Open the Power BI Dashboard

Open `Price_Analysis_Dashboard.pbix` in Power BI Desktop. If the CSV has been moved, update the data source path in Power BI and refresh the report.

## 💡 Skills Demonstrated

- Data cleaning and preprocessing
- Missing-value and duplicate handling
- Text standardization and data type conversion
- Feature engineering
- Exploratory data analysis
- Descriptive statistics
- Group-based analysis
- Correlation analysis
- Data visualization
- Python and Pandas
- Power BI dashboard development
- Business interpretation and analytical communication

## ⚠️ Limitations

- The dataset represents property listings, not independently verified completed transactions.
- Availability labels are taken from the source data and do not confirm current availability.
- The cleaned dataset does not provide a historical time series suitable for measuring price appreciation.
- Rental income is not included; rental yield and investment ROI cannot be calculated.
- Extreme values are present in some numeric fields and can influence averages, correlations, and visual scales.
- Location comparisons should be considered alongside listing counts, as low-volume locations may have less stable summaries.
- The analysis is exploratory and should not be treated as a formal property valuation or investment recommendation.

## 🚀 Conclusion

This project demonstrates an end-to-end analytics workflow using Bengaluru residential property listing data. Python was used to clean and transform the data, exploratory analysis was used to investigate pricing and property characteristics, and Power BI was used to present the results in an interactive dashboard.

The analysis highlights the dominance of 2 BHK and 3 BHK listings, the high listing representation of Whitefield, and the distribution of property types and availability labels. It also demonstrates the importance of validating outliers and interpreting summary statistics carefully.

## 👤 Author

**Vijay K G**  
BBA Graduate | Aspiring Data Analyst

**Technical Skills:** Python | SQL | Excel | Power BI

---

## 📷 EDA Visual Gallery

The following images are the existing EDA screenshots from the project.

<img width="530" height="314" alt="Property analysis visualization 1" src="https://github.com/user-attachments/assets/c625d534-e26d-41d1-8ac7-c9b76e2202e6" />
<img width="518" height="349" alt="Property analysis visualization 2" src="https://github.com/user-attachments/assets/b04b1b83-bf80-4f96-ba0d-6ad2c4f11be0" />
<img width="510" height="335" alt="Property analysis visualization 3" src="https://github.com/user-attachments/assets/7081d188-8578-40a8-b794-fd0c1b4ddec0" />
<img width="514" height="399" alt="Property analysis visualization 4" src="https://github.com/user-attachments/assets/df17911b-f67f-4d97-a6ac-b1cab166a21d" />
<img width="458" height="490" alt="Property analysis visualization 5" src="https://github.com/user-attachments/assets/dbe5d218-aaff-4c25-af0a-d33d0b22ffd8" />
<img width="622" height="513" alt="Property analysis visualization 6" src="https://github.com/user-attachments/assets/3317cb6b-6230-49eb-8eaf-db6f88d31f7d" />
<img width="537" height="529" alt="Property analysis visualization 7" src="https://github.com/user-attachments/assets/4f384886-b9ec-4474-a960-2d98d4c54994" />

---


## 📄 Dataset Attribution

Before publishing, add the original dataset publisher, dataset title, source URL, and applicable license or attribution terms. Retain any attribution requirements associated with the original dataset.
