
# Group12


# Title: The prognostic discovery for type 2 diabetes and its hetergeneity

## [Google slide](https://docs.google.com/presentation/d/1pRaJSgVr7_E0SP7Fd20o3aGQw3QT2S6Ua7CX5R92J5c/edit?usp=sharing) for final presentation

## Background: 

Type 2 diabetes (T2D) is one of the most prevalent chronic diseases worldwide, a mystery for modern medicine leaving no cure. As such, the early diagnosis (prediction)  is essential to stop or delay the onset of future T2D. However, the current clinical prognostics have very poor accuracy. The appropriate human model for this exploration is the foremost challenge. Gestational diabetes mellitus (GDM) is a glucose intolerance phenomenon, that first appears during the last trimester of pregnancy, and mostly disappears after childbirth. Since GDM women have a 74% increased age-adjusted risk for future T2D, and approximately 35% of GDM women developed T2D within 10 years of postpartum, GDM women can serve as an appropriate human model for the T2D prognostic discovery. 

## Dataset: 
This investigation employed a precision medicine approach on a baseline (6-9 weeks of postpartum) metabolomics dataset to develop a nested 1:1 pair-matched (i.e., age, BMI, sex, and glucose tolerance) case-control study using 60 GDM Women. Women who did not progress to T2D within few years of postpartum are classified as “Control.” Each control is then pair-matched with case women who developed T2D within same years of postpartum. 

## Preprocessing Dataset:

Analytes (variables) with more than 5% of values missing were removed. Otherwise, the missing values were estimated as half of the lowest positive values. A quantile normalization followed by log transformation were carried out to get a normal/semi-normal data distribution. The final dataset was composed of approximately 100 analytes (i.e., metabolites).

## Objectives:

### Aim-1: Applying PCA to find out the influence of confounding factors in this dataset.
### Aim-2: Initially, we will rank the analytes using random forest. A few top ranked analytes will be explored by supervised MLs-based classifiers (i.e., logistic regression, multiple logistic regression, decision tree, and SVM) to identify the prognostics, followed by the model comparisons. 
### Aim-3: Applying Deep Learning classifier to identify the prognostics.
### Aim-4: Applying clustering algorithms (i.e., K-means, and Hierarchical clustering) to identify the disease heterogeneity.


## Methods:

## Determination of confounding factors' influence in the dataset

  - Human dataset always suffers from confounding factors' influence which challenge the proper classification and may integrate biases in the results. As such, it is important to determine how much influence of different confounding factors in the dataset. If this influence is substantial, we can go for dimension reduction procedure. However, it will reduce the sample size which is another important factor for unbiased discovery of prognostics. Here, we will apply PCA to identify the confounding factors and their contribution (i.e., influence) in the dataset. Based on this parameters we will decide whether we need to dimension reduction.

### Classification

  - Rank parameters with random forest classifier model in terms of feature importance, find the top 10 parameters that relates the most to type II diabetes development.
  
  
      - Random forest classifier is a supervised machine learning model contains multiple decision tress, and try to obtain an uncorrelated forest of trees whose prediction by committee is more accurate than that of any individual tree.
      
      
  - Put the new dataframe with the top 10 parameters in multiple logistic regression model, verify that how predicting power increase with adding attribute.
  
  
    - Multiple Logistic Regression predicts a single binary variable using variables obtained from the dataset. With the increasing number of parameters determined from random forest classifier model being added into consideration, the accuracy, precision, and sensitivity score should be increasing as well, and could therefore verify how the predicting power would increase with adding attribute.
  
  
  - Apply different classification models (e.g., support vector machine model, decision tree, deep neural network, etc.) to classify the data based on the position in relation to a border between control and case individual in the study. 
  
  - By generating confusion matrix with assess of accuracy, precision, and sensitivity for each model, how reliable would the model we developed be to use for clinical prognostics for type 2 diabetes based on the data obtained from GDM women.



### Clustering
- T2D is a heterogeneous diseases, usually have many subgroups within the population. This diversity challenge the success of one-model-fits-all for treatment and diagnostics. As such, the discovery of these heterogenous subgroups are essential before targeting any disease curing interventions. In this instance, clustring algorithms can play a vital roles.  

- A form of unsupervised machine learning to discover natural grouping in input data. Both K-means clustering and Hierarchical clustering will be used and outputs will be compared.

  - **K-means clustering:** used to find groups which have not been explicitly labeled in the data, can be used to confirm what types of groups exist and to identify unknown groups in complex data sets
  
  - **Hierarchical clustering:** clusters are presented in the form of a tree, called dendrogram. Nodes are compared with one another based on their similarity, with larger groups being comprised of smalled nodes joined by similarity. 
  
- The data will be refined to three clinical variables/parameters to determine clusters based on their importance in T2D diagnosis:

  - FPG
  
  - HOMA_IR
  
  - 2hr_OGTT
 
- Both clustering techniques, K-means and Hierarchical clustering, will be used to compare which method gives the best result for the dataset.

# Results

## Random Forest for selecting top 10 variables
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
## Predictive accuracy of Random Forest Classifier
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
## Predictive accuracy of multiple logistic regression
We have used top 10 variables found in random forest, then use them in stepwise multiple logistic regression using R-code.
It selected 7 out of 10 variables and accuracy is 75% with ROC-AUC 90.5%.

![MLR](https://user-images.githubusercontent.com/100442163/181392023-c72d6f45-369f-4a32-af7d-b4785809629c.png)

### Accuracy table
![MLR_Accuracy](https://user-images.githubusercontent.com/100442163/181392480-61910ba1-3961-4934-aa2d-c0311b61ba0c.png)

### ROC-AUC
![Rplot](https://user-images.githubusercontent.com/100442163/181392360-f7fec243-b7cc-4aeb-be3b-14dbf5437c6c.png)

## Deep Neural Network
We applied Deep Neural network on the dataset to find out classification accuracy.

## things to submit for segment 2:
-Create database in RDS/MongoDB (or a database of your choice) along with tables from the ERD and the data imported in the tables.


-Python code connecting to the database and getting bringing data back in Python.


-Python for Exploratory Data Analysis (random forest to find the top 10 parameters).


-Python code for training and testing the benchmark (simple) machine learning model as per your Segment 1 deliverable e.g. Logistic Regression for classification, Kmean for clustering and PCA)


-Blue print for final dashboard (image to put in the actual dashboard)


