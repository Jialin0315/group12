# group12








## Methods


### classification


  - Rank parameters with random forest classifier model in terms of feature importance, find the top 10 parameters that relates the most to type II diabetes development.
  
  
      - Random forest classifier is a supervised machine learning model contains multiple decision tress, and try to obtain an uncorrelated forest of trees whose prediction by committee is more accurate than that of any individual tree.
      
      
  - Put the new dataframe with the top 10 parameters in multiple logistic regression model, verify that how predicting power increase with adding attribute.
  
  
    - Multiple Logistic Regression predicts a single binary variable using variables obtained from the dataset. With the increasing number of parameters determined from random forest classifier model being added into consideration, the accuracy, precision, and sensitivity score should be increasing as well, and could therefore verify how the predicting power would increase with adding attribute.
  
  
  - Apply PCA model (to determine the effect of confounding factors), and develop other classification models for analysis. For example, support vector machine model to classify the data based on the position in relation to a border between control and case individual in the study. 
  
  
    - By generating confusion matrix with assess of accuracy, precision, and sensitivity for each model, how reliable would the model we developed be to use for clinical prognostics for type 2 diabetes based on the data obtained from GDM women.
