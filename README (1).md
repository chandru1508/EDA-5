# Healthcare Data Analysis

## 📌 Project Overview

This project performs basic **data cleaning, preprocessing, and exploratory data analysis** on a healthcare dataset using Python.

The project uses **Pandas** for data manipulation and **Matplotlib/Seaborn** for data visualization. The healthcare dataset contains information such as admission type, medical condition, medical code, admission date, discharge date, billing amount, and patient age.

## 🛠️ Technologies Used

* Python
* Pandas
* Matplotlib
* Seaborn
* Google Colab
* CSV Dataset

## 📂 Dataset

The project reads the healthcare dataset from a CSV file:

```python
df = pd.read_csv("/content/healthcare_raw.csv")
```

The dataset is then inspected using:

```python
df.info()
df.head()
```

## 🔄 Data Preprocessing

The following preprocessing steps are performed:

### 1. Standardizing Admission Type

Admission type values are converted to lowercase:

```python
df["Admission_Type"] = df["Admission_Type"].str.lower()
```

### 2. Handling Missing Medical Codes

Missing values in the `Medical_Code` column are replaced with `"Undefind"`:

```python
df["Medical_Code"] = df["Medical_Code"].fillna("Undefind")
```

### 3. Checking Missing Values

Missing values are checked using:

```python
df.isnull()
```

### 4. Converting Date Columns

The admission and discharge dates are converted into datetime format:

```python
df["Admission_Date"] = df["Admission_Date"].astype("datetime64[ns]")
df["Discharge_Date"] = df["Discharge_Date"].astype("datetime64[ns]")
```

### 5. Calculating Hospital Stay

The number of days a patient stayed in the hospital is calculated using the admission and discharge dates:

```python
df["Hospital_stay_Days"] = (
    df["Discharge_Date"] - df["Admission_Date"]
).dt.days
```

## 📊 Exploratory Data Analysis

The project performs several analyses on the healthcare data.

### Admission Type Analysis

The number of patients for each admission type is calculated using:

```python
df["Admission_Type"].value_counts()
```

### Billing Amount Analysis

Statistical information about billing amounts is obtained using:

```python
df["Billing_Amount"].describe()
```

### Medical Condition Analysis

The number of occurrences of each medical condition is calculated using:

```python
df["Medical_Condition"].value_counts()
```

### Hospital Stay Analysis

Statistical information about hospital stay duration is obtained using:

```python
df["Hospital_stay_Days"].describe()
```

### Admission Type vs Medical Condition

A cross-tabulation is created to analyze the relationship between admission types and medical conditions:

```python
pd.crosstab(
    df["Admission_Type"],
    df["Medical_Condition"]
)
```

### Average Age by Medical Condition

The average patient age for each medical condition is calculated using:

```python
df.groupby("Medical_Condition")["Age"].mean()
```

## 🎯 Objectives

* Load healthcare data using Pandas.
* Inspect the structure and information of the dataset.
* Clean and preprocess healthcare data.
* Handle missing values.
* Convert date columns into the required format.
* Calculate hospital stay duration.
* Analyze admission types and medical conditions.
* Analyze billing amounts and hospital stay statistics.
* Calculate average age for different medical conditions.

## ▶️ How to Run

1. Open the notebook in **Google Colab** or Jupyter Notebook.
2. Upload the `healthcare_raw.csv` dataset.
3. Make sure the CSV file path matches the path used in the notebook.
4. Run the Python cells sequentially.

## 📁 Project Structure

```text
Healthcare-Data-Analysis/
│
├── Untitled7.ipynb
├── healthcare_raw.csv
└── README.md
```

## 📌 Conclusion

This project demonstrates the basic process of **healthcare data preprocessing and exploratory data analysis** using Python. It prepares the dataset for analysis by cleaning values, handling missing data, converting dates, calculating hospital stay duration, and examining important healthcare-related attributes.
