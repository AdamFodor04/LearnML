You are an expert teacher and exam/task designer specializing in **Machine Learning and Data Science**.

Create a practical programming/data science exam assignment for a student who has beginner to lower-intermediate knowledge of Python, Pandas, data analysis, and machine learning.

The exam should be designed so that the student has to work with a provided dataset and complete a realistic end-to-end data science / machine learning workflow.

The assignment should be **dataset-agnostic**. Do not assume a specific dataset such as Titanic, House Prices, Iris, MNIST, or another well-known dataset. Instead, define the required characteristics of the dataset and refer to generic concepts such as the target variable, numerical features, categorical features, training data, and test data.

The student should receive the dataset separately, for example as a CSV file.

The exam should be structured into numbered requirements and divided into logical sections such as:

1. Data loading and inspection
2. Data cleaning and preprocessing
3. Exploratory Data Analysis
4. Feature and target preparation
5. Model training
6. Model evaluation
7. Prediction and interpretation

The requirements should be concrete and objectively assessable. Each task should specify exactly what the student must implement or calculate, including required analyses, transformations, metrics, visualizations, and expected behavior.

The difficulty should be appropriate for someone who has completed introductory **Pandas and Machine Learning** material and is beginning to learn **Deep Learning**.

The exam should primarily test practical understanding rather than memorization.

---

### Dataset requirements

Define the characteristics that the provided dataset must satisfy.

Depending on the exam, specify requirements such as:

- tabular data
- numerical features
- categorical features where appropriate
- missing values
- a clearly defined target variable
- sufficient observations for a train/test split
- either a continuous target for regression or a categorical target for classification

Do not specify the actual dataset or its column names.

---

### Dataset discovery and selection (mandatory)

Before generating the exam, search **Kaggle for a real dataset** that is suitable for the student's current skill level and the requirements of the assignment.

Do not invent a dataset, dataset title, column names, statistics, download link, or source. Verify that the selected dataset actually exists and that its contents match the proposed exam.

#### Dataset selection criteria

1. Find a dataset hosted on Kaggle that is publicly accessible and suitable for practical data analysis and machine learning.
2. Prefer datasets that can be downloaded as a CSV file or a small collection of CSV files. Avoid datasets that require complicated API authentication, paid access, extensive preprocessing, or substantial computing resources.
3. Select a dataset with sufficient observations and meaningful features to support exploratory data analysis, visualization, preprocessing, model training, and evaluation.
4. Ensure that the dataset has a clearly identifiable prediction target suitable for either regression or classification.
5. Prefer datasets containing a mixture of numerical and categorical features, with enough complexity to practice data cleaning and preprocessing.
6. Prefer datasets that contain some missing values or other realistic data-quality issues, provided these can be handled at a beginner level. Do not require missing values if the dataset is otherwise suitable.
7. Avoid datasets that are excessively simple, artificially clean, predominantly text-based, or dependent on advanced domain knowledge.
8. Prefer datasets that can be used with the libraries the student is likely to know: Pandas, NumPy, Matplotlib, Seaborn, and scikit-learn.
9. Select a dataset that can be processed on a typical personal computer without a GPU.
10. Prefer a dataset the student has not already used in a previous practice exam, when information about previous datasets is available.

#### Dataset verification

Before writing the exam:

1. Open the actual Kaggle dataset page and verify its title, publisher or uploader, description, and available files.
2. Confirm the actual column names, approximate dataset size, and target variable by inspecting the available documentation, data preview, or dataset files where accessible.
3. Verify that the target variable is appropriate for the proposed regression or classification task.
4. Check for data leakage risks, such as features that directly reveal the target, identifiers that should not be treated as predictive features, or columns containing information unavailable at prediction time.
5. Check the dataset's stated license or usage restrictions where available. Do not assume that every Kaggle dataset is unrestricted.
6. If the dataset cannot be inspected sufficiently to verify its suitability, select another dataset rather than inventing details.
7. If the dataset requires a Kaggle account or acceptance of competition rules to download, explicitly mention this requirement.

#### Include the selected dataset in the exam

At the beginning of the generated exam, include a dedicated **Dataset description** section containing:

- **Dataset name:** the exact title shown on Kaggle.
- **Kaggle source:** a direct link to the dataset page.
- **Download instructions:** explain how to download the dataset and identify the relevant CSV file or files.
- **Dataset size:** the verified number of rows and columns, or clearly labeled approximate figures if the exact size cannot be confirmed.
- **Prediction task:** state whether the assignment is a regression or classification problem.
- **Target variable:** give the actual column name and explain what it represents.
- **Feature overview:** identify the relevant numerical and categorical columns using their real names.
- **Data-quality considerations:** mention verified missing values, duplicates, unusual values, or other relevant issues, if present.
- **Prerequisites:** list the Python libraries and any additional setup needed to complete the assignment.

The dataset must be the actual dataset used throughout the exam. Every task involving columns, the target, data types, visualizations, preprocessing, modeling, or prediction must be consistent with the verified dataset.

#### Adapt the exam to the selected data

Do not select a dataset after writing a generic exam and simply insert its name. Instead, **select and inspect the dataset first, then tailor the exam requirements to its actual structure**.

For example:

- If the target is continuous, create a regression assignment.
- If the target is categorical, create a classification assignment.
- If the dataset contains numerical and categorical predictors, include suitable preprocessing tasks for both.
- If there are missing values, require the student to investigate and handle them.
- If the dataset has an imbalanced target, include appropriate class-distribution analysis and evaluation metrics.
- If a proposed task is not applicable to the selected dataset, replace it with a relevant task of comparable difficulty.

Do not force every possible ML/DS technique into every exam. Choose requirements that are meaningful for the selected dataset and appropriate for the student's current knowledge.

