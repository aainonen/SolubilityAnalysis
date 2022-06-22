# Solubility Analysis: Project Overview

Curated solubility database (Sorkun et al. 2019) was used as data source. Database contains 
9982 molecule's curated solubility and molecular descriptor data.

Jupyter notebook contains my analysis where I utilized Python (Pandas) and machine learning techniques (Skicit-learn library).

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

I started exploratory data analysis by creating a correlation matrix to understand which molecular 2D descriptors correlate with solubility.
Strongest correlation factor with solubility was observed with MolMR (Molar refractivity, r = -0.42). MolWt (Molecular weight, r = -0.37),
HeavyAtomCount (r = -0.35), NumValenceElectrons (r = -0.35) and Labute ASA (Labute's approximate surface area, r = -0.35) had the next
strongest correlations.

![image](https://user-images.githubusercontent.com/48836327/174854206-2da396bd-ec64-469f-837e-bace7377ee79.png)

Solubility_class has two values: "1" stands for "highly soluble" and "0" stands for all the other solubility classes.
I created these 4 solubility classes based on criteria established In Sorkun et al. (2019) article:
- 'Highly soluble': solubility values (0, positive infinite]
- 'Soluble': solubility values (-2, 0]
- 'Slightly soluble': solubility values (-4,-2]
- 'Insoluble': solubility values (negative infine, -4]

Bar chart is shown below to visualize the distributions of solubility values in database.

![image](https://user-images.githubusercontent.com/48836327/174857157-f46dedb7-4e77-4ce2-a8f1-19afbaa646d2.png)

Below is also a Whisker plot to visualize how solubility values are distributed in each solubility class.

![image](https://user-images.githubusercontent.com/48836327/174858347-417c2f52-efc5-4ff3-8048-d18ef376a992.png)

Below is PCA visualization. Three principal components can separate the solubility classess.

![solubility PCA](https://user-images.githubusercontent.com/48836327/174958138-c2307e34-3dea-4562-9eb5-05dd2728144d.png)


## Modeling solubility

Best accuracy was found with ensemble voting regression. Below is scatter plot of predicted vrs actual solubilities.

![image](https://user-images.githubusercontent.com/48836327/174960295-5398edfd-9dc1-447d-b872-bb63565b5f26.png)

Following machine learning algorithms were tested from Skicit-learn library. Further work on project should involve improving
the models by optimizing their parameters. Downside of ensemble algorithm was that it was relatively slow (~ 0,5-1 min to train the model).

![image](https://user-images.githubusercontent.com/48836327/174960856-6d5d3798-794f-4a96-8660-f440573cc7eb.png)

## Solubility class predictions

Predicted solubility values (by neural network) were descaled and converted to solubility classes. Same treatment was made to for the
actual solubility values (y_test). Solubility class prediction accuracy was tested.

![image](https://user-images.githubusercontent.com/48836327/174961880-b5f18c5b-c995-4a3d-9dae-cd0627545e7e.png)

Only 64 % class prediction accuracy was obtained. But how much better classification accuracy could we get, if it would be good enough to know
whether molecule is just poorly soluble or well soluble?

Solubility classes would therefore be:
- Insoluble and slightly soluble molecules have solubility class code 0 (=poorly soluble)
- Soluble and highly soluble molecules have solubility class code 1 (=well soluble)

![image](https://user-images.githubusercontent.com/48836327/174962383-d691371d-a020-48e1-932a-213fe7dc2c47.png)

Now algorithm had 82 % prediction accuracy when classifying molecules between poorly soluble ('Insoluble','Slightly soluble') and well soluble ('Soluble','Highly soluble')

