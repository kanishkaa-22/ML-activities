# Machine Learning – Unit-wise Activities

Hands-on Jupyter notebooks for the five units of the Machine Learning course: exploratory data analysis, support vector machines, clustering, Markov models and decision trees. Each unit uses a real public dataset.

---

## Repository Structure

```
ACTIVITY/
├── unit1/
│   └── windai.ipynb                                   # Exploratory data analysis – wind turbine power data
├── unit2/
│   └── ml.ipynb                                       # Maximum-margin SVM – breast cancer classification
├── unit3/
│   └── Hierarchical_Clustering_Country_Development.ipynb   # Agglomerative hierarchical clustering of countries
├── unit4/
│   └── BPI2017_Abandonment_Markov_HMM_fixed.ipynb     # Markov chains and HMMs – loan-application abandonment
└── unit5/
    ├── CART_Student_Support.ipynb                     # CART decision tree – students needing academic support
    └── student-por.csv                                # Dataset for Unit 5
```

---

## Activities

### Unit 1 – Exploratory Data Analysis: Wind Turbine Power
**Notebook:** `unit1/windai.ipynb`

- **Dataset:** a reduced sample (500,000 rows, 18 columns) of the SDWPF wind-turbine dataset, with readings such as wind speed, wind direction, temperatures, blade pitch angles and active power output (`Patv`).
- **Work done:**
  - Data inspection: `head`, `info`, `describe` and missing values.
  - Descriptive statistics: mean, median, quartiles and percentiles.
  - Visualisations: wind speed histogram and box plot, active power box plot, wind speed vs active power scatter plot, and a correlation heatmap.

### Unit 2 – Maximum-Margin Support Vector Machine
**Notebook:** `unit2/ml.ipynb`

- **Dataset:** Breast Cancer Wisconsin (Diagnostic), with 569 tumour samples, 30 features, and benign or malignant labels.
- **Work done:**
  - Removed unnecessary columns.
  - Created an 80/20 train–test split.
  - Standardised the features.
  - Trained a linear-kernel maximum-margin SVM.
  - Evaluated it with a confusion matrix and a classification report.
  - Inspected the support vectors.
- **Result:** **96.5 % test accuracy**, using 38 support vectors (19 per class).

### Unit 3 – Agglomerative Hierarchical Clustering of Nations
**Notebook:** `unit3/Hierarchical_Clustering_Country_Development.ipynb`

- **Problem:** group 167 countries into stages of socio-economic development, using indicators such as child mortality, GDP per capita and health expenditure, to support targeted global aid allocation.
- **Dataset:** Unsupervised Learning on Country Data (HELP International): 167 countries and 9 indicators.
- **Work done:**
  - Pre-processing and feature engineering, including a Yeo–Johnson transform.
  - PCA, choosing the number of components.
  - Factor analysis and distance measures.
  - Comparison of linkage methods.
  - Choice of the number of clusters using silhouette, Davies–Bouldin and Calinski–Harabasz scores.
  - Ward-linkage dendrogram.
  - Comparison with K-means and Gaussian Mixture Models (EM).
  - World map of the clusters.
  - Aid-priority ranking.
- **Result:** three development stages: least developed (aid priority), developing and developed.

### Unit 4 – Markov Models: Predicting Loan-Application Abandonment
**Notebook:** `unit4/BPI2017_Abandonment_Markov_HMM_fixed.ipynb`

- **Problem:** given the first few events of a customer's journey, predict whether it will end in abandonment (cancellation).
- **Dataset:** BPI Challenge 2017, real loan applications from a Dutch financial institution.
- **Models:**
  - Absorbing Markov chain.
  - Class-conditional Markov chains.
  - Hidden Markov Models, scored with the forward algorithm.
  - A logistic-regression baseline that uses prefix length only.
- **Evaluation:**
  - Chronological 60/20/20 split.
  - Decision thresholds tuned on the validation set.
  - Metrics: ROC-AUC, PR-AUC, F1 and balanced accuracy.
  - AUC measured by prefix length.
