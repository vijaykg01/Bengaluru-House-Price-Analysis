# Bengaluru House Price Analysis 🏠

## 📌 Project Overview

This project focuses on cleaning, analyzing, and exploring residential property data from Bengaluru, India, using Python. The objective is to understand property price distributions, identify locations with the highest number of listings, analyze pricing patterns across different bedroom configurations, and investigate relationships between property features and prices.

The project follows a structured data analysis workflow, from data cleaning and feature engineering to exploratory data analysis (EDA) and visualization.

## 🎯 Project Objectives

* Clean and preprocess raw housing data.
* Handle missing values, duplicate records, and inconsistent text formatting.
* Convert property sizes into a consistent numerical format.
* Extract the number of bedrooms from the property size column.
* Calculate property prices per square foot.
* Analyze property prices across different bedroom configurations.
* Identify locations with the highest number of property listings.
* Investigate correlations between property features and prices.
* Generate visualizations to communicate key findings.

## 🛠️ Technologies Used

* **Python** — Data analysis and processing
* **Pandas** — Data manipulation and cleaning
* **NumPy** — Numerical operations
* **Matplotlib** — Data visualization
* **Seaborn** — Statistical visualization
* **Jupyter Notebook** — Interactive analysis

## 📂 Project Structure

```text
Bengaluru-House-Price-Analysis/
│
├── Data Cleansing.ipynb
│   └── Data cleaning, preprocessing, and feature engineering
│
├── Exploratory Data Analysis (EDA)(3).ipynb
│   └── Exploratory analysis and visualizations
│
├── Bengaluru_House_Data.csv
│   └── Original housing dataset
│
├── Bengaluru_House_Data_Cleaned.csv
│   └── Cleaned dataset used for analysis
│
└── README.md
    └── Project documentation
```

*Note: The notebook filenames in your GitHub repository should match the names used in this README. The original and cleaned CSV files must also be included if you want others to reproduce the complete analysis.*

## 📊 Dataset Description

The dataset contains information about residential properties in Bengaluru.

### Key Columns

| Column           | Description                               |
| ---------------- | ----------------------------------------- |
| `area_type`      | Type of property area                     |
| `availability`   | Property availability status              |
| `location`       | Property location in Bengaluru            |
| `size`           | Original property size description        |
| `society`        | Housing society information               |
| `total_sqft`     | Total property area in square feet        |
| `bath`           | Number of bathrooms                       |
| `balcony`        | Number of balconies                       |
| `price`          | Property price in lakhs                   |
| `bedrooms`       | Extracted number of bedrooms              |
| `price_per_sqft` | Calculated property price per square foot |

The `bedrooms` and `price_per_sqft` columns are derived during data preprocessing.

## 🧹 Data Cleaning and Preprocessing

The raw dataset initially contained **13,320 rows and 9 columns**.

The following data-cleaning operations were performed:

1. **Duplicate Removal:** Identified and removed duplicate records.
2. **Text Standardization:** Removed leading and trailing spaces and standardized repeated whitespace in categorical columns.
3. **Missing Value Handling:** Removed records with missing location or bedroom information.
4. **Bedroom Extraction:** Extracted numerical bedroom counts from the original `size` column.
5. **Numerical Conversion:** Converted property area values into a numerical format.
6. **Area Range Handling:** Replaced area ranges with their average values where applicable.
7. **Missing Value Imputation:** Filled missing bathroom and balcony values using their respective median values.
8. **Feature Engineering:** Calculated price per square foot using property price and total area.
9. **Final Validation:** Checked the processed data and removed duplicate records again.
10. **Data Export:** Saved the cleaned dataset as `Bengaluru_House_Data_Cleaned.csv`.

After preprocessing, the dataset contained **12,733 rows and 10 columns**.

## 🔍 Exploratory Data Analysis

The cleaned dataset was analyzed to answer the following business questions:

### 1. What is the typical property price in Bengaluru?

Analyzed the mean, median, minimum, and maximum property prices to understand the overall price distribution and identify unusually expensive properties.

### 2. Which locations have the highest number of property listings?

Identified and visualized the top 15 locations based on the number of available property listings.

### 3. How do property prices vary by bedroom count?

Compared property prices across different bedroom configurations to understand pricing differences between smaller and larger properties.

### 4. How does property size relate to price?

Examined the relationship between total property area and price to identify general pricing patterns and potential outliers.

### 5. What relationships exist between numerical variables?

Calculated correlations between property area, bedrooms, bathrooms, balconies, price, and price per square foot.

### Visualizations

The analysis includes:

* Property price distribution
* Property counts by bedroom configuration
* Property prices by bedroom count
* Top 15 locations by number of listings
* Property size versus price
* Correlation heatmap of numerical variables

## 📈 Key Findings

The following findings were identified from the exploratory analysis.

### 1. Property Price Distribution

