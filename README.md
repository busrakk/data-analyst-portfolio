
# 🦠 COVID-19 Data Analysis Project

This project focuses on analyzing global COVID-19 data to understand the spread, mortality, and recovery patterns through data preprocessing, statistical analysis, and visualization.

---

## 📁 Dataset

- **File**: `covid_19_data.csv`
- **Records**: 306,429 rows  
- **Columns**:
  - `SNo`: Serial number
  - `ObservationDate`: Date of the record
  - `Province/State`: Specific region or state
  - `Country/Region`: Country name
  - `Last Update`: Last updated time
  - `Confirmed`: Number of confirmed COVID-19 cases
  - `Deaths`: Number of deaths
  - `Recovered`: Number of recoveries

---

## 🎯 Objectives

- Load and inspect the COVID-19 dataset
- Handle missing values and clean the data
- Perform exploratory data analysis (EDA)
- Visualize key statistics (confirmed cases, deaths, recoveries, mortality rate)
- Generate insights from the dataset

---

## 🛠️ Technologies Used

- `Pandas` - for data manipulation
- `NumPy` - for numerical operations
- `Matplotlib` & `Seaborn` - for data visualization
- `Warnings` - to suppress warnings during development

---

## 🔍 1. Data Loading and Initial Inspection

- Loaded the dataset using `pandas.read_csv()`
- Checked column data types with `.info()`
- Identified missing values using `.isnull().sum()`
- Previewed unique values in key categorical columns

#### Summary:

- `Province/State` contains ~78,000 missing values
- Dataset contains both numerical and string-based fields
- Some numerical columns contain negative values, indicating possible anomalies

---

## 🧹 2. Data Cleaning

### 🧮 Numerical Columns:
- Columns: `Confirmed`, `Deaths`, `Recovered`
- Strategy: Missing values filled with **mean values** of respective columns

### 🔤 Categorical Columns:
- Columns: `Province/State`, `Country/Region`, `Last Update`, etc.
- Strategy: Missing values filled with **"Unknown"**

```python
# Numeric fill
data[numeric_columns] = data[numeric_columns].apply(lambda x: x.fillna(x.mean()))

# Categorical fill
data[non_numeric_columns] = data[non_numeric_columns].apply(lambda x: x.fillna('Unknown'))
```

✅ Post-cleaning check confirmed **no missing values remain**.

---

## 📊 3. Exploratory Data Analysis (EDA)

### 🔢 Unique Value Counts

- `Country/Region`: 229 unique entries  
- `Province/State`: 736 entries  
- `ObservationDate`: 494 dates  

### 📈 Distribution of Numerical Columns

- Histograms for `Confirmed`, `Deaths`, and `Recovered` showed **high skewness** due to extreme values.

```python
sns.histplot(data['Confirmed'], kde=True)
```

### 🧮 Correlation Matrix

```python
correlation_matrix = data[['Confirmed', 'Deaths', 'Recovered']].corr()
sns.heatmap(correlation_matrix, annot=True, cmap="coolwarm")
```

**Findings:**

- Strong positive correlation between:
  - `Confirmed` & `Deaths` = 0.94  
  - `Confirmed` & `Recovered` = 0.83  

---

## 📈 4. Statistical Visualizations

### 4.1 Total Numbers Overview

- Bar chart of total counts:
  - `Confirmed`: ~26.3 Billion
  - `Deaths`: ~624 Million
  - `Recovered`: ~15.4 Billion

```python
sns.barplot(x=['Confirmed', 'Deaths', 'Recovered'], 
            y=[data['Confirmed'].sum(), data['Deaths'].sum(), data['Recovered'].sum()])
```

### 4.2 Mortality Rate Calculation & Distribution

```python
data['Mortality Rate'] = (data['Deaths'] / data['Confirmed']) * 100
sns.histplot(data['Mortality Rate'], kde=True, color='red')
```

- Some mortality rates exceeded 100% or dropped below 0%, indicating **invalid or extreme records** — may require filtering for modeling.

---

## 📌 Insights & Observations

- Countries with the most records: **US, Russia, Japan, China, India**
- `Province/State = Unknown` was common in data from aggregated country-level reporting
- Mortality rate distribution showed **heavy tails** and outliers
- High correlation between `Confirmed` and `Deaths` suggests severe outbreaks in some countries

---

## 🧭 Next Steps

- Convert date columns to `datetime` format
- Create time-series visualizations for key countries
- Group data by `Country/Region` and `Date` to observe growth trends
- Apply forecasting models such as Prophet or ARIMA
- Clean outliers for more accurate insights

---

## 📂 Project Structure

```
covid-analysis/
│
├── covid_19_data.csv
├── covid_analysis.ipynb
├── README.md
└── outputs/
    ├── confirmed_distribution.png
    ├── deaths_distribution.png
    ├── recovered_distribution.png
    ├── correlation_matrix.png
    └── mortality_rate_distribution.png
```

---
