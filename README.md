# Global Affordability Dashboard: Cost of Living Analysis with Python ML & Tableau

An end-to-end data science project analyzing urban affordability across 3,700+ cities and 195+ countries. Integrates two global datasets, engineers a custom Affordability Score metric, and applies three machine learning models - Random Forest, Linear Regression, and K-Means Clustering - to segment cities into economic profiles and identify the primary drivers of financial stress worldwide.

<p align="center">
  <a href="https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/GlobalAffordabilityTracker2025">View Live Dashboard - Tableau Public</a> · <a href="Project_Presentation.pdf">View Project Presentation</a> · <a href="Executive_Summary.pdf">View Executive Summary</a> · <a href="https://tejashwinisaravanan.github.io/global-affordability-dashboard-tableau-ml/">View GitHub Pages</a>
</p>

<p align="center">
  <img src="images/Dashboard 1 Global Affordability Tracker 2025.png" width="680" alt="Global Affordability Tracker Dashboard"/>
</p>

<p align="center"><em>Dashboard 1: Global Affordability Tracker 2025 - geographic Economic Red Zones where living costs exceed local earnings.</em></p>

---

## Overview

The cost of living crisis is not uniform. In some cities, residents spend over 50% of their monthly salary on rent, groceries, and utilities alone - leaving nothing for savings, healthcare, or emergencies. In others, the same income covers essentials with significant surplus. Understanding exactly where that line falls, and what drives it, requires integrating data that is rarely combined: granular cost-of-living metrics at the city level with actual median salary data.

This project does that integration. By merging two Kaggle datasets on 3,700+ cities, engineering a custom Affordability Score, and applying a layered ML pipeline, the analysis identifies which economic variables most powerfully predict financial stress, which cities sit in genuine crisis zones, and what policy or business interventions could move the needle.

The project also has a direct healthcare extension. Healthcare costs are one of the largest drivers of financial instability globally - particularly in countries without universal coverage. A natural next iteration of this affordability model would incorporate out-of-pocket healthcare expenditure as a core affordability variable, connecting urban cost analysis to public health outcomes in a way that is directly relevant to health policy work.

---

## Results at a Glance

| Metric | Result |
|---|---|
| Cities Analyzed | 3,700+ |
| Countries Covered | 195+ |
| Random Forest R² | 0.975 |
| Model RMSE | 1.13 |
| Top Affordability Driver | Median Salary (+9.43 standardized coefficient) |
| Crisis Zone Countries | 127 (High Cost - Low Salary cluster) |
| Most Affordable City Type | Small metros with rent-to-salary ratio below 5% |

---

## The Data

| | |
|---|---|
| Dataset 1 | Global Cost of Living - Kaggle (rent, groceries, utilities by city) |
| Dataset 2 | Global Salary Data - Kaggle (median monthly salary by city and country) |
| Merged On | City and Country (inner join) |
| Final Records | 3,700+ city-level observations |
| Tools | Python, Pandas, NumPy, Scikit-Learn, Tableau Desktop, Jupyter Notebook |

---

## Analytical Pipeline

### Stage 1 - Data Integration and Feature Engineering

The two source datasets use inconsistent country naming conventions - "USA" in one, "United States" in the other, "UK" versus "United Kingdom" throughout. Resolving these inconsistencies before the merge was the most critical data quality step in the project. A join on mismatched keys silently drops rows without error, which means a dataset that appears complete is actually missing entire countries.

After standardizing naming conventions, the datasets were merged using a `pd.merge()` inner join on City and Country, retaining only cities with both cost and salary data. Missing salary values for smaller cities were handled via proxy imputation using regional medians rather than global medians - a more defensible approach because salary levels vary significantly by region and a global median would introduce systematic bias for lower-income geographies.

The central engineered feature is the **Affordability Score**:

$$\text{Affordability Score} = \frac{\text{Monthly Median Salary}}{\text{Rent} + \text{Groceries} + \text{Utilities}}$$

