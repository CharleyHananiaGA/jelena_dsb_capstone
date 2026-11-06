  # ⚓ dsb_capstone project

## 📊 Vignette Sales and Vessel Revenue Analysis (Capstone Project)

---

### 🎯 Project Overview (Data Question)
The primary question this project aims to answer is: **How do monthly revenues and the volume of sold vignettes trend over the years, and in what ways do vessel characteristics (such as length) impact spending?** The objective is to identify seasonal trends using historical data and prepare a clean dataset that machine learning models can utilize to forecast future revenues and optimize supply logistics (vignette inventory).

---

### 📁 Data Source
The data originates from internal Excel logs tracking issued vessel vignettes over a 5-year period (`Baza podataka 5 godina.xlsx`). The dataset contains detailed transaction-level information, including unique vignette serial numbers, vessel names and registration IDs, physical attributes (length), vessel purpose, validity periods, the specific branch office that issued the document, and financial metrics (prices with and without tax).

---

### ⚠️ Problem Statement
In its raw format, the dataset is unorganized and optimized for manual entry, containing empty rows, aggregate "Total" rows at the bottom of sheets, and inconsistent date formats. **The core challenge is transforming raw, individual transaction records into structured monthly aggregates grouped by branch offices.** Without this data cleaning and transformation, machine learning algorithms cannot accurately predict monthly revenues or effectively optimize vignette inventory for the year.

---

### 🔍 Potential Data Issues & Challenges
During the initial analysis, the following challenges were identified:
* **Missing Data:** Certain rows lack critical information, such as the issuing branch office (`Izdata od`), vessel registration mark, or vignette duration, which could skew the analysis if not handled properly.
* **SettingWithCopyWarning:** A technical Python warning occurs when extracting new features from the date columns, requiring precise indexing to guarantee that dataframe modifications are correctly applied.
* **Summary and Empty Rows:** Manually entered "total" summary rows within the Excel sheets introduce noise and artificially inflate data distributions in statistical summaries like `df.describe()`.

---

### 🛠️ Step-by-Step EDA Progress (What Has Been Done So Far)
During the Exploratory Data Analysis (EDA) phase, the following data preparation steps have been successfully completed:

* **Loading and Initial Inspection:** The data was imported into a Pandas DataFrame. Using `df.head(10)`, `df.shape`, and `df.info()`, the initial dataset size was determined to be 26,764 rows and 14 columns, along with their respective data types.
* **Missing Value Detection:** Running `df.isnull().sum()` successfully identified and located the exact count of missing values per column (e.g., 79 missing vessel registration IDs).
* **Dataset Cleaning:** Unusable rows lacking crucial information—such as the issuing branch office or price—were filtered out, preventing empty data records from corrupting future machine learning models.
* **Date Transformation:** The textual column 'Važi od' (Valid from) was converted into a datetime format (`pd.to_datetime`), allowing for the successful extraction of separate **Year** and **Month** features.
* **Data Aggregation:** The dataset was grouped (`groupby`) by branch office, year, and month. Total revenue, total vignettes issued, and the average vessel length were computed for each monthly interval.
* **Exporting Cleaned Data:** The transformed and aggregated dataset (consisting of 1,667 cleaned monthly records) was exported into a brand new, tidy Excel file (`vignette_inventory_and_revenue.xlsx`), omitting redundant index columns.

---

### 📈 Data Visualization (Plotting Trends)
To unlock deeper insights from our cleaned monthly records, visualization scripts were implemented to analyze performance metrics across different dimensions:
* **Yearly Trends per Office:** Implemented simplified plotting scripts utilizing Pandas pivot tables to map long-term seasonal and yearly performance for each unique branch office.
* **Quarterly Breakdowns:** Transformed monthly intervals into custom quarterly timeframes (Q1–Q4 concatenated with years, e.g., `2025-Q1`) to monitor mid-term volume adjustments and logistical spikes per office.
* **Annual Filtering (2025 Deep Dive):** Built conditional filtering blocks to isolate data from individual target years, such as 2025, mapping monthly fluctuations from January through December across multiple offices on a standardized x-axis scale.

---

### 💻 Technologies and Libraries Used
The project is built within a **Jupyter Notebook / Python 3** environment using the following packages:
* **Pandas & NumPy** - For data loading, cleaning, feature engineering, and aggregation.
* **Matplotlib & Seaborn** - For visual exploratory analysis, discovering seasonal trends, and tracking data distributions.
* **Scikit-learn** - Imported and prepared for the upcoming machine learning phase (utilizing models like *Logistic Regression*, *K-Neighbors Classifier*, and evaluation tools like *train_test_split* and *cross_val_score*).