* **Median price:** ₹70 lakhs
* **Mean price:** ₹112.64 lakhs
* **Minimum recorded price:** ₹9 lakhs
* **Maximum recorded price:** ₹2,912 lakhs (₹29.12 crore)

The mean price is higher than the median, indicating a right-skewed price distribution influenced by expensive properties.

### 2. Locations with the Most Listings

The three locations with the highest number of listings were:

| Location        | Number of Listings |
| --------------- | -----------------: |
| Whitefield      |                520 |
| Sarjapur Road   |                373 |
| Electronic City |                280 |

Whitefield had the highest number of property listings in the analyzed dataset.

### 3. Property Prices by Bedroom Count

* Two-bedroom properties were the most common, with approximately 5,150 listings.
* Three-bedroom properties followed, with approximately 4,500 listings.
* Four-bedroom properties accounted for approximately 1,200 listings.
* Properties with five or more bedrooms were considerably less common.

The analysis also showed that median property prices generally increased with bedroom count, although the extent of the increase varied across configurations.

### 4. Property Size and Price

Property prices generally increased with total area, but the relationship was not consistent across all listings. Some properties had unusually large areas or high prices, indicating the presence of potential outliers.

### 5. Correlation Analysis

The following correlations with property price were observed:

| Variable              | Correlation with Price |
| --------------------- | ---------------------: |
| Price per square foot |                   0.69 |
| Total area            |                   0.59 |
| Bathrooms             |                   0.52 |
| Bedrooms              |                   0.48 |
| Balconies             |                   0.12 |

The number of bathrooms and bedrooms also showed a strong positive correlation of approximately **0.87**.

*Note: Correlation measures the strength and direction of a linear relationship. It does not establish causation.*

## ⚙️ How to Run This Project

### Prerequisites

Install Python and Jupyter Notebook, along with the required libraries.

### Step 1: Clone the Repository

```bash
git clone <your-github-repository-url>
```

### Step 2: Navigate to the Project Directory

```bash
cd Bengaluru-House-Price-Analysis
```

### Step 3: Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### Step 4: Add the Dataset

Place `Bengaluru_House_Data.csv` in the project directory.

Make sure the dataset filename matches the filename specified in the data-cleaning notebook.

### Step 5: Run the Data Cleaning Notebook

```bash
jupyter notebook
```

Open the data-cleaning notebook and execute the cells in order.

The notebook generates:

`Bengaluru_House_Data_Cleaned.csv`

### Step 6: Run the EDA Notebook

Open the exploratory data analysis notebook and execute its cells in order.

Ensure the cleaned CSV file is available in the location specified in the notebook.

**Execution order:** Data Cleaning → Exploratory Data Analysis.

## 💡 Skills Demonstrated

* Data cleaning and preprocessing
* Exploratory data analysis (EDA)
* Missing value and duplicate handling
* Data type conversion
* Feature engineering
* Descriptive statistics
* Group-based analysis
* Correlation analysis
* Data visualization
* Python and Pandas
* Translating data into actionable insights

## 🚀 Conclusion

This project demonstrates an end-to-end exploratory analysis workflow using Bengaluru residential property data. Data cleaning and feature engineering prepared the dataset for analysis, while statistical summaries and visualizations revealed property price distributions, listing concentrations across locations, bedroom-related pricing patterns, and relationships between numerical features.

The findings provide a clearer understanding of the housing dataset and demonstrate practical Python-based data analysis skills.

## 👤 Author

**Vijay K G**

Aspiring Data Analyst | Python | SQL | Excel | Power BI

<img width="530" height="314" alt="Screenshot 2026-10-11 220421" src="https://github.com/user-attachments/assets/c625d534-e26d-41d1-8ac7-c9b76e2202e6" />
<img width="518" height="349" alt="Screenshot 2026-10-11 220441" src="https://github.com/user-attachments/assets/b04b1b83-bf80-4f96-ba0d-6ad2c4f11be0" />
<img width="510" height="335" alt="Screenshot 2026-10-11 220453" src="https://github.com/user-attachments/assets/7081d188-8578-40a8-b794-fd0c1b4ddec0" />
<img width="514" height="399" alt="Screenshot 2026-10-11 220505" src="https://github.com/user-attachments/assets/df17911b-f67f-4d97-a6ac-b1cab166a21d" />
<img width="458" height="490" alt="Screenshot 2026-10-11 220536" src="https://github.com/user-attachments/assets/dbe5d218-aaff-4c25-af0a-d33d0b22ffd8" />
<img width="622" height="513" alt="Screenshot 2026-10-11 220550" src="https://github.com/user-attachments/assets/3317cb6b-6230-49eb-8eaf-db6f88d31f7d" />
<img width="537" height="529" alt="Screenshot 2026-10-11 220607" src="https://github.com/user-attachments/assets/4f384886-b9ec-4474-a960-2d98d4c54994" />

