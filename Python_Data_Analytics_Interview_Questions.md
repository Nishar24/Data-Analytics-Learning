# Python & Data Analytics Interview Questions

> **Purpose:** Interview preparation for Python, Pandas, NumPy, Data Cleaning, Data Analysis, and basic Machine Learning.

---

## 1. Python Basics (Core Concepts)

### 1. What are Python's main data types?
**Answer:** `int`, `float`, `str`, `bool`, `list`, `tuple`, `set`, `dict`, `NoneType`.

### 2. What's the difference between a list and a tuple?
**Answer:** List is **mutable** (can be changed), while tuple is **immutable** (cannot be changed).

### 3. How is a set different from a list?
**Answer:** A set stores **unique values** and is unordered, while a list maintains order and can contain duplicates.

### 4. What's the difference between `is` and `==`?
**Answer:** `is` checks whether two variables refer to the **same object**; `==` checks whether their **values are equal**.

### 5. What is list comprehension?
**Answer:** A short way to create a list.
```python
[x**2 for x in range(5)]
```

### 6. How do you handle exceptions in Python?
**Answer:** Using `try`, `except`, `else`, and `finally`.
```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
finally:
    print("Done")
```

### 7. Explain shallow copy vs deep copy.
**Answer:** A shallow copy copies the outer object but nested objects may still be shared. A deep copy recursively copies nested objects too.
```python
import copy

shallow = copy.copy(data)
deep = copy.deepcopy(data)
```

### 8. What are `*args` and `**kwargs`?
**Answer:** They allow a function to accept a variable number of positional and keyword arguments.
```python
def test(*args, **kwargs):
    print(args)
    print(kwargs)
```

### 9. What are Python decorators?
**Answer:** Decorators are functions that modify or extend another function's behavior without changing its source code.

### 10. What are lambda functions?
**Answer:** Small anonymous functions, usually used for short operations.
```python
square = lambda x: x ** 2
```

### 11. What is the difference between mutable and immutable objects?
**Answer:** Mutable objects can be changed after creation (`list`, `dict`, `set`); immutable objects cannot (`int`, `float`, `str`, `tuple`).

### 12. What is the difference between `append()` and `extend()`?
**Answer:** `append()` adds one object; `extend()` adds each element from an iterable.
```python
a = [1, 2]
a.append([3, 4])   # [1, 2, [3, 4]]

b = [1, 2]
b.extend([3, 4])   # [1, 2, 3, 4]
```

### 13. What is the difference between `remove()`, `pop()`, and `del`?
**Answer:** `remove()` deletes by value, `pop()` deletes by index and returns the value, and `del` deletes an item/slice/variable.

### 14. What is a Python dictionary?
**Answer:** A mutable collection of key-value pairs.
```python
employee = {"name": "Nishar", "role": "Analyst"}
```

### 15. What is the difference between local and global variables?
**Answer:** A local variable exists inside a function; a global variable is defined outside functions and can be accessed more broadly.

### 16. What is a function in Python?
**Answer:** A reusable block of code designed to perform a specific task.

### 17. What is the difference between `return` and `print()`?
**Answer:** `print()` displays a value; `return` sends a value back from a function.

### 18. What is `None` in Python?
**Answer:** `None` represents the absence of a value.

### 19. What is the difference between `break`, `continue`, and `pass`?
**Answer:** `break` exits a loop, `continue` skips the current iteration, and `pass` does nothing and acts as a placeholder.

### 20. What is PEP 8?
**Answer:** PEP 8 is Python's official style guide for writing readable and consistent Python code.

---

# 2. Python for Data Analysis (Pandas, NumPy, etc.)

### 21. How do you read a CSV file in Python?
```python
import pandas as pd

df = pd.read_csv("file.csv")
```

### 22. How do you handle missing values in Pandas?
**Answer:** Common methods are:
```python
df.isna().sum()
df.dropna()
df.fillna(0)
df["sales"].fillna(df["sales"].mean())
```

### 23. What is the difference between `.loc[]` and `.iloc[]`?
**Answer:** `.loc[]` uses labels; `.iloc[]` uses integer positions.
```python
df.loc[0, "sales"]
df.iloc[0, 2]
```

### 24. How can you merge two datasets in Pandas?
```python
pd.merge(df1, df2, on="id", how="inner")
```

### 25. How do you remove duplicate records?
```python
df.drop_duplicates()
```

### 26. How do you calculate group-wise aggregations?
```python
df.groupby("category")["sales"].sum()
```

### 27. What is vectorization in NumPy and why is it faster?
**Answer:** Vectorization performs operations on entire arrays without explicit Python loops. NumPy uses optimized low-level implementations, making many numerical operations faster.

### 28. How can you apply a custom function to each row or column?
```python
df.apply(lambda x: x + 1)
```
For a specific column:
```python
df["sales"].apply(lambda x: x * 1.1)
```

