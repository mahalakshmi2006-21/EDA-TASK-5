# 🏥 Exploratory Data Analysis on Healthcare Dataset

## 📌 Project Overview

This project performs **Exploratory Data Analysis (EDA)** on a Healthcare dataset using Python.

The analysis focuses on understanding the dataset structure, handling missing values, cleaning categorical data, converting date columns, creating a new feature for hospital stay duration, performing statistical analysis, and visualizing categorical data.

## 🎯 Objectives

* Load and inspect the healthcare dataset
* Understand the shape and columns of the dataset
* Check and handle missing values
* Clean categorical data
* Convert date columns into datetime format
* Extract year, month, and day from admission dates
* Calculate hospital stay duration
* Perform descriptive statistical analysis
* Analyze medical conditions by gender
* Visualize admission types using a bar chart

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Google Colab / Jupyter Notebook**

## 📊 Dataset

The project uses a healthcare dataset containing patient and hospital-related information.

Important columns used in the analysis include:

* `Patient_ID`
* `Age`
* `Gender`
* `Medical_Condition`
* `Medical_Code`
* `Admission_Type`
* `Date_of_Admission`
* `Discharge_Date`
* `Billing_Amount`

## 🔍 EDA Process

### 1. Data Loading

The dataset is loaded using Pandas:

```python
df = pd.read_csv("healthcare_data_for_task.csv")
```

### 2. Data Inspection

The dataset is inspected using:

```python
df.shape
df.columns
df.info()
df.head
```

This helps understand the dataset's structure, columns, and data types.

### 3. Missing Value Handling

Missing values are checked using:

```python
df.isnull().sum()
```

Missing values in `Medical_Code` are replaced with `"unknown"`:

```python
df['Medical_Code'] = df['Medical_Code'].fillna('unknown')
```

### 4. Data Cleaning

`Admission_Type` is cleaned by removing extra spaces and standardizing the capitalization:

```python
df['Admission_Type'] = (
    df['Admission_Type']
    .str.strip()
    .str.title()
)
```

### 5. Admission Type Analysis

Unique admission types and their frequencies are identified using:

```python
df['Admission_Type'].unique()
df['Admission_Type'].value_counts()
```

A bar chart is used to visualize the frequency:

```python
df['Admission_Type'].value_counts().plot(kind='bar')
```

### 6. Date Conversion

Admission and discharge dates are converted into datetime format:

```python
df['Date_of_Admission'] = pd.to_datetime(df['Date_of_Admission'])
df['Discharge_Date'] = pd.to_datetime(df['Discharge_Date'])
```

Year, month, and day are extracted from the admission date.

### 7. Feature Creation

A new column `Stay _Days` is created to calculate the number of days a patient stayed in the hospital:

```python
df['Stay _Days'] = (
    df['Discharge_Date'] - df['Date_of_Admission']
).dt.days
```

### 8. Statistical Analysis

Descriptive statistics are performed on `Billing_Amount`:

```python
df['Billing_Amount'].describe()
```

This provides values such as count, mean, standard deviation, minimum, maximum, and quartiles.

### 9. Categorical Analysis

A cross-tabulation is performed between medical condition and gender:

```python
pd.crosstab(
    df['Medical_Condition'],
    df['Gender']
)
```

This shows the frequency of different medical conditions across genders.

## 📈 Visualizations

The project includes a **bar chart** to visualize the frequency of different admission types.

The visualization makes it easier to understand the distribution of admission categories.

## 📁 Project Structure

```text
EDA-Healthcare-Task/
│
├── EDA_TASK_5.ipynb
├── healthcare_data_for_task.csv
└── README.md
```

## ✅ Conclusion

This EDA project demonstrates how Python and Pandas can be used to inspect, clean, transform, analyze, and visualize healthcare data.

The analysis provides an understanding of patient information, admission types, medical conditions, hospital stay duration, and billing amounts.
