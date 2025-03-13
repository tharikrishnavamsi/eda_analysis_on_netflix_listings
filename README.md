# eda_analysis_on_netflix_listings

this project performs **exploratory data analysis (eda)** on the netflix dataset (`netflix_titles.csv`). the analysis covers **data cleaning, handling missing values, data visualization, and trend analysis** to extract insights about netflix content.

## **understanding the code**
let's walk through the code step by step.

- **read the dataset**: we start by loading the `netflix_titles.csv` file using `pd.read_csv()`. 
- **explore data structure**:
  - `df.info()` provides an overview of column names, data types, and missing values.
  - `df.head()` displays the first few rows to get a quick look at the dataset.
  - `df.describe()` gives summary statistics for numerical columns.
  - `df.columns` lists all column names.

### **handling missing values**
- we fill missing values in `director`, `cast`, `country`, and `rating` with `'Unknown'` to avoid errors during analysis.

### **handling duplicates**
- we check for duplicate rows using `df.duplicated(keep=False)`. if duplicates exist, they are printed for further inspection.

### **converting `date_added` column**
- since `date_added` is a string, we:
  - remove extra spaces using `str.strip()`.
  - convert it into a proper `datetime` format using `pd.to_datetime()`.

### **converting `duration` column**
- the `duration` column contains two formats:
  - movies: duration in minutes (e.g., "90 min").
  - tv shows: number of seasons (e.g., "2 seasons").
- we extract numeric values for both using custom functions and convert `duration` to numeric type.

### **Data Visualization**
- **boxplots**:
  - movie durations (in minutes).
  - tv show durations (in seasons).
- **histograms**:
  - distribution of `release_year`.
  - movie duration distribution.
  - tv show duration distribution.

### **outlier detection & removal**
- we use the **interquartile range (iqr)** method to detect and remove outliers from the `duration` column.
- a **boxplot before and after outlier removal** is used to visualize the effect.

### **finding mode for all columns**
- we compute the **most frequently occurring value** (mode) for each column using `df.mode()`.
- this helps us understand the dominant trends in categorical and numerical data.

### **analyzing genre distribution by country and type**
- the `listed_in` column contains multiple genres per row. We:
  - split the column into separate rows.
  - group data by `country`, `type` (Movie/TV Show), and `listed_in` (genre).
  - count occurrences to find the most common genre-type combinations across different countries.

### **analyzing genre popularity**
- we use `counter` to **count occurrences of each genre**.
- convert the genre counts into a **DataFrame** and sort them.
- **plot a bar chart** of the **top 10 most popular genres**.

### **pairplot for numerical columns**
- we use **seaborn’s `pairplot()`** to create scatter plots for all numerical column pairs.
- this helps us identify **correlations, trends, and potential outliers**.

### **distribution of ratings by content type**
- **seaborn’s `countplot()`** is used to visualize different **ratings**.
- the `hue='type'` parameter differentiates **Movies and TV Shows**.
- we rotate x-axis labels for better readability.

### **genre trends over time**
- **ensure `release_year` is numeric** using `pd.to_numeric()`.
- **explode `listed_in` column** for multi-genre entries.
- **count plot**: shows the top genres over time.
- **heatmap**: displays genre frequency across release years.
- **stacked bar chart**: highlights genre trends across decades.