### 29. How do you convert a categorical column into numeric values?
**Answer:**
```python
pd.get_dummies(df, columns=["category"])
```
For label encoding:
```python
from sklearn.preprocessing import LabelEncoder
```

### 30. What's the difference between `pivot_table()` and `groupby()`?
**Answer:** `groupby()` is mainly used for grouping and aggregation. `pivot_table()` creates spreadsheet-like multidimensional summaries.

### 31. What is a Pandas Series?
**Answer:** A one-dimensional labeled data structure.

### 32. What is a Pandas DataFrame?
**Answer:** A two-dimensional labeled table containing rows and columns.

### 33. How do you inspect a DataFrame quickly?
```python
df.head()
df.tail()
df.shape
df.columns
df.info()
df.describe()
```

### 34. How do you select a column from a DataFrame?
```python
df["sales"]
```

### 35. How do you filter rows in Pandas?
```python
df[df["sales"] > 1000]
```

### 36. How do you select multiple columns?
```python
df[["name", "sales", "country"]]
```

### 37. How do you rename columns?
```python
df.rename(columns={"old_name": "new_name"}, inplace=True)
```

### 38. How do you change a column's data type?
```python
df["sales"] = df["sales"].astype(float)
```

### 39. How do you find unique values?
```python
df["category"].unique()
```

### 40. How do you count unique values?
```python
df["category"].nunique()
```

### 41. How do you count occurrences of each category?
```python
df["category"].value_counts()
```

### 42. How do you sort a DataFrame?
```python
df.sort_values("sales", ascending=False)
```

### 43. How do you create a new column?
```python
df["profit"] = df["sales"] - df["cost"]
```

### 44. What is the difference between `map()`, `apply()`, and `applymap()`?
**Answer:** `map()` is commonly used element-by-element on a Series, `apply()` applies a function to a Series or along DataFrame rows/columns, and `DataFrame.map()` (formerly `applymap()` in older Pandas versions) applies element-wise to a DataFrame.

### 45. How do you concatenate DataFrames?
```python
pd.concat([df1, df2], axis=0)
pd.concat([df1, df2], axis=1)
```

### 46. What is the difference between `merge()` and `concat()`?
**Answer:** `merge()` combines datasets based on matching keys/columns; `concat()` stacks objects along rows or columns.

### 47. How do you export a DataFrame to Excel?
```python
df.to_excel("output.xlsx", index=False)
```

---

# 3. Data Cleaning, Analysis & Real-Use Cases

### 48. How do you identify and handle outliers?
**Answer:** Common methods are IQR, Z-score, box plots, and domain-specific rules.

**IQR rule:**
```python
Q1 = df["sales"].quantile(0.25)
Q3 = df["sales"].quantile(0.75)
IQR = Q3 - Q1

lower = Q1 - 1.5 * IQR
upper = Q3 + 1.5 * IQR

outliers = df[(df["sales"] < lower) | (df["sales"] > upper)]
```

### 49. How do you convert a date column to datetime?
```python
df["date"] = pd.to_datetime(df["date"])
```

### 50. How do you extract year or month?
```python
df["year"] = df["date"].dt.year
df["month"] = df["date"].dt.month
```

### 51. How can you find correlation between variables?
```python
df.corr(numeric_only=True)
```

### 52. How do you create columns based on conditions?
```python
import numpy as np

df["category"] = np.where(
    df["sales"] > 1000,
    "High",
    "Low"
)
```

### 53. How do you sort by multiple columns?
```python
df.sort_values(
    ["country", "sales"],
    ascending=[True, False]
)
```

### 54. How do you find top 5 products by sales?
```python
df.groupby("product")["sales"].sum().nlargest(5)
```

### 55. How do you calculate percentage contribution?
```python
df["pct"] = df["sales"] / df["sales"].sum() * 100
```

### 56. How do you save a cleaned DataFrame?
```python
df.to_csv("cleaned_data.csv", index=False)
```

### 57. How do you identify duplicate records?
```python
df.duplicated().sum()
```

### 58. How do you check missing values column-wise?
```python
df.isnull().sum()
```

### 59. How do you check the percentage of missing values?
```python
df.isnull().mean() * 100
```

### 60. How do you replace values in a DataFrame?
```python
df["status"] = df["status"].replace({
    "Pending": "Open"
})
```

### 61. How do you standardize text data?
```python
df["name"] = df["name"].str.strip().str.title()
```

### 62. How do you detect invalid or inconsistent data?
**Answer:** Check data types, missing values, duplicates, unexpected categories, impossible ranges, date errors, and business rules.

### 63. How would you clean a real-world dataset before analysis?
**Answer:** Understand the business requirement → inspect data → fix data types → handle missing values → remove/fix duplicates → standardize text → validate dates/ranges → investigate outliers → validate business rules → document changes.

