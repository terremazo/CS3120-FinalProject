### Project Goals

The ultimate goal of this project is to accurately predict the salesprice of the home. However, it is desired to see how different models perform this task. Specifically, Principal Component Analysis (PCA), K-Nearest Neighbors (KNN) applied to the PCA transformed data, K-Nearest Neighbors (KNN) without PCA, and Linear Discriminant Analysis (LDA) are the models that will be used to compare their performance. 

### Methodology
Linear Regression analysis was used to provide a baseline of performance for comparison.

PCA and LDA were utilized because they both take advantage of a covariance matrix of the data.
It was desired to investigate how a covariance matrix was used by the models.

KNN was utlized to see if and how much performance improved with or without the PCA model.
PCA was used with n_components = 3.
The KNN model used n_neighbors = 5.

LDA is normally a classification model being used in this instance as if it were performing regression.
The LDA model "binned" the data into three categories: 0-low price, 1-medium price, 2- high price.
These are the categories that the LDA model used as targets.

The data was cleaned and missing data ws imputed with the mean or mode depending which was appropriate.

### Data Analysis

The first part this presentation is a data analysis of the 2020 AMES Housing Data. The data is downloaded and analyzed using Python on Kaggle.
Next, a small portion of the data is displayed in order to understand what the data looks like. The data categories or types are displayed with the data type it corresponds to (int, float, object, etc) and indication of missing information (null values). The number of missing values or entries in the data is indicated per category. Basic statistics for 25 of the categories of the data is displayed.
A histogram of the saleprice of the homes is displayed.
A heat map of the covarinace matrix is shown.
The top 9 parameters associated with the salesprice are shown with their correlation coefficient.
Finally, the home salesprice is plotted against the top 5 correlated parameters in addition to total square footage.

The data indicates that the salesprice is most strongly correlated with the overall quality of the home, followed by the total square footage (the combined footage of the general living area above ground and basement square footage), the number of cars the garage can hold and the individual section square footage of areas of the house. The correlation coefficient of the top six parameters is shown below.

### Comparison of Results

#### Correlation Analysis

**Features Highly Correlated with SalePrice:**
1. `OverallQual` (ρ = 0.79): Indicates that higher overall quality significantly increases the sale price.
2. `TotalSquareFootage` (ρ = 0.78): Combines basement and above-ground square footage; highly indicative of home value.
3. `GrLivArea` (ρ = 0.71): Living area above ground, another critical determinant of house price.
4. `GarageCars` (ρ = 0.64): The number of cars the garage holds contributes strongly to price.
5. `GarageArea` (ρ = 0.62): Size of the garage further correlates with price, but less than the number of cars.
6. `TotalBsmtSF` (ρ = 0.61): Basement area correlates with price, particularly in areas where basements are finished.

---

#### Model Performance Comparison

**Linear Regression Results:**
- **RMSE**: 39,763.30
- **R² Score**: 0.79
- **Analysis**:
  - As a baseline model, Linear Regression captures linear relationships between features and target effectively but lacks the flexibility to handle non-linear interactions.
  - Strong correlations like `OverallQual` and `TotalSquareFootage` dominate its performance.

**PCA + KNN Results:**
- **RMSE**: 34,002.03
- **R² Score**: 0.85
- **Analysis**:
  - PCA reduces dimensionality to 3 principal components while retaining essential variance, improving the interpretability and efficiency of KNN.
  - The reduction mitigates overfitting and highlights underlying feature interactions effectively.

**KNN Without PCA Results:**
- **RMSE**: 34,699.63
- **R² Score**: 0.84
- **Analysis**:
  - While KNN captures non-linear relationships, its performance is slightly worse than PCA + KNN due to the curse of dimensionality.
  - Without PCA, KNN requires more computational resources and may overfit in high-dimensional spaces.

**LDA + KNN Results:**
- **RMSE**: 33,836.81
- **R² Score**: 0.85
- **Analysis**:
  - LDA transforms features to maximize class separability among binned price categories.
  - This transformation aids KNN in focusing on the most relevant feature differences, achieving the best RMSE and comparable R² to PCA + KNN.

---

### Similarities
- All advanced models (PCA + KNN, KNN without PCA, LDA + KNN) outperform Linear Regression, highlighting the importance of non-linear modeling for this dataset.
- `OverallQual` and `TotalSquareFootage` consistently emerge as critical predictors across models.
- PCA and LDA both improve KNN's performance by reducing noise and focusing on essential feature interactions.

---

### Differences
1. **Dimensionality Reduction**:
   - PCA retains general variance across all features, whereas LDA emphasizes class-specific separability.
   - PCA is better suited for continuous targets, while LDA excels in categorical/binned transformations.

2. **Performance**:
   - LDA + KNN achieves the lowest RMSE, likely due to its optimization for price-based separability.
   - PCA + KNN slightly outperforms KNN without PCA, confirming the value of dimensionality reduction.

3. **Linear Regression Limitations**:
   - Linear Regression fails to capture non-linear relationships, resulting in the highest RMSE and lowest R².
   - This limitation underscores the need for more sophisticated models for complex datasets like Ames Housing.

---

### Conclusion
- **Best Model**: LDA + KNN delivers the most accurate predictions (lowest RMSE), suggesting price categorization enhances predictive power.
- **Feature Insights**:
  - Combining features like `TotalBsmtSF` and `GrLivArea` into `TotalSquareFootage` significantly boosts predictive accuracy.
- **Future Considerations**:
  - Experiment with ensemble methods (e.g., Random Forest or Gradient Boosting) to compare with KNN-based approaches.
  - Explore further feature engineering and interaction effects for nuanced insights.

