# Machine Learning & Data Science Documentation

This document is a practical reference for the Python libraries and functions that are commonly useful when solving data science and machine learning tasks. It is intentionally written as a documentation-style guide rather than a step-by-step exam solution.

The goal is to help a learner understand what tools exist, what they are generally used for, and which functions are worth learning when working on realistic ML/data-science problems.

## 1. Core libraries

### pandas
Use pandas for tabular data manipulation, exploratory analysis, and preprocessing.

Common objects and functions:

- `pd.read_csv(...)` – load tabular data from CSV files
- `pd.read_excel(...)` – load Excel files
- `pd.DataFrame(...)` – create a DataFrame manually
- `df.head()`, `df.tail()` – inspect rows
- `df.info()` – dataset structure and dtypes
- `df.describe()` – summary statistics
- `df.shape` – number of rows and columns
- `df.columns` – column names
- `df.dtypes` – column data types
- `df.isna()`, `df.isnull()` – detect missing data
- `df.dropna()`, `df.fillna(...)` – handle missing values
- `df.astype(...)` – convert data types
- `df.copy()` – duplicate a DataFrame
- `df.sort_values(...)` – sort rows
- `df.rename(columns={...})` – rename columns
- `df.drop(columns=[...])` – remove columns
- `df.select_dtypes(...)` – filter by numeric/categorical dtype
- `df.duplicated()`, `df.drop_duplicates()` – detect and remove duplicates
- `df.merge(...)`, `df.join(...)` – combine tables
- `df.groupby(...)` – aggregate by categories/groups
- `df.pivot_table(...)` – summarize by pivoting
- `df.apply(...)`, `df.map(...)` – transform values
- `df.reset_index()` – reset index after operations

### NumPy
Use NumPy for numerical arrays, statistics, and efficient vectorized operations.

Common functions:

- `np.array(...)` – create arrays
- `np.mean(...)`, `np.median(...)`, `np.std(...)`, `np.var(...)` – descriptive statistics
- `np.sum(...)`, `np.max(...)`, `np.min(...)` – aggregate values
- `np.unique(...)` – unique values
- `np.where(...)` – conditional selection
- `np.random.seed(...)` – control random generation
- `np.corrcoef(...)` – correlation matrix
- `np.clip(...)` – bound values to a range
- `np.log(...)`, `np.sqrt(...)` – mathematical transforms

### Matplotlib and Seaborn
Use these libraries for plotting and visual exploration.

Common plotting functions:

- `plt.figure()`, `plt.subplots()` – create plots
- `plt.plot(...)` – line plots
- `plt.hist(...)` – histogram
- `plt.boxplot(...)` – boxplots
- `plt.scatter(...)` – scatter plots
- `plt.bar(...)`, `plt.barh(...)` – bar charts
- `sns.histplot(...)` – histogram with seaborn
- `sns.boxplot(...)` – boxplot
- `sns.scatterplot(...)` – scatter plot
- `sns.countplot(...)` – count bar plot
- `sns.heatmap(...)` – correlation or matrix visualizations
- `sns.pairplot(...)` – quick multivariate visualization
- `sns.barplot(...)`, `sns.violinplot(...)` – grouped comparisons

### scikit-learn
Use scikit-learn for preprocessing, modeling, evaluation, and validation.

#### Data splitting and validation

- `train_test_split(...)` – split data into train and test sets
- `cross_val_score(...)` – cross-validation scoring
- `KFold`, `StratifiedKFold` – cross-validation strategies
- `GridSearchCV` – systematic hyperparameter tuning
- `RandomizedSearchCV` – random hyperparameter search

#### Preprocessing

- `SimpleImputer` – fill missing values
- `StandardScaler` – scale numeric features
- `MinMaxScaler` – normalize to a range
- `OneHotEncoder` – encode categorical features
- `OrdinalEncoder` – ordinal encoding for ordered categories
- `ColumnTransformer` – apply different preprocessors to columns
- `Pipeline` – chain preprocessing and model steps

#### Models

Regression:

- `LinearRegression`
- `Ridge`
- `Lasso`
- `RandomForestRegressor`
- `GradientBoostingRegressor`

Classification:

- `LogisticRegression`
- `DecisionTreeClassifier`
- `RandomForestClassifier`
- `GradientBoostingClassifier`
- `KNeighborsClassifier`
- `SVC`
- `XGBClassifier` (when available)

#### Model evaluation