#### Output and source integrity

Include the direct Kaggle link in the final exam. Cite any additional external sources used to verify the dataset or its documentation.

Do not fabricate dataset properties or claim to have inspected files that were not accessible. Clearly distinguish verified facts from estimates.

If Kaggle is inaccessible or no suitable dataset can be verified, state this limitation and ask for permission to use an alternative source. Do not silently substitute a fictional dataset.

The final result must be a **complete, self-contained, dataset-specific practical exam**, with all numbered tasks adapted to the real data. The student should be able to download the dataset and begin working without having to invent a target variable, guess column names, or search for a different dataset.

### 1. Data loading and inspection

Require the student to:

- load the provided dataset using Pandas
- inspect the first and last rows
- determine the number of rows and columns
- inspect column names and data types
- generate appropriate descriptive statistics
- identify missing values
- determine the distribution of the target variable
- identify potentially irrelevant or problematic columns

Use concrete requirements and specify what information should be produced.

---

### 2. Data cleaning and preprocessing

Require the student to:

- identify missing values
- choose and apply an appropriate strategy for handling missing values
- detect obviously invalid values where applicable
- handle categorical variables appropriately
- handle numerical variables appropriately
- remove or transform unsuitable columns when justified
- verify that the resulting dataset is suitable for machine learning

Do not prescribe every preprocessing decision. Require the student to justify important choices.

---

### 3. Exploratory Data Analysis

Require the student to perform meaningful exploratory analysis.

Include requirements such as:

- calculate appropriate descriptive statistics
- investigate relationships between important features and the target
- compare relevant groups
- identify possible correlations or patterns
- create multiple appropriate visualizations
- explain the main observations from the visualizations

Require the student to choose appropriate visualization types rather than prescribing every plot.

---

### 4. Feature and target preparation

Require the student to:

- clearly identify the feature matrix `X`
- clearly identify the target `y`
- select an appropriate subset of features
- explain why the selected features are useful
- split the dataset into training and testing subsets
- use a reproducible random state
- use stratification when appropriate for classification
- apply feature scaling when appropriate

Ensure that the instructions make it clear that preprocessing must not leak information from the test set into the training process.

---

### 5. Machine learning model

Create an appropriate modeling task based on the provided dataset.

For a regression dataset, require a regression model.

For a classification dataset, require a classification model.

Require the student to:

- select an appropriate algorithm from those covered in the course
- train the model using the training data
- generate predictions for the test data
- avoid using the test set for model training

For a more advanced version of the exam, require the student to train and compare at least two different models.

Do not provide the exact solution or implementation code.

---

### 6. Model evaluation

Require evaluation using metrics appropriate for the problem.

For regression, possible metrics include:

- MAE
- MSE
- RMSE
- R²

For classification, possible metrics include:

- accuracy
- precision
- recall
- F1-score
- confusion matrix

Require the student to:

- calculate the relevant metrics
- present the results clearly
- compare models where multiple models are used
- explain what the metrics mean
- identify potential weaknesses of the evaluation

Do not require metrics that are inappropriate for the problem type.

---

### 7. Visualization and interpretation

Require the student to create visualizations that help evaluate or interpret the model.

Examples may include:

- actual vs. predicted values for regression
- confusion matrix for classification
- feature importance
- prediction probability distributions
- residual analysis
- training/validation curves where applicable

Require the student to explain what the visualization shows.

---

### 8. Prediction on new data

Provide a generic new observation or require the student to construct one.

Require the student to:

- apply the same preprocessing used during training
- generate a prediction
- report the predicted value or class
- report a probability/confidence value where the model supports it
- briefly interpret the prediction

---

### 9. Short written analysis

Require a short final analysis containing questions such as:

- Which features appear to be most important?
- Which model performed best and why?
- What limitations does the model have?
- Is there evidence of overfitting or underfitting?
- How could the model be improved?
- What additional data could improve the prediction?
- Which assumptions or preprocessing decisions could affect the result?

The answers should require reasoning based on the student's actual results rather than generic theoretical definitions.

---

### Difficulty and progression

The exam should be appropriate for the student's current level.

Do not require advanced techniques that have not been introduced in the course, such as:

- transformers
- advanced CNN architectures
- complex hyperparameter optimization
- advanced feature engineering
- mathematical derivations of optimization algorithms
- advanced statistical inference

unless explicitly requested.

The exam should instead emphasize:

- Python
- Pandas
- NumPy
- data cleaning
- exploratory data analysis
- visualization
- train/test splitting
- preprocessing
- basic supervised machine learning
- model evaluation
- interpretation of results

If the exam is intended as a later progression after an introductory deep learning course, it may additionally include:

- neural networks
- validation data
- training history
- loss curves
- overfitting
- image preprocessing
- basic neural-network evaluation

---

### Exam style

Write the exam in **Hungarian**.

Use a formal, concise educational style similar to a real Hungarian programming/data science exam sheet.

Number every requirement sequentially.

Divide the assignment into clearly labeled sections.

Use imperative wording such as:

- „Töltse be…”
- „Határozza meg…”
- „Vizsgálja meg…”
- „Készítsen…”
- „Számítsa ki…”
- „Tanítson…”
- „Értékelje…”
- „Hasonlítsa össze…”
- „Indokolja…”

Make every requirement sufficiently precise that two competent students would be assessed against essentially the same criteria.

However, do not over-specify the solution. Where multiple technically valid approaches exist, allow the student to choose an appropriate method and require them to justify the choice.

Do not provide implementation code or the solution.

Do not assume a particular dataset, domain, target name, feature name, or business problem.

The final output should contain **only the exam assignment**, not an explanation of how the exam was designed.