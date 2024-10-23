# Predicting the Spectral Class of a Star

This simple machine learning project aims to predict the spectral class of a star using multiple features such as the temperature, luminosity, radius, and absolute magnitude of the astrophysical object. The spectral class or stellar classification is a way to categorize stars based on their physical properties, mainly their _temperature_ and _color_. Stars are classified under the [Morgan-Keenan System](https://en.wikipedia.org/wiki/Stellar_classification), they are classified through letters _O, B, A, F, G, K,_ and _M_, where _O_ is the hottest and _M_ is the coolest. This simple study provides essential parameters for understanding stellar behavior which can be useful for further astrophysical analysis and scientific research. 

## Table of Contents
* Needed libraries
* Dataset
* Data preprocessing
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
10. **sklearn.linear_model (linear_model)**: Provides various linear models for regression and classification tasks, such as `LinearRegression` or `LogisticRegression`.
11. **sklearn.metrics (mean_absolute_error, root_mean_squared_error, r2_score)**: A module containing functions to evaluate the performance of machine learning models using metrics like Mean Absolute Error (MAE), Root Mean Squared Error (RMSE), and the R² score.

### Dataset
The dataset that was used in this project is the [Astronomical Data](https://www.kaggle.com/datasets/datascientist97/astronomical-data) from _Raja Ahmed Ali Khan_. You can read the full dataset description on the link embedded which will redirect to Raja's data card. In summary, the dataset contains the astrophysical properties of each star. The dataset has a dimension of **7 columns** with **240 entries**. The table displayed below is a portion of the dataset.

| Temperature | Luminosity | Radius | Absolute magnitude Mv |  Star type | Star color | Spectral Class |
|:----------: |:----------:|:------:| :--------------------:|:---------: |:---------: | :------------: |
|    3042     |   0.0005   | 0.1542 |         16.6          |      0     |     Red    |        M       |
|    2600     |   0.0003   | 0.102  |         18.7          |      0     |     Red    |        M       |
|    2800     |   0.0002   |        |        16.65          |      0     |     Red    |        M       |
|    1939     |  0.000138  | 0.103  |        20.06          |      0     |     Red    |        M       |
|    2840     |            | 0.11   |        16.98          |      0     |     Red    |        M       |