- **Note:** in this run the sequence models did not beat the length-only baseline (ROC-AUC about 0.70). The notebook discusses the limitations and the next steps.

### Unit 5 – CART Decision Tree: Identifying Students Who Need Academic Support
**Notebook:** `unit5/CART_Student_Support.ipynb`

- **Problem:** use attendance, socio-economic background and continuous assessment scores to identify students who need academic support (final grade below 10).
- **Dataset:** UCI Student Performance, Portuguese course: 649 students and 33 attributes.
- **Models:** three CART trees using Gini impurity:
  - a full-grown tree;
  - a pre-pruned tree (grid search);
  - a cost-complexity pruned tree.

  Each uses balanced class weights. The final model was selected with 50-fold repeated cross-validation.
- **Extras:**
  - Feature importance.
  - Early-warning checkpoints: start of year and after the first assessment.
  - An academic-support plan for flagged students.
- **Result:** the final pre-pruned tree (depth 3, 8 rules) found **85 % of the students who needed support**, with a ROC-AUC of 0.935.

---

## Datasets

| Unit | Dataset | Link | File name expected by the notebook |
|---|---|---|---|
| 1 | SDWPF wind turbine data (reduced sample) | [Google Drive](https://drive.google.com/file/d/1GxHfbQfxjNXzJvySiFVLlxoa1TMooUY4/view?usp=sharing) | `sdwpf_redused.csv` |
| 2 | Breast Cancer Wisconsin (Diagnostic) | [Kaggle](https://www.kaggle.com/datasets/uciml/breast-cancer-wisconsin-data) | `breast_cancer.csv` |
| 3 | Unsupervised Learning on Country Data | [Kaggle](https://www.kaggle.com/datasets/rohan0301/unsupervised-learning-on-country-data) | `Country-data.csv` |
| 4 | BPI Challenge 2017 | [Kaggle](https://www.kaggle.com/datasets/rascanudragos/bpi-challenge-2017) | `bpi_2017_cleaned.csv` |
| 5 | Student Performance (UCI) | [UCI ML Repository](https://archive.ics.uci.edu/dataset/320/student+performance) | `student-por.csv` (included) |

Only the Unit 5 dataset is included in this repository. Download the others from the links above and place each file in its unit's folder, using the file name in the last column. Rename a file if it downloads under a different name; for example, the Kaggle breast cancer file downloads as `data.csv`.

---

## How to Run

1. Clone the repository:
   ```bash
   git clone <your-repo-url>
   cd ACTIVITY
   ```
2. Install the required libraries:
   ```bash
   pip install numpy pandas matplotlib seaborn scikit-learn scipy plotly hmmlearn
   ```
3. Download the datasets and place them in the matching unit folders (see the table above).
4. Open a notebook and run all cells:
   ```bash
   jupyter notebook
   ```

**Requirements:** Python 3.9 or later and Jupyter Notebook or JupyterLab. The notebooks also run on Google Colab.

---

## Topics Covered

| Unit | Topic | Techniques |
|---|---|---|
| 1 | Exploratory data analysis | Descriptive statistics, distributions, outliers, correlation |
| 2 | Support vector machines | Maximum-margin classifier, linear kernel, support vectors |
| 3 | Unsupervised learning | Hierarchical clustering, K-means, Gaussian mixtures (EM), PCA, factor analysis |
| 4 | Sequential models | Markov chains, absorbing chains, Hidden Markov Models |
| 5 | Decision trees | CART, Gini impurity, pre-pruning, cost-complexity pruning, cross-validation |

---

## Acknowledgements

- SDWPF dataset: Baidu KDD Cup 2022 (Spatial Dynamic Wind Power Forecasting).
- Breast Cancer Wisconsin (Diagnostic): UCI Machine Learning Repository.
- Country data: HELP International, published on Kaggle by Rohan Kokkula.
- BPI Challenge 2017: van Dongen, B. F. (2017), 4TU.ResearchData.
- Student Performance: P. Cortez and A. Silva (2008), UCI Machine Learning Repository.
