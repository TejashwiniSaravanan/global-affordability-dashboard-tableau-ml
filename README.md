# 🌍 Cost of Living Crisis Dashboard: Global Affordability Analysis 

![Tableau](https://img.shields.io/badge/Visualization-Tableau-blue) ![Python](https://img.shields.io/badge/Data_Science-Python-green) ![ML](https://img.shields.io/badge/Machine_Learning-Scikit--Learn-orange) ![Status](https://img.shields.io/badge/Status-Complete-success)

## 📌 Project Overview
In an era of record-high inflation and wage stagnation, understanding the "real" cost of living is critical for global citizens and policymakers. This project integrates **Global Cost of Living** metrics with **Global Salary Data** to calculate a custom **Affordability Score** for cities worldwide. 

By merging disparate datasets and applying machine learning models (Random Forest, Linear Regression, and K-Means Clustering), this project identifies the true economic burden of rent, groceries, and utilities relative to local earnings.

### 🔗 Interactive Dashboards (Tableau Public)
The visualization suite follows a "Macro-to-Micro" design philosophy, transitioning from global trends to specific city-level economic drivers:

* **[Dashboard 1: Global Affordability Tracker 2025](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/GlobalAffordabilityTracker2025)**
    * **Focus:** Geographical heat map of the custom Affordability Score. Identifies "Economic Red Zones" where costs heavily outweigh local earnings.
* **[Dashboard 2: Country-Level Affordability Insights](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/Country-LevelAffordabilityInsights)**
    * **Focus:** Ranks countries by Rent-to-Salary percentages, highlighting how national housing markets impact disposable income.
* **[Dashboard 3: City-Level Affordability Insights](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/City-LevelAffordabilityInsights)**
    * **Focus:** A granular "Search & Compare" interface for specific cities, breaking down costs for Groceries, Rent, and Utilities.
* **[Dashboard 4: Global Cost of Living Key Insights](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/GlobalCostofLivingKeyInsights)**
    * **Focus:** Visualizes Machine Learning outputs, including K-Means clusters (e.g., "High Salary–High Cost" vs. "Affordable Hubs").
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

> 📸 **[Insert Screenshot: Distribution of Affordability Scores Histogram from Slide 4]** > *Insight: Most cities cluster around median affordability, proving that true financial comfort is reserved for a global minority.*

### 2. Machine Learning Implementation
#### **A. Predictive Modeling (Random Forest)**
* **Model Performance:** Achieved a **Test R² of 0.975**, capturing complex, non-linear relationships between salary and essential costs.
* **Accuracy:** Significantly outperformed the single Decision Tree model by reducing prediction error (RMSE: 1.13).

> 📸 **[Insert Screenshot: Random Forest Performance Metrics from Slide 6]**

#### **B. Key Drivers (Linear Regression)**
* **Top Driver:** Median Salary (+9.43 standardized coefficient) is the strongest positive driver.
* **Economic Drags:** Grocery Prices (-4.29) and Rent (-4.11) are the primary negative impacts on urban affordability.

> 📸 **[Insert Screenshot: Standardized Coefficients Bar Chart from Slide 8]**

#### **C. Market Segmentation (K-Means Clustering)**
* Applied clustering to segment cities into 5 distinct profiles:
    * **Cluster 1:** High Salary–High Cost (19 countries, manageable rent burdens).
    * **Cluster 0:** High Cost–Low Salary (127 countries, the "Crisis Zone").
    * **Cluster 3:** Low Salary–Low Cost (104 countries).

> 📸 **[Insert Screenshot: Rent Burden by Cluster Boxplot from Slide 5 or 7]**

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
├── data/
│   └── final_project_assignment_csv.csv    # Merged & Cleaned Dataset
├── notebooks/
│   └── finalprojectassignment.ipynb        # Python Wrangling & ML Code
├── docs/
│   ├── Executive_Summary.pdf               # Business Summary
│   ├── Final_Project_Paper.docx            # Detailed Research Paper
│   └── Presentation.pdf                    # Visual Slide Deck
└── README.md
