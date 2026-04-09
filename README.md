# 📈 Rossmann Store Sales Forecasting

This repository contains my Python project for exploring Rossmann store sales data and building regression models to forecast future sales. The project combines **data cleaning**, **exploratory data analysis**, **feature investigation**, and **linear regression modelling** to understand the key drivers of store sales and predict sales for July 2015.

---

## 📌 Introduction

This project focuses on forecasting Rossmann store sales using Python and machine learning.

Using historical store-level sales data, I explored how sales change across **years**, **months**, **days of the week**, **promotions**, **customers**, and **holiday effects**. After cleaning the dataset and creating a subset of the **top 200 stores**, I built and compared several regression models to identify which variables best predict sales.

This project demonstrates practical skills in:

- data cleaning and preprocessing
- exploratory data analysis
- feature selection
- correlation analysis
- linear regression modelling
- model comparison
- sales forecasting

---

## 💡 Motivation

Sales forecasting is an important business task because it helps retailers plan inventory, staffing, promotions, and operations more effectively.

The goal of this project is to understand which variables are most strongly associated with Rossmann store sales and to use those insights to generate a simple predictive model for future sales performance.

The project explores questions such as:

- How do sales vary by year?
- How do sales change across days of the week?
- How strongly are customer counts linked to sales?
- Do promotions improve sales?
- What is the effect of school holidays and state holidays?
- Which regression model performs best for forecasting future sales?

---

## 📂 Dataset Description

The project uses the Rossmann store sales dataset loaded from:

- `train.csv`

The dataset includes variables such as:

- `Store`
- `DayOfWeek`
- `Date`
- `Sales`
- `Customers`
- `Open`
- `Promo`
- `StateHoliday`
- `SchoolHoliday`

Additional date-based features were created from the `Date` column, including:

- `Year`
- `Month`
- `DayOfMonth`

The notebook also creates a subset of the **top 200 stores** for focused modelling and comparison.

---

## 🧪 Tools and Libraries Used

This project was built using:

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **scikit-learn**

Main modelling tools include:

- `LinearRegression`
- `train_test_split`
- `r2_score`

These libraries were used for cleaning, summarising, visualising, modelling, and evaluating the sales data.

---

## 🧹 Data Preparation

Before modelling, the notebook performs several preprocessing steps:

### 1. Load and parse the dataset
The CSV file is loaded with Pandas, and the `Date` field is converted into a proper datetime format.

### 2. Create new date features
Additional time-based variables are extracted from the `Date` column:

- `Year`
- `Month`
- `DayOfMonth`

These features support year-based, month-based, and daily sales analysis.

### 3. Review variable structure
The notebook checks the structure and value ranges of key variables such as:

- `Store`
- `DayOfWeek`
- `Open`
- `Promo`
- `StateHoliday`
- `SchoolHoliday`

### 4. Check for missing and incorrect data
The project reviews missing values and validates the dataset before running analysis and modelling.

### 5. Remove outliers
Outliers are identified and removed to improve modelling quality and reduce the effect of extreme observations.

### 6. Create a top 200 stores subset
A separate subset is created for the top 200 stores so that analysis and forecasting can focus on the most significant store group.

---

## 🔍 Exploratory Data Analysis

The notebook performs a broad EDA workflow to understand store sales behaviour.

### 1. Continuous variable analysis
The project explores numeric variables such as:

- `Sales`
- `Customers`

to understand their spread and relationship.

### 2. Categorical variable analysis
Categorical features such as promotions, holidays, and day-of-week are reviewed to understand how store sales differ across categories.

### 3. Year-based sales comparison
The project compares total sales across years for both:

- all stores
- top 200 stores

to identify overall sales trends.

### 4. Day-of-week sales analysis
Daily sales patterns are compared to understand which weekdays generate stronger or weaker sales.

### 5. Correlation analysis
A correlation matrix is created to examine the relationships among store sales, customers, promotions, holidays, and time-based features.

### 6. Feature-specific sales analysis
Separate analyses are performed for:

- Customers
- Promotions
- Day of Week
- School Holidays
- State Holidays

This helps identify which features are strongest candidates for prediction.

---

## 🤖 Regression Modelling

The project builds several **linear regression models** to predict `Sales`.

### One-dimensional models
The notebook first builds models using one predictor at a time:

- Customers
- Promo
- SchoolHoliday
- StateHoliday

### Two-dimensional models
The notebook then compares models using two predictors:

- Customers & Promo
- Customers & SchoolHoliday
- Customers & StateHoliday
- Promo & SchoolHoliday
- Promo & StateHoliday
- SchoolHoliday & StateHoliday

Each model is evaluated using:

- training score
- testing score
- regression coefficients

---

## 📊 Model Comparison

