# Solubility Analysis: Project Overview

Curated solubility database (Sorkun et al. 2019) was used as data source. Database contains 
9982 molecule's curated solubility and molecular descriptor data.

Jupyter notebook contains my analysis using Python (Pandas) and machine learning techniques (Skicit-learn).

### Project overview:

- Handled data with Pandas-library (feature selection, categorical values coding)
- Explored data by creating a correlation matrix, bar charts, whisker pltos and histograms
- Performed PCA-analysis and visualization
- Modeled solubility with Skicit-learn regression algorithms
    - Skicit-learn model_selection package to split data into training and testing subsets (20 % test)
    - Skicit-learn preprocessing package to scale data
    - Tested six different regression algorithms on their solubility prediction accuracy
    - Best accuracy found with an ensemble voting regressor (MAE = 0.4 and r2 = 0.67)
    - Trained neural network performed the second best (MAE = 0.41 and r2 = 0.65)
 - Predicted molecule's solubility class (i.e. 'Insoluble', 'Slightly soluble', 'Soluble', 'Highly soluble')
    - 64 % classification accuracy when predicted solubility-values were converted to corresponding solubility class
    - 82 % classification accuracy when predicting whether molecule in poorly soluble (0) or soluble (1)
        - 'Insoluble' and 'Slightly soluble' were assigned to poorly soluble class, and 'Soluble' and 'Highly soluble' were assgined to soluble class

## EDA

Highlights of EDA

![image](https://user-images.githubusercontent.com/48836327/174854206-2da396bd-ec64-469f-837e-bace7377ee79.png)



