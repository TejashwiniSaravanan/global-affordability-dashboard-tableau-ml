# 🌍 Cost of Living Crisis Dashboard: Global Affordability Analysis 

![Tableau](https://img.shields.io/badge/Visualization-Tableau-blue) ![Python](https://img.shields.io/badge/Data_Science-Python-green) ![ML](https://img.shields.io/badge/Machine_Learning-Scikit--Learn-orange) ![Status](https://img.shields.io/badge/Status-Complete-success)

## 📌 Project Overview
In an era of record-high inflation and wage stagnation, understanding the "real" cost of living is critical for global citizens and policymakers. This project integrates **Global Cost of Living** metrics with **Global Salary Data** to calculate a custom **Affordability Score** for cities worldwide. 

By merging disparate datasets and applying machine learning models (Random Forest, Linear Regression, and K-Means Clustering), this project identifies the true economic burden of rent, groceries, and utilities relative to local earnings.

## 📊 Interactive Dashboard Suite

The following grid provides a high-level overview of the global affordability analysis. Click on the dashboard titles to explore the interactive versions on Tableau Public.

| [Dashboard 1: Global Affordability](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/GlobalAffordabilityTracker2025) | [Dashboard 2: Country Insights](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/Country-LevelAffordabilityInsights) |
| :---: | :---: |
| <img src="images/Dashboard 1 Global Affordability Tracker 2025.png" width="450"> | <img src="images/Dashboard 2  Country-Level Affordability Insights.png" width="450"> |
| **Global Affordability Tracker 2025** | **Country-Level Affordability Insights** |
| *Visualizes geographic "Economic Red Zones" where living costs exceed local earnings. Uses a custom Affordability Score to identify global disparities.* | *Benchmarks average salaries against total essential costs (rent, groceries, utilities) to reveal which nations face the highest inflation pressure.* |
| | |
| [Dashboard 3: City Deep-Dive](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/City-LevelAffordabilityInsights) | [Dashboard 4: Key Insights](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/GlobalCostofLivingKeyInsights) |
| <img src="images/Dashboard 3 City-Level Affordability Insights .png" width="450"> | <img src="images/Dashboard 4 Global Cost of Living Key Insights.png" width="450"> |
| **City-Level Affordability Insights** | **Global Cost of Living Key Insights** |
| *A granular analysis of the Top 10 and Bottom 10 cities. Highlights the "Rent Trap" where housing costs consume more than 40% of the median salary.* | *Synthesizes regional cost patterns and visualizes the results of K-Means clustering to categorize cities into economic profiles.* |

---

## 🛠 Tech Stack & Tools
| Category | Tools |
| :--- | :--- |
| **Data Science** | Python 3.x (Pandas, NumPy) |
| **Machine Learning** | Scikit-Learn (Linear Regression, Random Forest, K-Means) |
| **Visualization** | Tableau Desktop/Public, Matplotlib, Seaborn |
| **Project Mgmt** | MS Project, Notion, Google Workspace |

---

## ⚙️ Analytical Pipeline
### 1. Data Wrangling & Merging
* **Integration:** Merged two Kaggle datasets (Global Cost of Living + Global Salary Data) using a `pd.merge()` inner join on City and Country.
* **Standardization:** Resolved naming inconsistencies (e.g., "USA" vs "United States") and handled missing salary values via proxy imputation.
* **Feature Engineering:** Calculated the **Affordability Score**:  
    $$\text{Affordability Score} = \frac{\text{Monthly Median Salary}}{\text{Rent} + \text{Groceries} + \text{Utilities}}$$

 **<img src="images/Distribution of Affordability Scores Histogram.png" width="350">**

*Insight: Most cities cluster around median affordability, proving that true financial comfort is reserved for a global minority.*

### 2. Machine Learning Implementation
#### **A. Predictive Modeling (Random Forest)**
* **Model Performance:** Achieved a **Test R² of 0.975**, capturing complex, non-linear relationships between salary and essential costs.
* **Accuracy:** Significantly outperformed the single Decision Tree model by reducing prediction error (RMSE: 1.13).

 **<img src="images/Random Forest Performance Metrics .png" width="350">**

*Insight: Evaluation of the Random Forest Regressor, achieving a high Test R² of 0.975.*

#### **B. Key Drivers (Linear Regression)**
* **Top Driver:** Median Salary (+9.43 standardized coefficient) is the strongest positive driver.
* **Economic Drags:** Grocery Prices (-4.29) and Rent (-4.11) are the primary negative impacts on urban affordability.

 **<img src="images/Standardized Coefficients .png" width="350">**

 *Insight: dentifying Median Salary, Groceries, and Rent as the primary drivers of the Affordability Score.*

#### **C. Market Segmentation (K-Means Clustering)**
* Applied clustering to segment cities into 5 distinct profiles:
    * **Cluster 1:** High Salary–High Cost (19 countries, manageable rent burdens).
    * **Cluster 0:** High Cost–Low Salary (127 countries, the "Crisis Zone").
    * **Cluster 3:** Low Salary–Low Cost (104 countries).

 **<img src="images/Rent Burden by Cluster Boxplot.png" width="350">**

 *Insight: Boxplot illustrating how rent as a percentage of salary varies significantly across city clusters* 


---

## 📊 Global Insights & Quartile Analysis
* **Q1 (Lowest Affordability):** Residents in these cities spend approximately **50% of their salary** on essentials, creating a survival-based economy.
* **The Rent Lever:** Rent burden falls by nearly **28 percentage points** when moving from the lowest (Q1) to the highest (Q4) affordability quartiles.
* **City Rankings:** Non-major metro areas like **Emporia (USA)** and **Treherbert (UK)** achieved the highest scores due to exceptionally low rent-to-salary ratios (~3-5%).

---

## 🚀 Business & Policy Recommendations
1.  **Housing Policy:** Implement rent control or housing subsidies in cities where the Rent-to-Salary ratio exceeds 35%.
2.  **Corporate Strategy:** Businesses in high-cost cities should adopt **Cost-of-Living-Adjusted (COLA)** salaries to ensure wage fairness and talent retention.
3.  **Supply Chain:** Focus on local supply chain optimization for essential goods in "High Cost–Low Salary" cities to reduce grocery price indices.

---

## 📝 Project Reflection (The 3Ws)
* **What Went Well:** Successfully built a robust predictive framework and transformed complex global data into user-friendly Tableau dashboards.
* **What Didn't Go Well:** Missing/inconsistent data for smaller cities required imputation, which may affect localized precision.
* **What to Improve:** Future work will integrate **real-time datasets** and additional cost categories like **Healthcare and Transport** for a 360-degree affordability view.

---
## 📂 Repository Structure

```text
├── images/                          # Dashboard screenshots and analytical plots
├── Executive_Summary.pdf            # 1-page business impact summary
├── Project_Presentation.pdf         # Visual slide deck of the project
├── README.md                        # Project documentation (this file)
├── cost-of-living-crisis.csv        # Cleaned and merged global dataset
├── cost-of-living-crisis.ipynb      # Python notebook (Data cleaning & ML models)
├── cost-of-living-crisis.twb        # Tableau Workbook file
├── requirements.txt                 # List of required Python libraries
└── LICENSE                          # MIT License file

``` 

## 👤 Author
Tejashwini Saravanan [LinkedIn](https://www.linkedin.com/in/tejashwinisaravanan/)