A score above 1.0 means a median earner can cover essentials. Below 1.0 means they cannot. This ratio is more analytically useful than any single cost variable because it captures the relationship between earnings and expenditure rather than either in isolation.

<p align="center">
  <img src="images/Distribution of Affordability Scores Histogram.png" width="560" alt="Distribution of Affordability Scores across 3,700+ cities"/>
</p>

<p align="center"><em>Most cities cluster around median affordability - confirming that genuine financial comfort is available to a global minority rather than the norm.</em></p>

---

### Stage 2 - Predictive Modeling with Random Forest

A Random Forest Regressor was trained to predict Affordability Score from the full feature set. Random Forest was selected over a single Decision Tree because it averages predictions across many trees, reducing variance and handling non-linear feature interactions - both of which are present in cost-of-living data where the relationship between salary and rent burden differs dramatically by region.

The model was evaluated on a held-out test set using 80/20 train-test split.

| Metric | Random Forest | Decision Tree Baseline |
|---|---|---|
| R² Score | 0.975 | Lower |
| RMSE | 1.13 | Higher |

An R² of 0.975 means the model explains 97.5% of variance in Affordability Score across cities it was not trained on. The low RMSE of 1.13 confirms that predictions are tightly clustered around actual values - the model generalizes well rather than overfitting to the training data.

<p align="center">
  <img src="images/Random Forest Performance Metrics .png" width="540" alt="Random Forest performance metrics and actual vs predicted plot"/>
</p>

<p align="center"><em>Near-perfect fit on held-out test data - the Random Forest captures complex non-linear relationships between salary, rent, and essential costs that a linear model would miss.</em></p>

---

### Stage 3 - Driver Identification with Linear Regression

While Random Forest explains how well affordability can be predicted, it does not directly explain which variables drive it. A Linear Regression model with standardized coefficients was used specifically for interpretability - standardizing all features before fitting means the coefficients are comparable on the same scale, showing the relative impact of each variable on affordability.

| Driver | Standardized Coefficient | Direction |
|---|---|---|
| Median Salary | +9.43 | Strongest positive driver |
| Grocery Prices | -4.29 | Primary drag on affordability |
| Rent | -4.11 | Second largest negative driver |
| Utilities | Smaller negative | Minor drag |

<p align="center">
  <img src="images/Standardized Coefficients .png" width="540" alt="Standardized regression coefficients showing relative impact of each variable"/>
</p>

<p align="center"><em>Median Salary has more than twice the impact of any cost variable - meaning wage policy is a more powerful affordability lever than rent control or grocery subsidies alone.</em></p>

The salary coefficient of +9.43 compared to rent at -4.11 has a direct policy implication: a 10% increase in median salary improves affordability more than a 10% reduction in rent. This finding reframes the affordability crisis as a wage problem first and a housing problem second - a distinction that matters for how governments and employers prioritize interventions.

---

### Stage 4 - City Segmentation with K-Means Clustering

K-Means clustering with k=5 was applied to segment cities into distinct economic profiles based on salary level, rent burden, grocery cost, and Affordability Score. The optimal k was selected using the elbow method on within-cluster sum of squares.

| Cluster | Economic Profile | Countries |
|---|---|---|
| Cluster 1 | High Salary - High Cost (manageable rent burden) | 19 |
| Cluster 0 | High Cost - Low Salary - Crisis Zone | 127 |
| Cluster 3 | Low Salary - Low Cost | 104 |
| Clusters 2 & 4 | Transitional economies | Remaining |

<p align="center">
  <img src="images/Rent Burden by Cluster Boxplot.png" width="540" alt="Rent burden by cluster showing variance across economic profiles"/>
</p>

<p align="center"><em>Rent as a percentage of salary varies dramatically across clusters - Cluster 0 cities see residents spending over 50% of income on housing alone, leaving minimal margin for other essentials.</em></p>

The 127-country Crisis Zone cluster is the most actionable finding in the project. These are not edge cases - they represent the majority of countries analyzed, meaning unaffordable urban living is the global default rather than the exception.

