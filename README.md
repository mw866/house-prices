# House Prices

By Chris M Wang 

## Usage

View the Zeppelin notebook here: https://www.zeppelinhub.com/viewer/notebooks/aHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL213ODY2L2hvdXNlLXByaWNlcy9tYXN0ZXIvbm90ZS5qc29u



## Part 1: Take the raw data, propose an initial feature shaping  approach, select a machine learning algorithm available in Spark (or TensorFlow), construct an experiment and analyze the output

### Initial feature shaping
Since there are a mix sets of numerial (integer) and categorical (string) features, the following feature shaping techniques are identified:
* String-Indexing
* One-Hot-Encoding

Also, the features needs to assembled into vectors before feeding into the model by using:

* VectorAssembler

All the above-mentioned feature shaping techniques are meet the minimal requirement for the linear regression to function properly.

### Machine Learning Algorithm Selection
As the label (`SalePrice`) is continuous, an regression algorithm is required. 
The Linear Regression is selected for its speed and simplicity.

### Analysis

The evaluation achieves a R2 of  <u>0.9063243754152835</u>. It definitely can be improved.

## Part 2: Using analysis from Part 1, construct and justify 5  different “classes” of features engineering changes to the  data. A “class” of a change is, for example, normalization. Normalizing all of the original numerical feature vectors  would be one class of feature engineering change. (any operation that is repeated on multiple columns is a class)

1. **One-Hot-Encoding** : Refer to Part 1
2. **String-Indexing** : Refer to Part 1
3. **Vector-Assembly** : Refer to Part 1
4. **Normalization**: The numerical features have very different semantic meaning with high range of mean and variance. Normalizations help to equalize the influence of the features to the model for better performance of the model. 
5. **PCA**: The original data has ~80 columns. By reducing the dimensionality of the data, PCA helps to improve the performance of the model.


## Part 3: Using data uncovered from your analysis, explain which segments of the data benefit most from the use of feature engineering from Part 1 and Part 2.

Below is how the evaluation metric R2 improves after applying the feature engineering techniques.


| Feature Engineering Techniques | R2 Score            |
| ------------------------------ | ------------------- |
| 1+2+3                          | 0.9063243754152835  |
| 1+2+3+4                        | 0.6399090091007191  |
| 1+2+3+4+5                      | 0.22497359098890068 |



The categorical (string) features benefit the most from the (1) One-Hot-Encoding (2) String-Indexing .

The numerical (integer) features benefits the most from the (4) Normalization (5) PCA



## Reference
* Kaggle Competition page: https://www.kaggle.com/c/house-prices-advanced-regression-techniques
* Statistical and Mathematical Functions with DataFrames in Apache Spark: https://databricks.com/blog/2015/06/02/statistical-and-mathematical-functions-with-dataframes-in-spark.html

