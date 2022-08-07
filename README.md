
# The prognostic discovery for type 2 diabetes and its hetergeneity

## [Google slide](https://docs.google.com/presentation/d/1pRaJSgVr7_E0SP7Fd20o3aGQw3QT2S6Ua7CX5R92J5c/edit?usp=sharing) for final presentation

## [Google Colaboratory](https://colab.research.google.com/drive/1lznWzu9_MxCyXmacX5vLXKvsyel4X0vV?usp=sharing) for all Codes (Visualization Dashboard)

## [Tableau Dashboard](https://public.tableau.com/views/Group12databackgrounddashboard/Dashboard1?:language=zh-CN&publish=yes&:display_count=n&:origin=viz_share_link) for Dataset Background

## [Tableau Dashboard](https://public.tableau.com/views/ClusteringDashboard-Group12/Clustering?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link) for Clustering

## Background: 

Type 2 diabetes (T2D) is one of the most prevalent chronic diseases worldwide, a mystery for modern medicine leaving no cure. As such, the early diagnosis (prediction)  is essential to stop or delay the onset of future T2D. However, the current clinical prognostics have very poor accuracy which warrents the discovery of a highly accurate prognostics. 

For prognostic or predictive diagnostic discovery, we need a longitudinal study propulation, and some of these participants should develop T2D within a few of study. Here, we are using a metabolomics dataset of a population from whom some developed T2D within 5 years. We have taken 30 participants metabolomics dataset who devepoled T2D within 5 years. We pair-matched them to 28 controls who did not developed T2D. The pair-matching was carried out using age, BMI, sex, and race.  

This investigation employed a precision medicine approach on a baseline (none of them had T2D) metabolomics dataset to develop a nested pair-matched case-control study using 58 participants. participants who did not progress to T2D within few years from baseline time are classified as “Control.” Each control is then pair-matched with case participants who developed T2D within same years from baseline time point. 

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
  
  - By generating confusion matrix with assess of accuracy, precision, and sensitivity for each model, how reliable would the model we developed be to use for clinical prognostics for type 2 diabetes.



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

## Correlation Heatmap

<img width="435" alt="截屏2022-07-31 下午9 20 13" src="https://user-images.githubusercontent.com/100896537/182054920-69f25945-49c3-41a2-99b5-c97ea5efa483.png">


## Predictive accuracy of Random Forest Classifier
The accuracy of Random Forest Classifier is 41%; after modifying according to feature's correlation to target, the accuracy was increased to 79%


<img width="723" alt="截屏2022-08-03 下午9 15 29" src="https://user-images.githubusercontent.com/100896537/182742018-ab00339f-8331-4ca8-8fd7-ce03759ad832.png">


## Top 10 important variables selected by Random Forest Classifier


<img width="446" alt="截屏2022-08-03 下午8 02 29" src="https://user-images.githubusercontent.com/100896537/182741956-e06ff2a1-b0d0-42ff-910a-c2d0ca12b90f.png">



## Predictive accuracy of multiple logistic regression
We have used top 10 variables found in random forest, then use them in stepwise multiple logistic regression using R-code.
It selected 7 out of 10 variables and accuracy is 86.2% with ROC-AUC 91.3% (95% Confidence interval 84.1% - 98.5%).


![MLR_Final](https://user-images.githubusercontent.com/100442163/182738114-50f561c0-02ba-4819-bc24-01ea94ce0288.jpg)

### ROC-AUC

![Rplot](https://user-images.githubusercontent.com/100442163/182738335-ed40b920-0504-4609-9e5a-ee9ebe4f7480.png)

## Deep Neural Network
We applied Deep Neural network on the dataset to find out classification accuracy.
### Density plot
![DNN_density plot](https://user-images.githubusercontent.com/100442163/181393876-557d4538-fd92-4864-863f-84c39659acfe.png)

### Defining the neural net
![DNN_Define the net](https://user-images.githubusercontent.com/100442163/181393967-a6b46f1f-e339-47d4-8fbf-37324d5ab271.png)

### Accuracy
![DNN_Accuracy](https://user-images.githubusercontent.com/100442163/181394047-0c916bc1-63fe-4262-8511-3cd21fd96281.png)

## K-Means Clustering

### Elbow Curve

<img width="698" alt="Screen Shot 2022-08-01 at 5 44 15 PM" src="https://user-images.githubusercontent.com/86126331/182251530-fce16aef-b4c1-4e87-9e92-cd78728d0891.png">

A K-value of 4 was obtained from the elbow curve of the data pertaining to the three variables being used; FPG, HOMA_IR, and 2hr_OGTT. The below 2D and 3D scatter plots were obtained.

### Scatter Plot for k=4 

<img width="713" alt="Screen Shot 2022-08-01 at 5 44 31 PM" src="https://user-images.githubusercontent.com/86126331/182251561-c5c3038c-a2ee-4cba-b7d1-71224750b21a.png">


### 3D Scatter Plot for k=4

<img width="729" alt="Screen Shot 2022-08-07 at 12 01 18 AM" src="https://user-images.githubusercontent.com/86126331/183274670-99928723-1149-4a84-83c4-1eb51806ea3d.png">


## Hierarchical Clustering

### Dendogram

<img width="694" alt="Screen Shot 2022-08-07 at 12 20 38 AM" src="https://user-images.githubusercontent.com/86126331/183275179-7b2a0e82-ebff-4353-beb0-a7ff1faee08d.png">

A K value of 6 was seen upon analysis of the dendogram. The resulting scatter plot, using K=6, can be seen below.


### Scatter Plot

<img width="649" alt="Screen Shot 2022-08-07 at 12 08 12 AM" src="https://user-images.githubusercontent.com/86126331/183274857-960d37e3-a3fd-48ac-bce0-8b1ca4398ecc.png">


## things to submit for segment 3:
-Complete the open pull requests by finishing peer reviews and merging branches


-Create a presentation to share with the class
    - presentation should not exceed 8 minutes, will have 2 minutes for questions from the class and instructor (10 minutes in total)
    - state problem, how it was solved (choice of model, accuracy etc), results, next steps (subject to presentation length)
    - presentation should be 4-5 slides -> shouldn't require more slides

-Add polish to dashboard and tie up loose ends
    - visuals must be clear and accurate
    - look professional
    - relay important information

-Test your code prior to presentation