---

## Four Interactive Tableau Dashboards

All four dashboards are live and interactive on Tableau Public.

**[Dashboard 1 - Global Affordability Tracker 2025](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/GlobalAffordabilityTracker2025)**
Geographic view of Economic Red Zones where living costs exceed local earnings. Uses the custom Affordability Score to surface global disparities at a glance.

<p align="center">
  <img src="images/Dashboard 1 Global Affordability Tracker 2025.png" width="620" alt="Dashboard 1 - Global Affordability Tracker"/>
</p>

---

**[Dashboard 2 - Country-Level Affordability Insights](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/Country-LevelAffordabilityInsights)**
Benchmarks average salaries against total essential costs by country. Identifies which nations face the highest inflation pressure relative to local wages.

<p align="center">
  <img src="images/Dashboard 2  Country-Level Affordability Insights.png" width="620" alt="Dashboard 2 - Country Level Insights"/>
</p>

---

**[Dashboard 3 - City Deep-Dive](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/City-LevelAffordabilityInsights)**
Granular analysis of the top 10 and bottom 10 cities by affordability. Highlights the Rent Trap - cities where housing consumes more than 40% of median salary.

<p align="center">
  <img src="images/Dashboard 3 City-Level Affordability Insights .png" width="620" alt="Dashboard 3 - City Deep Dive"/>
</p>

---

