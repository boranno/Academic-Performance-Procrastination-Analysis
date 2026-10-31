# Predicting the Impact of Procrastination on Academic Performance

**Author:** Boranno Golder

This project uses survey responses collected by Boranno Golder to explore the relationship between procrastination habits and academic performance. The notebook trains classifiers to predict a respondent's CGPA range from their survey answers.

## Dataset

The author collected the survey data and published it on Kaggle:

[Procrastination and Academic Performance — Kaggle dataset](https://www.kaggle.com/datasets/borannogolder/procrastination-and-academic-performance/data)

The notebook reads the CSV from Google Drive. Download the Kaggle dataset and place or rename its CSV to the following path in your Drive:

```text
MyDrive/Colab Files/Survey on Procrastination and Academic Performance  (Responses) - Form Responses.csv
```

The target is `cgpa`, grouped into five ranges. The notebook removes the timestamp and rows containing missing values before analysis. The dataset is not included in this repository; get it from Kaggle.

## Notebook workflow

The Colab notebook:

1. Installs the machine-learning and visualization libraries and mounts Google Drive.
2. Cleans the survey data and label-encodes categorical responses.
3. Explores CGPA class balance and uses SMOTE to balance the classes.
4. Uses chi-squared feature selection to examine and select predictors.
5. Trains Logistic Regression, Decision Tree, K-Nearest Neighbors, Naive Bayes, Random Forest, Gradient Boosting, CatBoost, and XGBoost classifiers, plus a soft-voting ensemble.
6. Prints classification reports, compares accuracy, runs 5-fold cross-validation, and creates confusion-matrix and feature-explanation visualizations, including SHAP analyses.

## Run in Google Colab

1. Open `Predicting_The_Performance_of_Procrastination_on_Academic_Performance.ipynb` in Google Colab.
2. Download the dataset from the Kaggle link above and place the CSV at the Google Drive path shown in the Dataset section.
3. Run the cells from top to bottom and authorize the Google Drive mount when prompted.

The notebook installs its dependencies in its first cells. Packages used include pandas, NumPy, scikit-learn, imbalanced-learn, CatBoost, XGBoost, Matplotlib, Seaborn, SHAP, LIME, and Graphviz.

## Results

The notebook output currently available contains package-installation logs only; model evaluation results have not yet been added. After running the notebook in Colab, summarize the results here:

- Best-performing model and its accuracy.
- Five-fold cross-validation mean accuracy and standard deviation.
- Macro-averaged precision, recall, and F1-score, plus per-class results.
- A confusion matrix or model-comparison chart, if useful.

The current evaluation has the limitations described below, so present its scores as exploratory. Do not include raw survey rows or outputs that could identify respondents.

## Evaluation note

In the current notebook workflow, SMOTE and chi-squared feature selection are applied before the train/test split. This can allow information from the eventual test set to influence training and make evaluation scores optimistic. The cross-validation section also uses `KFold` rather than a stratified splitter. Treat the reported scores as exploratory, not as an unbiased estimate of how the models will perform on new data.

This is observational survey data. Model predictions and feature explanations describe patterns in the collected responses; they do not establish that procrastination causes changes in academic performance or necessarily generalize to other student populations.

## Repository contents

- `Predicting_The_Performance_of_Procrastination_on_Academic_Performance.ipynb` — Google Colab analysis and model experiments.
- `requirements.txt` — Python package list.
- `.gitignore` — excludes local datasets, credentials, generated files, and notebook checkpoints.

Review notebook outputs for respondent information before making the repository public. Do not commit Kaggle credentials.