### 64. How do you validate data quality before sharing a dashboard?
**Answer:** Check row counts, duplicates, missing values, data types, totals against the source, date ranges, filters, joins, calculated metrics, and sample records. Finally, reconcile key KPIs with the source system.

### 65. How do you investigate an unexpected drop in sales?
**Answer:** First validate the data and refresh. Then compare sales by date, product, region, channel, and customer segment. Check whether the drop is caused by missing data, a business event, seasonality, or a real performance issue.

---

# 4. Python for Data Analytics & Machine Learning

### 66. What are the steps in a machine learning workflow?
**Answer:** Problem definition → data collection → exploration → cleaning → feature engineering → train/test split → preprocessing → model training → evaluation → tuning → deployment/monitoring.

### 67. How do you split data into training and testing sets?
```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X, y,
    test_size=0.2,
    random_state=42
)
```

### 68. How do you evaluate regression models?
**Answer:** Common metrics are MAE, MSE, RMSE, and R².

### 69. How do you evaluate classification models?
**Answer:** Accuracy, precision, recall, F1-score, ROC-AUC, and confusion matrix.

### 70. What is feature scaling?
**Answer:** Scaling puts numerical features on comparable scales.

Common methods:
```python
from sklearn.preprocessing import StandardScaler, MinMaxScaler
```

### 71. What is the difference between supervised and unsupervised learning?
**Answer:** Supervised learning uses labeled data; unsupervised learning finds patterns in unlabeled data.

### 72. How can you visualize model performance?
**Answer:** Confusion matrix, ROC curve, precision-recall curve, residual plot, predicted-vs-actual plot, and learning curves.

### 73. How can Python be used for A/B testing?
**Answer:** Define the hypothesis and metric, collect control/treatment data, select an appropriate statistical test, calculate the p-value/confidence interval, and interpret the business impact.

Example:
```python
from scipy.stats import ttest_ind

stat, p_value = ttest_ind(group_a, group_b)
```

### 74. What libraries are used for data visualization?
**Answer:** Matplotlib, Seaborn, Plotly.

### 75. What's the difference between Series and DataFrame?
**Answer:** Series is 1D; DataFrame is 2D.

### 76. Explain OLS regression.
**Answer:** Ordinary Least Squares estimates regression coefficients by minimizing the sum of squared differences between actual and predicted values.

### 77. What is overfitting?
**Answer:** When a model performs very well on training data but poorly on unseen data.

### 78. What is underfitting?
**Answer:** When a model is too simple to capture important patterns and performs poorly even on training data.

### 79. What is cross-validation?
**Answer:** A technique that repeatedly splits the training data into training and validation parts to estimate model performance more reliably.

### 80. What is the difference between MAE and RMSE?
**Answer:** MAE is the average absolute error. RMSE is the square root of average squared error and penalizes larger errors more strongly.

---

# 5. Coding-Based Python Questions

## 81. Find all even numbers in a list
```python
[x for x in mylist if x % 2 == 0]
```

## 82. Count unique values in a column
```python
df["col"].nunique()
```

## 83. Reverse a string
```python
s[::-1]
```

## 84. Find top 3 customers by total spending
```python
df.groupby("customer")["sales"].sum().nlargest(3)
```

## 85. Replace missing values with mean
```python
df["col"] = df["col"].fillna(df["col"].mean())
```

## 86. Merge customer and orders datasets
```python
pd.merge(
    customers,
    orders,
    on="cust_id",
    how="inner"
)
```

## 87. Find correlation between numeric features
```python
df.corr(numeric_only=True)
```

## 88. Apply a discount
```python
df["discounted_price"] = df["price"] * 0.9
```

## 89. Find the largest number in a list
```python
max(mylist)
```

## 90. Find the second-largest unique number
```python
sorted(set(mylist))[-2]
```

## 91. Count frequency of each element
```python
from collections import Counter

Counter(mylist)
```

## 92. Remove duplicates from a list
```python
list(set(mylist))
```
> Use this only when original order does not matter. For order-preserving removal:
```python
list(dict.fromkeys(mylist))
```

## 93. Check whether a string is a palindrome
```python
s == s[::-1]
```

## 94. Find common elements between two lists
```python
list(set(a) & set(b))
```

## 95. Find rows where sales are above average
```python
df[df["sales"] > df["sales"].mean()]
```

## 96. Find the top-selling product
```python
df.groupby("product")["sales"].sum().idxmax()
```

## 97. Calculate total sales by region
```python
df.groupby("region")["sales"].sum()
```

## 98. Calculate average sales by category
```python
df.groupby("category")["sales"].mean()
```

## 99. Find customers who placed more than 5 orders
```python
order_count = df.groupby("customer")["order_id"].nunique()
order_count[order_count > 5]
```

