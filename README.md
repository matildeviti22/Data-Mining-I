# Data-Mining-I

# Board Games Dataset Analysis 

## [Read the full report](https://github.com/matildeviti22/Data-Mining-I/blob/main/report.pdf)

This project was developed as part of the **Data Mining: Fundamentals** course and focuses on the analysis of a large board games dataset collected from **BoardGameGeek (BGG)**.

The objective of the project is to explore the structure of the dataset, identify meaningful patterns among board game features, and compare different data mining and machine learning techniques for clustering, classification, regression, and association rule mining.

## Project Overview

The dataset contains **21,925 board games** described by **46 attributes**, including gameplay characteristics, complexity metrics, community engagement indicators, publishing information, category membership, and rating-related variables.

The project covers the full analytical workflow:

- Data understanding and preprocessing
- Missing values analysis and treatment
- Feature correlation and redundancy reduction
- Feature aggregation and transformation
- Outlier detection and handling
- Clustering analysis
- Classification tasks
- Regression models
- Frequent pattern mining and association rules

## Dataset

Each record represents a board game and includes information such as:

- Number of players
- Playtime
- Recommended age
- Game complexity
- User ratings and community engagement
- Game categories
- Expansions, implementations, and alternate versions
- Rating class

Several features required cleaning due to missing values, semantic inconsistencies, placeholder values, or high redundancy.

## Data Preparation

The preprocessing phase included:

- Removal of non-informative features such as IDs, image URLs, and unstructured descriptions
- Treatment of placeholder values and missing values
- Category-based median imputation for selected variables
- Removal of highly sparse or semantically inconsistent features
- Spearman correlation analysis to detect redundant variables
- Feature aggregation, including:
  - `InterestScore`
  - `PlaytimeComAvg`
- Log transformations for highly skewed numerical features
- Ordinal encoding of the target variable `Rating`
- Outlier detection and filtering on `MaxPlayers`

## Methods

### Clustering

The clustering analysis compared different approaches:

- K-Means
- DBSCAN
- Hierarchical clustering with Ward linkage

K-Means was selected as the most coherent clustering solution. The final configuration used **k = 5**, achieving balanced and interpretable clusters.

DBSCAN was not retained because the dataset did not show clear density gaps, often producing either fragmented clusters or one dominant cluster.

### Classification

Two classification tasks were performed:

1. **Multiclass classification**  
   Target: `Rating`  
   Classes: Low, Medium, High

2. **Binary classification**  
   Target: `HighInteraction`  
   Derived from user rating activity

The following models were tested:

- K-Nearest Neighbors
- Naive Bayes
- Decision Tree

Models were evaluated using accuracy, precision, recall, F1-score, confusion matrices, and ROC/AUC analysis.

### Regression

Regression models were used to predict `GameWeight`, representing game complexity.

Tested approaches included:

- Linear Regression
- Ridge Regression
- LASSO Regression
- Decision Tree Regressor
- KNN Regressor

The non-linear models performed better than the linear ones, suggesting that game complexity depends on non-linear interactions between features.

### Pattern Mining

Frequent pattern mining and association rule extraction were performed using:

- Apriori
- FP-Growth

The analysis focused on discovering frequent itemsets and interpretable rules related to rating, complexity, playtime, and publication period.

## Main Results

- **K-Means with k = 5** provided the most robust clustering solution, with balanced cluster sizes and interpretable segmentation.
- In multiclass classification, the best model reached approximately **65% accuracy**, highlighting the difficulty of predicting rating classes due to feature overlap.
- In binary classification, the Decision Tree achieved the best performance, with approximately **77% accuracy** and **AUC = 0.85**.
- For regression, the Decision Tree Regressor achieved the best result, explaining around **61% of the variance** in game complexity.
- Association rule mining revealed that lightweight and short games were more likely to receive low ratings, suggesting a preference within the BGG community for games with greater strategic depth.

## Key Findings

The analysis shows that board game ratings and engagement are influenced by multiple interacting factors rather than by a single dominant feature.

Important patterns emerged around:

- Game complexity
- Playtime
- Publication year
- Strategic category membership
- Community engagement indicators
- Expansion and implementation features

The results also highlight the importance of feature selection and data preprocessing in improving model interpretability and performance.

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Mlxtend