**[Dashboard 4 - Key Insights & Clustering Results](https://public.tableau.com/app/profile/tejashwini.saravanan8751/viz/finalprojectassigmentTableau/GlobalCostofLivingKeyInsights)**
Synthesizes regional cost patterns and visualizes the K-Means clustering output, mapping each city to its economic profile.

<p align="center">
  <img src="images/Dashboard 4 Global Cost of Living Key Insights.png" width="620" alt="Dashboard 4 - Key Insights"/>
</p>

---

## Key Findings

**The affordability crisis is the global norm, not the exception.** 127 out of 195+ countries fall into the High Cost - Low Salary cluster. Cities in the bottom affordability quartile see residents spending approximately 50% of monthly salary on essentials alone, leaving no financial buffer for savings, healthcare, or emergencies.

**Salary is a more powerful lever than rent.** The standardized regression coefficient for Median Salary (+9.43) is more than twice the magnitude of Rent (-4.11). Policies that raise wages improve affordability more efficiently than rent subsidies or grocery price controls targeting the same percentage change.

**The Rent Trap is real and measurable.** Cities where rent exceeds 40% of median salary show disproportionately low scores on all other affordability dimensions - grocery spending is compressed, savings rates collapse, and financial resilience effectively disappears.

**Small metros outperform large cities on affordability.** Non-major metro areas like Emporia, USA and Treherbert, UK achieved the highest Affordability Scores due to rent-to-salary ratios below 5%. The assumption that cities with higher nominal salaries are more affordable does not hold when cost of living is factored in.

**The model generalizes across geographies.** An R² of 0.975 on held-out test data confirms that the underlying drivers of affordability are structurally consistent across cultures and geographies - not artifacts of regional data quirks.

---

## Policy and Business Recommendations

**For governments in Crisis Zone countries:** The analysis supports a rent-to-salary ratio threshold of 35% as a policy trigger for housing intervention. Cities crossing this threshold show cascading affordability deterioration across all essential cost categories.

**For employers and HR teams:** Cost-of-Living-Adjusted salary frameworks are analytically defensible. The salary coefficient confirms that wage adjustments are the most efficient mechanism for improving employee financial stability - more effective per dollar than benefits packages addressing individual cost categories in isolation.

**For supply chain and retail operations:** Cities in the High Cost - Low Salary cluster show the highest grocery price sensitivity. Local supply chain development in these markets would reduce grocery cost indices and directly improve affordability for the largest segment of the global urban population.

**For health policy:** The natural extension of this model is incorporating out-of-pocket healthcare expenditure as a fourth essential cost variable. In countries without universal coverage, healthcare costs represent one of the largest and least predictable affordability shocks. A healthcare-adjusted affordability score would connect this economic analysis directly to public health outcomes.

---

## Repository Structure

```
global-affordability-dashboard-tableau-ml/
│
├── images/                             # All dashboard and analytical plot screenshots
│   ├── Dashboard 1 Global Affordability Tracker 2025.png
│   ├── Dashboard 2  Country-Level Affordability Insights.png
│   ├── Dashboard 3 City-Level Affordability Insights .png
│   ├── Dashboard 4 Global Cost of Living Key Insights.png
│   ├── Distribution of Affordability Scores Histogram.png
│   ├── Random Forest Performance Metrics .png
│   ├── Rent Burden by Cluster Boxplot.png
│   └── Standardized Coefficients .png
│
├── cost-of-living-crisis.ipynb         # Full Python notebook - data wrangling, ML models
├── cost-of-living-crisis.csv           # Cleaned merged dataset (3,700+ cities)
├── cost-of-living-crisis.twb           # Tableau Workbook file
├── Executive_Summary.pdf               # 1-page business impact summary
├── Project_Presentation.pdf            # Full visual slide deck
├── requirements.txt                    # Python dependencies
├── LICENSE                             # MIT License
└── README.md
```

---

## Getting Started

```bash
# Clone the repository
git clone https://github.com/TejashwiniSaravanan/global-affordability-dashboard-tableau-ml.git
cd global-affordability-dashboard-tableau-ml

# Install dependencies
pip install -r requirements.txt

# Launch the notebook
jupyter notebook cost-of-living-crisis.ipynb
```

To explore the Tableau dashboards, open `cost-of-living-crisis.twb` in Tableau Desktop or visit the live Tableau Public links above.

---

## Limitations and What I Would Do Next

The merged dataset drops cities that appear in one source but not the other. Smaller and lower-income cities are disproportionately absent from salary datasets, which means the analysis likely underrepresents the most severely unaffordable urban environments.

The proxy imputation for missing salary values uses regional medians, which is defensible but introduces smoothing. Cities with genuinely anomalous salary structures - resource extraction towns, government administrative centers, tourism-dependent economies - may be misrepresented by regional averaging.

The most important extension is adding healthcare expenditure as a fourth essential cost variable. Out-of-pocket healthcare costs are highly correlated with financial fragility in countries without universal coverage, and their absence means the affordability score systematically understates financial stress in those markets.

---

## Tools and Technologies

Python · Pandas · NumPy · Scikit-Learn · Random Forest · K-Means Clustering · Linear Regression · Tableau Desktop · Tableau Public · Jupyter Notebook · Matplotlib · Seaborn

---

## Related Projects

- **[Clinical Trial Patient Selection](https://github.com/TejashwiniSaravanan/Clinical-Trial-Patient-Selection-Optimization)** - Predictive modeling for patient recruitment optimization
- **[Healthcare Analytics - PySpark ML & GCP Strategy](https://github.com/TejashwiniSaravanan/Healthcare-Analytics-PySpark-ML-GCP-Strategy)** - Cloud architecture for real-time patient monitoring
- **[Pharmaceutical Sales Analytics - Power BI](https://github.com/TejashwiniSaravanan/Drug-Sales-Analysis-PowerBI)** - Star Schema BI solution for global drug sales and regulatory compliance

---

## About Me

**Tejashwini Saravanan** - Master's student in Data Analytics at Seattle Pacific University, focused on healthcare data engineering, economic analytics, and scalable ML pipelines.

[LinkedIn](https://www.linkedin.com/in/tejashwinisaravanan/) · [GitHub](https://github.com/TejashwiniSaravanan) · [Tableau Public](https://public.tableau.com/app/profile/tejashwini.saravanan8751)

---

*Data: Global Cost of Living & Global Salary Data - Kaggle · License: MIT · Seattle Pacific University*