- `accuracy_score(...)`
- `precision_score(...)`
- `recall_score(...)`
- `f1_score(...)`
- `roc_auc_score(...)`
- `classification_report(...)`
- `confusion_matrix(...)`
- `mean_squared_error(...)`
- `mean_absolute_error(...)`
- `r2_score(...)`
- `mean_squared_log_error(...)` (for skewed target distributions)

#### Prediction and interpretation

- `model.fit(X, y)` – train the model
- `model.predict(X)` – make predictions
- `model.predict_proba(X)` – class probabilities
- `model.score(X, y)` – accuracy or R²-like score depending on model
- `feature_importances_` – tree-based feature importance
- `coef_` – linear model coefficients
- `permutation_importance(...)` – model-agnostic importance testing

### scipy
Useful for statistics and scientific calculations.

Common functions:

- `scipy.stats.skew(...)` – skewness of a distribution
- `scipy.stats.kurtosis(...)` – kurtosis
- `scipy.stats.zscore(...)` – z-score normalization
- `scipy.stats.mode(...)` – most frequent value

## 2. Data loading and inspection

These are foundational steps in any practical ML/data science task.

Typical tasks:

- read a CSV file into a DataFrame
- inspect the first rows and column names
- check dtypes and missingness
- understand shape and row counts
- identify likely target and feature columns

Useful functions:

- `pd.read_csv()`
- `df.head()`
- `df.tail()`
- `df.shape`
- `df.columns`
- `df.info()`
- `df.describe()`
- `df.isna().sum()`
- `df.nunique()`
- `df.value_counts()`

Typical questions to answer:

- How many rows and columns exist?
- Which columns are numeric, categorical, or textual?
- Are there missing values?
- Are there obvious outliers or suspicious values?
- Is there a clear prediction target?

## 3. Data cleaning and preprocessing

This is where much of the real-world work happens.

### Missing values

Common patterns:

- remove rows with missing values when the data is low-quality or sparse
- fill with a statistic such as median or mode
- use a model-aware imputer for pipelines

Useful tools:

- `df.isna().sum()`
- `df.dropna()`
- `df.fillna(value)`
- `df.fillna(df.mean())`
- `df.fillna(df.median())`
- `SimpleImputer`

### Duplicates and invalid values

Useful tools:

- `df.duplicated()`
- `df.drop_duplicates()`
- `df.replace(...)`
- `df.loc[...]` for targeted cleaning
- `df.astype(...)` to correct types

### Categorical data

Common operations:

- check unique values with `df[col].unique()`
- inspect category distributions with `value_counts()`
- encode categories for modeling with `OneHotEncoder` or `OrdinalEncoder`
- convert date strings into date-like values if necessary

### Numeric data

Common operations:

- handle skewed distributions with log transforms
- remove unrealistic outliers when justified
- scale features for algorithms sensitive to magnitude

Useful tools:

- `np.log1p()`
- `StandardScaler`
- `MinMaxScaler`
- `df.clip(lower=..., upper=...)`

## 4. Exploratory data analysis (EDA)

EDA is about understanding the dataset before modeling.

Key ideas:

- understand variable distributions
- detect relationships among features
- check target imbalance or skew
- identify possible leakage or unusable columns

Useful operations:

- `df.describe()`
- `df.groupby(...).mean()`
- `df.corr()`
- `df['col'].value_counts()`
- `df['col'].plot.hist()`
- `df.plot.scatter(...)`
- `sns.histplot(...)`
- `sns.boxplot(...)`
- `sns.countplot(...)`
- `sns.heatmap(df.corr())`
- `sns.pairplot(df)`

Questions EDA often answers:

- Is the target balanced or imbalanced?
- Which features appear correlated with the target?
- Are there strong relationships between features?
- Are there outliers or unusual patterns?

## 5. Feature and target preparation

Before training a model, data must usually be split into feature variables and target variables.

Typical patterns:

- `X = df[feature_columns]`
- `y = df[target_column]`
- `X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)`

For classification tasks, also check the target distribution:

- `y.value_counts(normalize=True)`
- `y_train.value_counts(normalize=True)`

If labels are imbalanced, consider class weighting or appropriate evaluation metrics.

Useful tools:

- `train_test_split`
- `ColumnTransformer`
- `Pipeline`
- `OneHotEncoder`
- `StandardScaler`

## 6. Modeling workflow

The goal is to build a simple and interpretable pipeline that can be trained and evaluated reliably.

Common pattern:

