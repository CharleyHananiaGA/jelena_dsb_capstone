⚓ DSB_capstone project

📊 Vignette Sales and Vessel Revenue Analysis (Capstone Project)

🎯 Project Overview (Data Question)
The primary question this project aims to answer is: How do monthly revenues and the volume of sold vignettes trend over the years, and in what ways do vessel characteristics (such as length) impact spending? The objective is to identify seasonal trends using historical data and perform an in-depth Exploratory Data Analysis (EDA) along with robust Feature Engineering to prepare the dataset for future predictive modeling.

📁 Data Source
The data originates from internal Excel logs tracking issued vessel vignettes over a 5-year period (Baza podataka 5 godina.xlsx). The dataset contains detailed transaction-level information, including unique vignette serial numbers, vessel names and registration IDs, physical attributes (length), vessel purpose, validity periods, the specific branch office that issued the document (Issued by), and financial metrics (prices with and without tax).

⚠️ Problem Statement
In its raw format, the dataset is unorganized and optimized for manual entry, containing empty rows, aggregate "Total" rows at the bottom of sheets, and inconsistent date formats. The core challenge is transforming raw, individual transaction records into structured, clean data through systematic cleaning, exploratory analysis, and advanced feature engineering. Without this preprocessing, insights and downstream machine learning algorithms cannot accurately interpret temporal trends or regional performance.

🔍 Potential Data Issues & Challenges
During the initial inspection, the following challenges were identified and addressed:

Missing Data: Certain rows lack critical information, such as vessel names or registration marks (e.g., 79 missing vessel IDs), which could skew the analysis if not properly handled.

Summary and Empty Rows: Manually entered summary rows at the bottom of spreadsheets introduce noise and artificially inflate statistical summaries.

Date Formats: Raw date fields start as plain text strings (object data types) and require formal conversion into pandas datetime objects for chronological tracking.

🛠️ Step-by-Step EDA & Feature Engineering Progress
The project notebook (JelenaVasic_capstone.ipynb) follows a rigorous, beginner-friendly pipeline divided into clear steps:

Step 1: Data Sourcing & Initial Loading – Imported the raw Excel file into a pandas DataFrame (df.read_excel) and inspected structural dimensions (26,764 rows and 12 initial columns) using df.head(10) and df.shape.

Step 2: Structural Audit & Descriptive Statistics – Evaluated column types using df.info() and calculated baseline statistics (mean, min, max, percentiles) for numerical features like vessel length and total price using df.describe().

Step 3: Data Cleansing & Missing Value Handling – Identified null values via df.isnull().sum() and filtered out unusable rows lacking critical identifiers to protect data integrity.

Step 4: Categorical Grouping & Business Insights – Analyzed transaction volumes and gross revenue generation across regional branch offices (such as Tivat, Zelenika, and Bar) using value_counts() and groupby().

Step 5: Datetime Normalization & Temporal Decomposition – Converted textual dates into formal datetime64 objects and extracted dedicated Year and Month features for year-over-year and seasonal analysis.

Step 6: Data Visualization – Generated visual reports using matplotlib and seaborn (including count plots for office distribution, distribution histograms for vessel lengths, and line charts for seasonal revenue trends across years).

Step 7: Advanced Feature Engineering – Enhanced the dataset with structural transformations:

Data Imputation: Filled missing vessel names with 'Unknown Vessel' and missing lengths with the median value.

Categorizations: Classified vignettes into price tiers (Low Price, Medium Price, High Price).

Time Series Metrics: Calculated time gaps (diff) between consecutive transactions to capture temporal momentum.

Dimensionality Reduction: Applied StandardScaler and Principal Component Analysis (PCA) to project numerical vessel and pricing attributes into principal components (PCA1, PCA2).

Step 8: Predictive Modeling (Introductory Preview) – Implemented a foundational Linear Regression model grouped by year and office location to project future vignette inventory demand.

💻 Technologies and Libraries Used
The project is built within a Jupyter Notebook / Python 3 environment using the following packages:

Pandas & NumPy - For data loading, cleaning, feature engineering, and aggregation.

Matplotlib & Seaborn - For visual exploratory analysis, discovering seasonal trends, and tracking data distributions.

Scikit-learn - Utilized for preprocessing (StandardScaler), feature transformation (PCA), and introductory predictive modeling (LinearRegression).
