# Chicago Real Estate Price Prediction 
---
## Project Overview
This project analyzes a large real-world dataset of historical Chicago property records (about 1.7 million rows and 69 columns) to understand what drives home prices across the city and to predict them with machine learning.

The work has two parts. In **Part 1**, I cleaned the raw data by handling missing values, removing unreliable columns, and treating outliers. In **Part 2**, I explored price patterns by ZIP code and neighborhood, then compared four regression models: Linear Regression, Ridge Regression, Decision Tree, and Light Random Forest.

The Decision Tree achieved the highest score (R² = 0.749), but feature-importance analysis showed it relied almost entirely on `list_price`, so the result likely overstates its real predictive power. The analysis could help home buyers, sellers, and analysts see how location, property size, and age relate to price.
---
## Code and Reports 
| Part | Code | Report |
|---|---|---|
|1. Data Cleaning | [Notebook](notebooks/data_cleaning_chicago_real_estate_prediction.ipynb) | [Interactive Report](https://ngockhanhhoang.github.io/chicago-real-estate-price-prediction/reports/data_cleaning_chicago_real_estate_prediction.html) |
|2. Visualization and model comparison| | [Download report](reports/data_visualization_model_comparison_chicago_real_estate_price_prediction.zip) |

The Part 2 report is zipped because the original HTML (115,536 KB) exceeds GitHub's file size limit. Download it, unzip it, and open the HTML in a browser.

---
## Key Results
### Model Comparison
| Model | R-squared | RMSE |
|---|---|---|
| Linear Regression | 0.675 | 150,199 |
| Ridge Regression | 0.675 | 149,978 |
| **Decision Tree** | **0.749** | **131,861** |
| Light Random Forest | 0.536 | 179,341 |

*Metrics computed on [test set/ cross-validation]*
**Highest score: Decision Tree.** It explains about 75% of price variance and has the lowest error. However, feature-importance analysis shows it relies almost entirely on 'list_price' (98.6% importance), a likely source of leakage, so its score may overstate real predictive power.
**Most balanced: Light Random Forest.** Its predictions rely more evenly on square footage, garage, and ZIP code, but it scored lower.

### Market Insights
**Price Distribution & Market Trends**
- High-priced clusters are concentrated in downtown neighborhoods: Loop (60601, 60602), River North (60611), and Gold Coast (60610), where median home prices exceed $500K. These areas have high demand due to proximity to corporate hubs and luxury amenities.
- Affordable housing options are available in South and West Chicago, particularly in areas like Englewood (60621) and Austin (60644), where median prices are below $200K.
  
**Demand & Neighborhood Characteristics**
- Strong demand in the North Side (e.g., Lincoln Park (60614), Lakeview (60657), and Wicker Park (60622)) due to access to top-tier schools, cultural hubs, and lakefront amenities. These areas have a higher price-per-square-foot ratio than the city average.
- Garfield Park and Austin have the lowest price per square foot.
  
**Year Built & Property Age Impact**
- Homes in central and north-side areas are newer and renovated, with an average year built post-1990. These attract young professionals seeking modern amenities.
- In contrast, older properties (pre-1950s) dominate the South and West Sides, often requiring significant renovation, which limits first-time buyer interest.

**Property Type & Lot Size Insights**
- Luxury condos dominate the downtown core, while single-family homes and townhouses are more common in outer districts like Jefferson Park (60630) and Beverly (60643).
- Larger lot sizes (>0.5 acres) are mostly found in suburban-like areas such as Norwood Park and Edison Park, appealing to families

**Investment & Future Projections**
-Best areas for appreciation: Hyde Park, Bronzeville, and South Loop due to upcoming infrastructure projects.
- Best for affordability: Garfield Park and Austin offer the lowest price per square foot, making them prime for entry-level buyers and investors.
  
---
## Dataset
- **Size:** 1696381 rows × 69 columns
  
---
## Methodology
1. Domain research: reviewed how Chicago real estate data is structured and which variables matter.
2. Data Cleaning:
- Handling the NaN values:
+ Checked the NaN values of all columns.
+ Dropped the columns with > 75% NaN values.
+ Dropped rows with missing unique indentifiers.
+ Examined the relationships between related variables using correlation matrix, boxplots, and scatter plots.
+ Filled missing values in related columns using group averages.
- Handling outliers:
+ Used boxplots to find extreme values in each column.
+ Replaced outliers with median values.
+ Compared boxplots before and after cleaning.
3. Exploratory analysis: an interactive Folium choropleth map of price by ZIP code.
4. Modeling: Linear, Ridge Regression, Decision Tree, Light Random Forest
5. Evaluation: R-squared and RMSE on [test set / cross-validation], feature-importance analysis.

---
## Limitations
- list_price dominates the Decision Tree, so the best score likely overstates generalization.
- Outliers were replaced with medians, which can reduce real price variation.

