## 1. Imputing Missing Data
1. Using median/mean/mode (not accurate, can face logical issues if there are relationships between column with missing data and other data)

2. Drop missing data (can lead to bias)

3. Using ML
	1. KNN (find K most similar rows and average)
	2. Deep Learning (build ML model to impute data for ML model)
		* Works well for categorical data but complicated
	3. Regression
		* Find linear/non linear relationship between missing feature and other features
		* Can use MICE (Multiple Imputations by Chained Equations)

	4. Collect more data

## 2. Dealing with unbalanced data
Methods to balance data:
1. Random Oversampling  - duplicate samples from minority class
2. Random Undersampling
3. SMOTE

Adjust Threshold according to cost of FN vs FP