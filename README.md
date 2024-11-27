The ultimate goal of this project is to accurately predict the salesprice of the home. However, it is desired to see how different models perform this task. Specifically, Principal Component Analysis (PCA), K-Nearest Neighbors (KNN) applied to the PCA transformed data, K-Nearest Neighbors (KNN) without PCA, and Linear Discriminant Analysis (LDA). 

The first part this presentation is a data analysis of the 2020 AMES Housing Data. The data is downloaded and analyzed using Python on Kaggle.
Next, a small portion of the data is displayed in order to understand what the data looks like. The data categories or types are displayed with the data type it corresponds to (int, float, object, etc) and indication of missing information (null values). The number of missing values or entries in the data is indicated per category. Basic statistics for 25 of the categories of the data is displayed.
A histogram of the saleprice of the homes is displayed.
A heat map of the covarinace matrix is shown.
The top 9 parameters associated with the salesprice are shown with their correlation coefficient.
Finally, the home salesprice is plotted against the top 5 correlated parameters in addition to total square footage.
