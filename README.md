<div align="center">

# 🌍 Global Affordability Dashboard
### Urban Cost of Living Analysis - Tableau & Machine Learning

 
[![Python](https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Tableau](https://img.shields.io/badge/Tableau-Public-E97627?style=for-the-badge&logo=tableau&logoColor=white)](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/GlobalAffordabilityTracker2025)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-ML-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Status](https://img.shields.io/badge/Status-Complete-2ea44f?style=for-the-badge)](https://github.com/TejashwiniSaravanan/global-affordability-dashboard-tableau-ml)
[![License](https://img.shields.io/badge/License-MIT-lightgrey?style=for-the-badge)](LICENSE)

<br/>

**In an era of record-high inflation and wage stagnation, understanding the *real* cost of living is critical.**
This project integrates global cost-of-living metrics with salary data across **3,700+ cities** to compute a custom **Affordability Score** - revealing where people thrive and where they barely survive.

<br/>

[![View Live Dashboard](https://img.shields.io/badge/🔴%20View%20Live%20Dashboard%20on%20Tableau%20Public-FF6B6B?style=for-the-badge)](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/GlobalAffordabilityTracker2025)


</div>

---

## ⚡ Key Results at a Glance

| Metric | Result |
|---|---|
| 🏙️ Cities Analysed | **3,700+** |
| 🌐 Countries Covered | **195+** |
| 🤖 Random Forest R² Score | **0.975** |
| 📉 Model RMSE | **1.13** |
| 🔑 Top Affordability Driver | **Median Salary (+9.43 coeff)** |
| 🚨 "Crisis Zone" Countries | **127** (High Cost - Low Salary) |
| 🏆 Most Affordable City Type | **Small metros with rent-to-salary < 5%** |

---

## 📊 Interactive Dashboard Suite

> Click any dashboard title to explore the **live, interactive Tableau version**.

| | |
|:---:|:---:|
| [![Dashboard 1](https://github.com/TejashwiniSaravanan/cost-of-living-crisis-dashboard/blob/main/images/Dashboard%201%20Global%20Affordability%20Tracker%202025.png?raw=true)](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/GlobalAffordabilityTracker2025) | [![Dashboard 2](https://github.com/TejashwiniSaravanan/cost-of-living-crisis-dashboard/blob/main/images/Dashboard%202%20%20Country-Level%20Affordability%20Insights.png?raw=true)](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/Country-LevelAffordabilityInsights) |
| **[🌍 Dashboard 1: Global Affordability Tracker 2025](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/GlobalAffordabilityTracker2025)** | **[📈 Dashboard 2: Country-Level Insights](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/Country-LevelAffordabilityInsights)** |
| Visualises geographic "Economic Red Zones" where living costs exceed local earnings. Uses a custom Affordability Score to identify global disparities. | Benchmarks average salaries against total essential costs (rent, groceries, utilities) to reveal which nations face the highest inflation pressure. |
| [![Dashboard 3](https://github.com/TejashwiniSaravanan/cost-of-living-crisis-dashboard/blob/main/images/Dashboard%203%20City-Level%20Affordability%20Insights%20.png?raw=true)](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/City-LevelAffordabilityInsights) | [![Dashboard 4](https://github.com/TejashwiniSaravanan/cost-of-living-crisis-dashboard/blob/main/images/Dashboard%204%20Global%20Cost%20of%20Living%20Key%20Insights.png?raw=true)](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/GlobalCostofLivingKeyInsights) |
| **[🏙️ Dashboard 3: City Deep-Dive](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/City-LevelAffordabilityInsights)** | **[💡 Dashboard 4: Key Insights](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/GlobalCostofLivingKeyInsights)** |
| A granular analysis of the Top 10 and Bottom 10 cities. Highlights the "Rent Trap" where housing costs consume more than 40% of median salary. | Synthesises regional cost patterns and visualises K-Means clustering results to categorise cities into distinct economic profiles. |

---

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| **Language** | Python 3.x |
| **Data Wrangling** | Pandas, NumPy |
| **Machine Learning** | Scikit-Learn - Linear Regression, Random Forest, K-Means Clustering |
| **Visualisation** | Tableau Desktop / Public, Matplotlib, Seaborn |
| **Project Management** | MS Project, Notion, Google Workspace |
| **Notebook** | Jupyter Notebook |

---

## ⚙️ Analytical Pipeline

### 1. 🧹 Data Wrangling & Feature Engineering

- **Integration:** Merged two Kaggle datasets - *Global Cost of Living* and *Global Salary Data* - using a `pd.merge()` inner join on City and Country.
- **Standardisation:** Resolved naming inconsistencies (e.g., `"USA"` vs `"United States"`) and handled missing salary values via proxy imputation.
- **Feature Engineering:** Derived a custom **Affordability Score** metric:

$$\text{Affordability Score} = \frac{\text{Monthly Median Salary}}{\text{Rent} + \text{Groceries} + \text{Utilities}}$$

<img src="https://github.com/TejashwiniSaravanan/cost-of-living-crisis-dashboard/blob/main/images/Distribution%20of%20Affordability%20Scores%20Histogram.png?raw=true" width="450"/>

> *Most cities cluster around median affordability - proving that true financial comfort is reserved for a global minority.*

---

### 2. 🤖 Machine Learning Models

#### A. Predictive Modelling - Random Forest Regressor

- **Test R²: 0.975** - capturing complex, non-linear relationships between salary and essential costs.
- **RMSE: 1.13** - significantly outperforming a single Decision Tree baseline.

<img src="https://github.com/TejashwiniSaravanan/cost-of-living-crisis-dashboard/blob/main/images/Random%20Forest%20Performance%20Metrics%20.png?raw=true" width="350"/>

> *The Random Forest Regressor achieved a near-perfect fit on held-out test data.*

---

#### B. Key Drivers - Linear Regression (Standardised Coefficients)

| Driver | Coefficient | Direction |
|---|---|---|
| 💰 Median Salary | +9.43 | ✅ Strongest positive driver |
| 🛒 Grocery Prices | -4.29 | ❌ Primary drag on affordability |
| 🏠 Rent | -4.11 | ❌ Second largest negative driver |

<img src="https://github.com/TejashwiniSaravanan/cost-of-living-crisis-dashboard/blob/main/images/Standardized%20Coefficients%20.png?raw=true" width="350"/>

> *Identifying Median Salary, Groceries, and Rent as the primary drivers of the Affordability Score.*

---

#### C. Market Segmentation - K-Means Clustering (k=5)

Cities were segmented into 5 distinct economic profiles:

| Cluster | Profile | Countries |
|---|---|---|
| **Cluster 1** | High Salary - High Cost (manageable rent burden) | 19 |
| **Cluster 0** | High Cost - Low Salary (**"Crisis Zone"**) | 127 |
| **Cluster 3** | Low Salary - Low Cost | 104 |

<img src="https://github.com/TejashwiniSaravanan/cost-of-living-crisis-dashboard/blob/main/images/Rent%20Burden%20by%20Cluster%20Boxplot.png?raw=true" width="350"/>

> *Rent as a percentage of salary varies dramatically across city clusters - revealing stark global inequality.*

---

## 📊 Global Insights & Quartile Analysis

- **Q1 (Lowest Affordability):** Residents spend approximately **50% of their salary** on essentials - a survival-based economy with no financial cushion.
- **The Rent Lever:** Rent burden falls by nearly **28 percentage points** when moving from the lowest (Q1) to the highest (Q4) affordability quartile.
- **Top Performers:** Non-major metro areas like **Emporia (USA)** and **Treherbert (UK)** achieved the highest scores due to exceptionally low rent-to-salary ratios (~3-5%).

---

## 🚀 Business & Policy Recommendations

> **1. 🏠 Housing Policy**
> Implement rent control or housing subsidies in any city where the Rent-to-Salary ratio exceeds **35%**.

> **2. 💼 Corporate Strategy**
> Businesses in high-cost cities should adopt **Cost-of-Living-Adjusted (COLA)** salaries to ensure wage fairness and improve talent retention.

> **3. 🚚 Supply Chain Optimisation**
> Focus on local supply chain development for essential goods in "High Cost - Low Salary" cities to drive down grocery price indices.

---

## 💻 Getting Started
 
```bash
#1. Clone the repository
git clone https://github.com/TejashwiniSaravanan/global-affordability-dashboard-tableau-ml.git
cd global-affordability-dashboard-tableau-ml

#2. Install dependencies
pip install -r requirements.txt
 
#3. Launch the notebook
jupyter notebook cost-of-living-crisis.ipynb
```

> To explore the Tableau dashboards, open `cost-of-living-crisis.twb` in Tableau Desktop, or visit the **[live Tableau Public version](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/GlobalAffordabilityTracker2025)**.

---

## 📂 Repository Structure

```
global-affordability-dashboard-tableau-ml/
│
├── 📁 images/                          # Dashboard screenshots & analytical plots
├── 📄 Executive_Summary.pdf            # 1-page business impact summary
├── 📊 Project_Presentation.pdf         # Full visual slide deck
├── 📓 cost-of-living-crisis.ipynb      # Python notebook - data cleaning & ML models
├── 🗄️  cost-of-living-crisis.csv        # Cleaned & merged global dataset (3,700+ cities)
├── 📈 cost-of-living-crisis.twb        # Tableau Workbook file
├── 📋 requirements.txt                 # Python dependencies
├── 📖 README.md                        # Project documentation (you are here)
└── ⚖️  LICENSE                          # MIT License
```

---

## 📝 Project Reflection

| | |
|---|---|
| ✅ **What Went Well** | Successfully built a robust predictive framework (R² = 0.975) and transformed complex global data into four user-friendly, interactive Tableau dashboards. |
| ⚠️ **What Didn't Go Well** | Missing and inconsistent data for smaller cities required proxy imputation, which may affect localised precision. |
| 🔭 **Future Work** | Integrate **real-time datasets** and additional cost categories - Healthcare, Transport, and Education - for a 360° affordability view. |

---

## 👤 Author

<div align="center">

**Tejashwini Saravanan**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/tejashwinisaravanan/)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/TejashwiniSaravanan)
[![Portfolio](https://img.shields.io/badge/Portfolio-Visit-FF6B6B?style=for-the-badge&logo=google-chrome&logoColor=white)](https://tejashwinisaravanan.github.io/global-affordability-dashboard-tableau-ml/)

</div>

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

---

<div align="center">

*If you found this project insightful, please consider giving it a ⭐ - it helps others discover it!*

</div>
