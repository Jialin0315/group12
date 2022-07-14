# group12


# Title: The prognostic discovery for type 2 diabetes and its hetergeneity

# Background: 

Type 2 diabetes (T2D) is one of the most prevalent chronic diseases worldwide, a mystery for modern medicine leaving no cure. As such, the early diagnosis (prediction)  is essential to stop or delay the onset of future T2D. However, the current clinical prognostics have very poor accuracy. The appropriate human model for this exploration is the foremost challenge. Gestational diabetes mellitus (GDM) is a glucose intolerance phenomenon, that first appears during the last trimester of pregnancy, and mostly disappears after childbirth. Since GDM women have a 74% increased age-adjusted risk for future T2D, and approximately 35% of GDM women developed T2D within 10 years of postpartum, GDM women can serve as an appropriate human model for the T2D prognostic discovery. 

## Dataset: 
This investigation employed a precision medicine approach on a baseline (6-9 weeks of postpartum) metabolomics dataset to develop a nested 1:1 pair-matched (i.e., age, BMI, sex, and glucose tolerance) case-control study using 60 GDM Women. Women who did not progress to T2D within few years of postpartum are classified as “Control.” Each control is then pair-matched with case women who developed T2D within same years of postpartum. 

## Preprocessing Dataset:

Analytes (variables) with more than 5% of values missing were removed. Otherwise, the missing values were estimated as half of the lowest positive values. A quantile normalization followed by log transformation were carried out to get a normal/semi-normal data distribution. The final dataset was composed of approximately 100 analytes (i.e., metabolites).

# Objectives:

## Aim-1: Applying PCA to find out the influence of confounding factors in this dataset.
## Aim-2: Initially, we will rank the analytes using random forest. A few top ranked analytes will be explored by supervised MLs-based classifiers (i.e., logistic regression, multiple logistic regression, decision tree, and SVM) to identify the prognostics, followed by the model comparisons. 
## Aim-3: Applying Deep Learning classifier to identify the prognostics.
## Aim-4: Applying clustering algorithms (i.e., K-means, and Hierarchical clustering) to identify the disease heterogeneity.



## google slide for final presentation
https://docs.google.com/presentation/d/1pRaJSgVr7_E0SP7Fd20o3aGQw3QT2S6Ua7CX5R92J5c/edit?usp=sharing


## things to submit:
-dataset breakdown (an overview of what the dataset is)
-an overview of what the project itself is
-have github ready (i.e individual branches etc)

