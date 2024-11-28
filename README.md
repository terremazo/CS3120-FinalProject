The ultimate goal of this project is to accurately predict the salesprice of the home. However, it is desired to see how different models perform this task. Specifically, Principal Component Analysis (PCA), K-Nearest Neighbors (KNN) applied to the PCA transformed data, K-Nearest Neighbors (KNN) without PCA, and Linear Discriminant Analysis (LDA) are the models that will be used to compare their performance. 

Data Analysis
The first part this presentation is a data analysis of the 2020 AMES Housing Data. The data is downloaded and analyzed using Python on Kaggle.
Next, a small portion of the data is displayed in order to understand what the data looks like. The data categories or types are displayed with the data type it corresponds to (int, float, object, etc) and indication of missing information (null values). The number of missing values or entries in the data is indicated per category. Basic statistics for 25 of the categories of the data is displayed.
A histogram of the saleprice of the homes is displayed.
A heat map of the covarinace matrix is shown.
The top 9 parameters associated with the salesprice are shown with their correlation coefficient.
Finally, the home salesprice is plotted against the top 5 correlated parameters in addition to total square footage.

Model Performance 
Comparison of Results
Key Observations

Feature Correlation with SalePrice
Top Correlated Features:
OverallQual and TotalSquareFootage show the strongest correlation with SalePrice, indicating their critical role in determining house prices.
Other features like GrLivArea, GarageCars, and GarageArea are moderately correlated, reflecting their importance.


Model Comparisons

Linear Regression:
RMSE: 39,763.30
R² Score: 0.79
Strengths: A simple and interpretable baseline model, but it assumes linear relationships between features and the target, which may not capture complex interactions.
PCA + KNN:
RMSE: 34,002.03
R² Score: 0.85
PCA effectively reduces dimensionality, preserving significant variance. Combining this with KNN provides flexibility in modeling non-linear relationships, leading to better performance than linear regression.
KNN Without PCA:
RMSE: 34,699.63
R² Score: 0.84
Shows similar performance to PCA + KNN but slightly less efficient due to potential high-dimensionality effects. PCA helps mitigate the curse of dimensionality, making KNN more robust.
LDA + KNN:
RMSE: 33,836.81
R² Score: 0.85
LDA maximizes separability between different price ranges (binned categories). The resulting features work well with KNN, achieving the best RMSE and comparable R² to PCA + KNN.

Similarities
Advanced Techniques (PCA + KNN, KNN Without PCA, and LDA + KNN):
All outperform Linear Regression, demonstrating the need for non-linear modeling in capturing housing price determinants.
PCA and LDA both enhance KNN's ability to handle complex relationships, but through different mechanisms (variance preservation vs. class separability).

Differences
Dimensionality Reduction:
PCA captures overall variance in features, leading to general improvements across predictions.
LDA focuses on price categories, optimizing for class-specific feature differences.
Performance:
LDA + KNN achieves the lowest RMSE, showing its strength in price-category-based modeling.
Linear Regression has the weakest performance due to its inability to model non-linear relationships.
Complexity vs. Interpretability:
Linear Regression provides the most interpretable results but at the cost of accuracy.
PCA and LDA introduce complexity in interpreting individual feature contributions but enhance model performance.

Conclusion
Best Model: LDA + KNN due to its optimal RMSE and R², leveraging the advantages of feature separability in price ranges.
Insights:
Feature engineering (e.g., combining TotalBsmtSF and GrLivArea) significantly improves model accuracy.
Non-linear methods (KNN with PCA/LDA) are more suited for this dataset compared to linear models.
