# Predicting the Spectral Class of a Star
`Note: this is an ongoing project and will continue to be refined until done`

This simple machine learning project aims to predict the spectral class of a star using multiple features such as the temperature, luminosity, radius, and absolute magnitude of the astrophysical object. The spectral class or stellar classification is a way to categorize stars based on their physical properties, mainly their _temperature_ and _color_. Stars are classified under the [Morgan-Keenan System](https://en.wikipedia.org/wiki/Stellar_classification), they are classified through letters _O, B, A, F, G, K,_ and _M_, where _O_ is the hottest and _M_ is the coolest. This simple study provides essential parameters for understanding stellar behavior which can be useful for further astrophysical analysis and scientific research. 

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/3/37/Stellar_Classification_Chart.png" />
</p>

## Table of Contents
* Needed libraries
* Dataset
* Data preprocessing
* Checking assumptions
* Modeling approach
* Results and Assessment

### Needed libraries
The list below is a brief description of each of the libraries and tools I've used for processing the data.
1. **pandas**: A library used for data manipulation and analysis, especially useful for handling structured data such as DataFrames.
2. **numpy**: A fundamental package for numerical computation in Python, providing support for arrays, matrices, and mathematical functions
3. **sklearn.neighbors (KNeighborsClassifier)**: A machine learning classifier that uses the K-Nearest Neighbors algorithm for classification tasks by finding the closest data points.
4. **re**: A library for working with regular expressions, allowing for pattern matching and text manipulation.
5. **sklearn.preprocessing (StandardScaler)**: A tool to standardize features by removing the mean and scaling to unit variance, often necessary for machine learning models to perform well.
6. **sklearn.model_selection (train_test_split)**: A function that splits your dataset into training and testing subsets, ensuring fair evaluation of machine learning models.
7. **matplotlib.pyplot (plt)**: A sub-library of matplotlib that provides a MATLAB-like interface for making plots.
8. **seaborn**: A data visualization library built on top of matplotlib, providing high-level functions to create attractive and informative statistical graphics.
9. **%matplotlib inline**: A magic function specific to Jupyter notebooks that ensures that plots are displayed inline, within the notebook.
10. **sklearn.metrics (accuracy_score, confusion_matrix, classification_report)**: A module containing functions to evaluate the performance of machine learning models using metrics like Accuracy score, Confusion Matrix, Classification report.
11. **imblearn.oversampling (RandomOverSampler)**: Used for oversampling minority classes in the dataset to counter imbalanced class that affects the performance of the model to predict between classes.

### Dataset
The dataset that was used in this project is the [Astronomical Data](https://www.kaggle.com/datasets/datascientist97/astronomical-data) from _Raja Ahmed Ali Khan_. You can read the full dataset description on the link embedded which will redirect to Raja's data card. In summary, the dataset contains the astrophysical properties of each star. The dataset has a dimension of **7 columns** with **240 entries**. The table displayed below is a portion of the dataset.

| Temperature (K) | Luminosity (L/Lo) | Radius (R/Ro) | Absolute magnitude (Mv) |  Star type | Star color | Spectral Class |
|:----------: |:----------:|:------:| :--------------------:|:---------: |:---------: | :------------: |
|    3042     |   0.0005   | 0.1542 |         16.6          |      0     |     Red    |        M       |
|    2600     |   0.0003   | 0.102  |         18.7          |      0     |     Red    |        M       |
|    2800     |   0.0002   |        |        16.65          |      0     |     Red    |        M       |
|    1939     |  0.000138  | 0.103  |        20.06          |      0     |     Red    |        M       |
|    2840     |            | 0.11   |        16.98          |      0     |     Red    |        M       |

### Data preprocessing
* All variables were converted into proper data formats before assessing the number of null values per column. Columns Temperature, Luminosity, Radius, and Absolute magnitude were cleaned by filling the missing values with the mean value for each column.
* Rows with missing values on the Spectral Class, on the other hand, were dropped/removed since there are only 2 missing values. Ordinal encoding was applied to the Spectral Class column by replacing the letter values with numbers from 0 to 6, then the data format for that column was converted to numeric.
* The missing star color values were imputed using K-Nearest Neighbors. The star color imputation aimed to replace missing star color values by assessing all available features. It identifies the data points that are most similar to those with missing values based on the other features and assigns the star color of the closest match to fill in the missing star color values.
* Before splitting the data into training 80% and testing 20% sets, the predictor variables were scaled to ensure that their values were on comparable scales, improving the performance and accuracy of the regression model.

### Checking assumptions
1. _Class imbalance:_
The dataset exhibited a severe class imbalance, with the majority of stars belonging to spectral class 0. To address this imbalance, oversampling using imblearn's RandomOverSampler was used. Oversampling is creating synthetic samples by randomly replicating samples in minority classes until they reach a balanced distribution.
2. _Outlier handling:_
Several features, such as luminosity, radius, and temperature, exhibited significant outliers that could distort the KNN distance calculations.
Log transformation was applied to compress the range of these features and reduce the influence of extreme values, improving model robustness.

### Modeling approach
I focused on predicting the _spectral class_ (dependent variable) using four key features (predictors): _temperature, luminosity, radius, and absolute magnitude_. Originally, the dataset contained seven columns, but I chose these four predictors as they are the most relevant for the problem. I applied K-Nearest Neighbors model to the dataset. A KNN classifier was initialized as a model with weighted distances and the training sets were fitted into the model. The model was then used to predict y values using the `x_test` values and stored it in a `y_pred` variable. 

### Model assessment
Before Data Augmentation:

`Overall accuracy:` 81%

`Class-wise Performance:` 

* The model performed well for the majority class (spectral class 0), achieving near-perfect precision and recall.
* However, the model struggled with minority classes (especially class 1 and class 4), as the dataset contained very few instances of these classes, leading to lower recall and F1-scores for these categories. 
* The imbalanced dataset results in a model that is heavily biased toward the majority class, with poor performance in minority classes.

After Data Augmentation:

`Overall accuracy:` 95%

`Class-wise Performance:` 

* The model performed well in all classes, achieving near-perfect precision and recall.
* The oversampling mitigated the class imbalance by adding synthetic samples for minority classes, leading to more balanced predictions and fewer misclassifications.




