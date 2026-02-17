Exploraty Data Analysis

Shared link to project: https://colab.research.google.com/drive/1AtdHRuVJXoynP5J3wtb8rsIDrJeOPqPk?usp=sharing#scrollTo=-TCfZY8u7hEj

Project Overview

This project performs Exploratory Data Analysis (EDA) on the dataset related to sales and logistics using Python.

The goal of this analysis is to:

understand the dataset structure

clean and validate data

detect patterns and anomalies

analyze relationships between variables

generate visual insights

🗂 Dataset


data/cleanedDatasets/countries_cleaned.csv
data/cleanedDatasets/events_cleaned.csv
data/cleanedDatasets/products_cleaned.csv
data/cleanedDatasets/final_analytical_dataset.csv

⚙️ Tools & Libraries

Project built using:

Python 3.x
pandas
matplotlib

google/collab


🔍 Analysis Steps
1️⃣ Data Overview

dataset shape and schema
missing values check
duplicates check
data types validation

2️⃣ Data Cleaning

handled missing values
removed duplicates
corrected data types
treated outliers

3️⃣ Exploratory Analysis

distribution analysis
correlation analysis
group aggregations
time trends (if applicable)

4️⃣ Visualization

Key plots created:
distribution plots
boxplots
correlation heatmap
trend charts

All plots saved in the Plots/ folder.


Business recommendations:

Scale high-margin categories
Invest in top regions
Optimize slow-shipping product supply chains
Focus marketing on strongest weekdays
Expand high-profit sales channels
This project demonstrates full-cycle Data Analytics workflow: data cleaning → feature engineering → KPI modeling → visualization → business insights.

▶️ How to Run

Clone the repository:

git clone https://github.com/dmitruzik/exploraty_data_analysis.git
cd project-name


Install dependencies:
pip install -r requirements.txt


Run scripts:

python Python/data_overview.py
python Python/data_cleaning.py

Final Business Insights
This analysis identified:

• Key revenue-driving product categories
• High-value geographic markets
• Most profitable sales channels
• Delivery time patterns
• Sales seasonality trends
• Margin distribution across products

Business recommendations:

Scale high-margin categories
Invest in top regions
Optimize slow-shipping product supply chains
Focus marketing on strongest weekdays
Expand high-profit sales channels
This project demonstrates full-cycle Data Analytics workflow: data cleaning → feature engineering → KPI modeling → visualization → business insights.
