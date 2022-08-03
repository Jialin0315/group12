
# Group12


# Title: The prognostic discovery for type 2 diabetes and its hetergeneity

## [Google slide](https://docs.google.com/presentation/d/1pRaJSgVr7_E0SP7Fd20o3aGQw3QT2S6Ua7CX5R92J5c/edit?usp=sharing) for final presentation

## [Google Colaboratory](https://colab.research.google.com/drive/1lznWzu9_MxCyXmacX5vLXKvsyel4X0vV?usp=sharing) for all Codes

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

## Correlation Heatmap

<img width="435" alt="截屏2022-07-31 下午9 20 13" src="https://user-images.githubusercontent.com/100896537/182054920-69f25945-49c3-41a2-99b5-c97ea5efa483.png">


## Random Forest for selecting top 10 variables


<img width="449" alt="截屏2022-07-27 下午8 34 34" src="https://user-images.githubusercontent.com/100896537/181395488-8ad28fa3-c095-496b-b5a8-7dbb86139a76.png">

## Predictive accuracy of Random Forest Classifier
The accuracy of Random Forest Classifier is 0.41.


<img width="666" alt="截屏2022-07-31 下午9 19 23" src="https://user-images.githubusercontent.com/100896537/182054876-1958c9fa-62d9-489a-a980-22fa491aad0a.png">

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
### Density plot
![DNN_density plot](https://user-images.githubusercontent.com/100442163/181393876-557d4538-fd92-4864-863f-84c39659acfe.png)

### Defining the neural net
![DNN_Define the net](https://user-images.githubusercontent.com/100442163/181393967-a6b46f1f-e339-47d4-8fbf-37324d5ab271.png)

### Accuracy
![DNN_Accuracy](https://user-images.githubusercontent.com/100442163/181394047-0c916bc1-63fe-4262-8511-3cd21fd96281.png)

## K-Means Clustering

### Elbow Curve

<img width="698" alt="Screen Shot 2022-08-01 at 5 44 15 PM" src="https://user-images.githubusercontent.com/86126331/182251530-fce16aef-b4c1-4e87-9e92-cd78728d0891.png">


### Scatter Plot for k=4

<img width="713" alt="Screen Shot 2022-08-01 at 5 44 31 PM" src="https://user-images.githubusercontent.com/86126331/182251561-c5c3038c-a2ee-4cba-b7d1-71224750b21a.png">


### 3D Scatter Plot for k=4

<img width="717" alt="Screen Shot 2022-08-01 at 5 44 52 PM" src="https://user-images.githubusercontent.com/86126331/182251610-465d6da5-5642-4407-8921-2f57251645df.png">


## Hierarchical Clustering

### Dendogram

<img width="679" alt="Screen Shot 2022-08-01 at 5 43 13 PM" src="https://user-images.githubusercontent.com/86126331/182251408-6c3ab22e-14ef-4c6c-98ef-3a489223358c.png">

### Scatter Plot

<img width="646" alt="Screen Shot 2022-08-01 at 5 42 57 PM" src="https://user-images.githubusercontent.com/86126331/182251375-5964f347-da42-4d14-9f6e-26547167eacc.png">


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