## 100. Find the month with the highest sales
```python
monthly_sales = (
    df.groupby(df["date"].dt.to_period("M"))["sales"]
      .sum()
)

monthly_sales.idxmax()
```

---

# 6. High-Value Interview Questions for Data Analyst Roles

### 101. What is the difference between `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`, and `FULL OUTER JOIN`?
**Answer:** They differ in which unmatched rows they keep. `INNER` keeps matches only; `LEFT` keeps all rows from the left table; `RIGHT` keeps all rows from the right table; `FULL` keeps all rows from both.

### 102. What is data leakage in machine learning?
**Answer:** Data leakage occurs when information that would not be available at prediction time is accidentally used during model training, producing unrealistically good results.

### 103. Why should you split data before fitting preprocessing steps?
**Answer:** To avoid test-set information leaking into the training process. Fit preprocessing such as scaling/imputation on training data and apply it to test data.

### 104. What is multicollinearity?
**Answer:** When predictor variables are highly correlated with each other, making individual coefficient estimates harder to interpret in models such as linear regression.

### 105. What is the difference between correlation and causation?
**Answer:** Correlation means variables move together; causation means a change in one variable produces a change in another. Correlation alone does not prove causation.

### 106. What is a KPI?
**Answer:** A Key Performance Indicator is a measurable metric used to evaluate progress toward a business objective.

### 107. How do you choose the right visualization?
**Answer:** Match the chart to the question: line for trends, bar for category comparisons, scatter for relationships, histogram for distributions, and box plot for spread/outliers.

### 108. What makes a good dashboard?
**Answer:** Clear business purpose, relevant KPIs, simple layout, consistent definitions, useful filters, readable visuals, validated data, and actionable insights.

### 109. How do you explain technical analysis to a non-technical stakeholder?
**Answer:** Start with the business question, explain the key finding in simple language, quantify the impact, show only necessary evidence, and finish with the recommended action.

### 110. How do you handle a stakeholder who says your numbers are wrong?
**Answer:** Stay objective. Reproduce the metric, check source data and filters, verify calculations and joins, compare with an independent source, identify the discrepancy, and explain the resolution clearly.

---

# 7. Quick Revision Cheat Sheet

| Topic | Important Functions / Concepts |
|---|---|
| Python Types | `int`, `float`, `str`, `bool`, `list`, `tuple`, `set`, `dict` |
| Conditions | `if`, `elif`, `else` |
| Loops | `for`, `while`, `break`, `continue` |
| Functions | `def`, `return`, `*args`, `**kwargs`, lambda |
| Exceptions | `try`, `except`, `else`, `finally` |
| Pandas Read | `pd.read_csv()` |
| Inspection | `head()`, `info()`, `describe()`, `shape` |
| Missing Data | `isna()`, `fillna()`, `dropna()` |
| Duplicates | `duplicated()`, `drop_duplicates()` |
| Filtering | Boolean indexing, `loc`, `iloc` |
| Grouping | `groupby()`, `agg()` |
| Joining | `merge()` |
| Combining | `concat()` |
| Reshaping | `pivot_table()`, `melt()` |
| Sorting | `sort_values()` |
| Dates | `pd.to_datetime()`, `.dt.year`, `.dt.month` |
| NumPy | Arrays, vectorization, aggregation |
| Visualization | Matplotlib, Seaborn, Plotly |
| Statistics | Mean, median, std, correlation, IQR |
| ML | Train/test split, preprocessing, model, evaluation |
| Regression | MAE, RMSE, R² |
| Classification | Accuracy, Precision, Recall, F1, ROC-AUC |

---

# 8. Interview Answer Formula

For most technical interview questions, use this structure:

**1. Definition → 2. Simple explanation → 3. Example/code → 4. Business use case**

### Example: `groupby()`

**Definition:** `groupby()` groups rows based on one or more columns.

**Simple explanation:** Suppose we have sales data and want total sales for each region.

**Code:**
```python
df.groupby("region")["sales"].sum()
```

**Business use:** It can help management compare revenue across regions.

---

# 9. Most Important Topics to Prioritize

If you are preparing specifically for a **Data Analyst / MIS / Data Analytics interview**, prioritize these first:

1. Python basics
2. Pandas DataFrame operations
3. `loc` vs `iloc`
4. Filtering
5. `groupby()` + aggregation
6. `merge()` / joins
7. Missing values
8. Duplicate handling
9. Date/time operations
10. Sorting and ranking
11. `apply()`, `map()`, `lambda`
12. NumPy basics and vectorization
13. Outlier detection
14. Correlation
15. Data cleaning workflow
16. Real-world data validation
17. Matplotlib / Seaborn
18. SQL + Pandas comparison
19. Excel + Python comparison
20. Business-case questions