```python
from sklearn.compose import ColumnTransformer
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import OneHotEncoder, StandardScaler
from sklearn.impute import SimpleImputer
from sklearn.ensemble import RandomForestClassifier

numeric_features = X.select_dtypes(include=['number']).columns
categorical_features = X.select_dtypes(exclude=['number']).columns

numeric_transformer = Pipeline([
    ('imputer', SimpleImputer(strategy='median')),
    ('scaler', StandardScaler())
])

categorical_transformer = Pipeline([
    ('imputer', SimpleImputer(strategy='most_frequent')),
    ('onehot', OneHotEncoder(handle_unknown='ignore'))
])

preprocessor = ColumnTransformer([
    ('num', numeric_transformer, numeric_features),
    ('cat', categorical_transformer, categorical_features)
])

model = Pipeline([
    ('preprocessor', preprocessor),
    ('classifier', RandomForestClassifier(random_state=42))
])

model.fit(X_train, y_train)
```

This pattern is useful because it handles numeric and categorical features together and keeps the workflow reproducible.

## 7. Evaluation metrics

Different tasks require different metrics.

### Classification metrics

- `accuracy_score` – overall correct predictions
- `precision_score` – proportion of predicted positives that are actually positive
- `recall_score` – proportion of actual positives captured
- `f1_score` – balance of precision and recall
- `roc_auc_score` – ranking quality for binary classification
- `classification_report` – summary of precision, recall, and F1
- `confusion_matrix` – matrix of actual vs predicted labels

### Regression metrics

- `mean_absolute_error` – average absolute error
- `mean_squared_error` – squared error loss
- `r2_score` – explained variance relative to baseline

### Validation strategy

- `train_test_split` for a single holdout validation
- `cross_val_score` for more stable estimates
- `GridSearchCV` for tuning model parameters

## 8. Prediction and interpretation

Once a model is trained, it is typically used to generate predictions for unseen data.

Common operations:

- `y_pred = model.predict(X_test)`
- `y_proba = model.predict_proba(X_test)`
- `model.predict(new_data)` for new observations
- `feature_importances_` on tree-based models
- `coef_` on linear models
- `permutation_importance` for feature-level interpretation

Interpretation questions:

- Which features most strongly influence the prediction?
- How confident are the predictions?
- Are there systematic errors across subgroups?
- Is the model likely to generalize beyond the training data?

## 9. Common ML/data-science patterns

These are recurring patterns in beginner-to-intermediate ML tasks.

### Pattern: classification problem

- inspect the target column
- check target balance
- split into train/test
- preprocess numeric and categorical features
- train a baseline model
- evaluate using accuracy, F1, recall/precision, and confusion matrix
- compare several models if needed

### Pattern: regression problem

- inspect target distribution
- split data into train/test
- preprocess features
- train a baseline regression model
- evaluate with MAE, MSE, and R²
- check for outliers or skewed target distributions

### Pattern: data quality problem

- check missing values
- inspect duplicates and invalid records
- decide whether to impute, drop, or transform variables
- ensure the target is not accidentally leaked by a predictor

### Pattern: model tuning problem

- start with a simple baseline
- compare at least a few candidate models
- use cross-validation to reduce variance
- tune a few key hyperparameters
- prefer simple models when performance is similar

## 10. Practical tips for learning

Focus on understanding the purpose of each library and function rather than memorizing exact usage without context.

A useful mental model is:

- pandas for data handling
- NumPy for numeric operations
- Matplotlib/Seaborn for visual exploration
- scikit-learn for modeling and evaluation

When solving real tasks, start with:

1. Load the data
2. Inspect structure and quality
3. Understand the target and feature columns
4. Clean and transform data appropriately
5. Train a simple baseline model
6. Evaluate carefully
7. Iterate with better preprocessing or a stronger model only if needed

## 11. Useful beginner checklist

Before submitting a solution to a data science or ML problem, check:

- data is loaded correctly
- missing values are handled intentionally
- categorical variables are encoded appropriately
- target data is prepared correctly
- train/test split is done properly
- evaluation metrics fit the task type
- model assumptions and limitations are understood
- results are interpreted, not just printed

## 12. Summary

This is not a step-by-step exam answer sheet. It is a practical reference to the functions and concepts that are useful in machine learning and data science work. Use it as a mental map of the tools available to you, not as a script to reproduce in every assignment.

The most valuable learning habit is to connect the question to the right tool:

- data inspection → pandas
- numerical calculations → NumPy
- visualization → Matplotlib / Seaborn
- modeling → scikit-learn
- evaluation → scikit-learn metrics and validation tools
