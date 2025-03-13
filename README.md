# Exploratory Data Analysis (EDA) on Netflix Dataset

This project performs **Exploratory Data Analysis (EDA)** on the Netflix dataset (`netflix_titles.csv`). The analysis covers **data cleaning, handling missing values, data visualization, and trend analysis** to extract insights about Netflix content.

## 📌 **Understanding the Code**
Let's walk through the code step by step as if we are teaching someone new to EDA.

### **1. Data Loading & Initial Exploration**
- **Read the Dataset**: We start by loading the `netflix_titles.csv` file using `pd.read_csv()`. 
- **Explore Data Structure**:
  - `df.info()` provides an overview of column names, data types, and missing values.
  - `df.head()` displays the first few rows to get a quick look at the dataset.
  - `df.describe()` gives summary statistics for numerical columns.
  - `df.columns` lists all column names.

### **2. Handling Missing Values**
- We fill missing values in `director`, `cast`, `country`, and `rating` with `'Unknown'` to avoid errors during analysis.

### **3. Handling Duplicates**
- We check for duplicate rows using `df.duplicated(keep=False)`. If duplicates exist, they are printed for further inspection.

### **4. Converting `date_added` Column**
- Since `date_added` is a string, we:
  - Remove extra spaces using `str.strip()`.
  - Convert it into a proper `datetime` format using `pd.to_datetime()`.

### **5. Converting `duration` Column**
- The `duration` column contains two formats:
  - Movies: Duration in minutes (e.g., "90 min").
  - TV Shows: Number of seasons (e.g., "2 Seasons").
- We extract numeric values for both using custom functions and convert `duration` to numeric type.

### **6. Data Visualization**
- **Boxplots**:
  - Movie durations (in minutes).
  - TV Show durations (in seasons).
- **Histograms**:
  - Distribution of `release_year`.
  - Movie duration distribution.
  - TV show duration distribution.

### **7. Outlier Detection & Removal**
- We use the **Interquartile Range (IQR)** method to detect and remove outliers from the `duration` column.
- A **boxplot before and after outlier removal** is used to visualize the effect.

### **8. Finding Mode for All Columns**
- We compute the **most frequently occurring value** (mode) for each column using `df.mode()`.
- This helps us understand the dominant trends in categorical and numerical data.

### **9. Analyzing Genre Distribution by Country and Type**
- The `listed_in` column contains multiple genres per row. We:
  - Split the column into separate rows.
  - Group data by `country`, `type` (Movie/TV Show), and `listed_in` (genre).
  - Count occurrences to find the most common genre-type combinations across different countries.

### **10. Analyzing Genre Popularity**
- We use `Counter` to **count occurrences of each genre**.
- Convert the genre counts into a **DataFrame** and sort them.
- **Plot a bar chart** of the **top 10 most popular genres**.

### **11. Pairplot for Numerical Columns**
- We use **Seaborn’s `pairplot()`** to create scatter plots for all numerical column pairs.
- This helps us identify **correlations, trends, and potential outliers**.

### **12. Distribution of Ratings by Content Type**
- **Seaborn’s `countplot()`** is used to visualize different **ratings**.
- The `hue='type'` parameter differentiates **Movies and TV Shows**.
- We rotate x-axis labels for better readability.

### **13. Genre Trends Over Time**
- **Ensure `release_year` is Numeric** using `pd.to_numeric()`.
- **Explode `listed_in` Column** for multi-genre entries.
- **Count Plot**: Shows the top genres over time.
- **Heatmap**: Displays genre frequency across release years.
- **Stacked Bar Chart**: Highlights genre trends across decades.