The notebook compares all regression models and ranks them by predictive performance.

The strongest model is:

- **Customers & Promo**

This model achieved approximately:

- **Training Score:** 0.804
- **Testing Score:** 0.806

Other strong-performing models include:

- Customers & StateHoliday
- Customers & SchoolHoliday
- Customers only

This suggests that **customer count** is the strongest individual predictor of sales, and combining it with **promotion status** improves predictive performance further.

---

## 📈 Forecasting Future Sales

After comparing the models, the notebook uses the best-performing regression setup to forecast future sales for **July 2015**.

### Attempt 1
The first forecasting attempt compares predicted sales against actual sales for July 2015.

Results:

- **Actual Sales:** 58,674,070
- **Predicted Sales:** 57,133,376
- **% Difference:** -2.626%
- **Accuracy Score:** -0.787

### Attempt 2
A second forecasting setup improves the fit between predicted and actual values.

Results:

- **Actual Sales:** 51,274,647
- **Predicted Sales:** 49,802,828
- **% Difference:** -2.87%
- **Accuracy Score:** 0.695

This second attempt provides the better forecasting result and is used as the final model comparison output.

---

## 📊 Key Visualisations

### 1. Total Sales by Year

![Total Sales by Year](Screenshot%202026-04-09%20at%204.20.05%E2%80%AFpm.png)

This chart compares total sales across **2013, 2014, and 2015** for both **all stores** and the **top 200 stores**. In both views, sales are highest in **2013**, slightly lower in **2014**, and much lower in **2015**, which is expected because the 2015 data only covers part of the year. The chart also shows that the top 200 stores account for a substantial share of overall sales.

### 2. Total Sales by Day of Week

![Total Sales by Day of Week](Screenshot%202026-04-09%20at%204.20.21%E2%80%AFpm.png)

This line chart shows how total sales vary across the **days of the week**. Sales are strongest on **Day 1** and **Day 5**, while **Day 7** has the weakest performance by a large margin. The same general pattern appears across 2013, 2014, and 2015, suggesting a strong weekly sales cycle.

### 3. Correlation Heatmap

![Correlation Heatmap](Screenshot%202026-04-09%20at%204.20.32%E2%80%AFpm.png)

The correlation matrix summarizes the relationships among the main variables used in the project. The strongest positive relationship is between **Sales** and **Customers** (**0.82**), confirming that customer volume is the most important driver of store sales. **Promo** also has a moderate positive correlation with **Sales**, while holiday-related variables show much weaker relationships.

### 4. Actual vs Predicted Sales Forecast

![Actual vs Predicted Sales](Screenshot%202026-04-09%20at%204.21.21%E2%80%AFpm.png)

This chart compares **actual sales** and **predicted sales** for the final forecasting attempt. The prediction line follows the overall sales pattern reasonably well, including the sharp drops and rebounds throughout the month. Although the model does not perfectly match every peak and trough, it captures the general movement of sales and shows that the forecasting approach is useful.

---

## 📈 Main Insights

The project reveals several key findings:

- **Customers** is the strongest predictor of store sales
- **Promotions** improve model performance when combined with customer counts
- **SchoolHoliday** and **StateHoliday** have much weaker predictive power on their own
- sales vary clearly across **years** and **days of the week**
- **Day 7** consistently has the lowest sales
- simple linear regression can provide useful forecasts when strong business variables such as customers and promotions are included

Overall, the project shows that combining **customer activity** and **promotion status** leads to the most effective simple sales forecasting model in this dataset.

---

## 🛠️ Techniques Used

This project demonstrates the use of:

- `read_csv()`
- datetime conversion
- date feature extraction
- missing-value checks
- outlier filtering
- `groupby()`
- summary statistics
- Seaborn and Matplotlib visualisations
- `train_test_split()`
- `LinearRegression()`
- `predict()`
- `score()`
- `r2_score()`

---

## 📁 Files

- `Sales_Forecasting_Project.ipynb` – Jupyter notebook containing the full data analysis and forecasting workflow
- `train.csv` – Rossmann training dataset used in the project
- `Screenshot 2026-04-09 at 4.20.05 pm.png` – total sales by year visualisation
- `Screenshot 2026-04-09 at 4.20.21 pm.png` – total sales by day of week visualisation
- `Screenshot 2026-04-09 at 4.20.32 pm.png` – correlation heatmap
- `Screenshot 2026-04-09 at 4.21.21 pm.png` – actual vs predicted sales forecast visualisation

---

## ▶️ How to Run the Project

1. Open the notebook in **Jupyter Notebook**, **JupyterLab**, or **VS Code**
2. Make sure `train.csv` is in the same working directory
3. Install the required libraries if needed:

```python
pip install pandas numpy matplotlib seaborn scikit-learn
