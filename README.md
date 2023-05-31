# Classifying Mushrooms from Agaricus and Lepiota Families

### Introduction and Goals
In this project we work with the UCI mushroom dataset (https://archive.ics.uci.edu/ml/datasets/mushroom), the goals of this project 
are as follows:

- Classify mushrooms as poisonous or edible with high accuracy (above 90%)
- Select a model with good F1 score (low false positives and false negatives)
- Explore and perform extensive feature engineering methods to identify the best features for classification
- Perform hyperparameter search for the models to be tested through cross validation to examine each model’s performance carefully.
- To identify the most common categorical features of poisonous mushrooms.
- Propose the best model with low computational complexity, high accuracy and F1 score and high scalability.
---

### Initial Observations
We set up 2 baseline models and compare other models against these baselines. These models are as follows:
- Trivial system (randomly predict the class for a given datapoint)
- Nearest Mean Classifier (predict the class of depending on the closeness to class means)

Baseline model performance:
- Trivial system: Accuracy = 50.27% | F1 score = 0.4379
- Nearest Mean Classifier: Accuracy = 60.35% | F1 score = 0.5364
---

### Feature Engineering

We then select logistic regression model and perform PCA for dimension reduction and the following is the summary of the initial observations:

- Trivial system has a classification accuracy of 50.67% which is as good as tossing a coin
- The baseline model of nearest mean classifier has an accuracy of 60.346% which is only slightly better than the trivial system
- Training a logistic regression model on all one hot encoded features (92 features) resulted in a classification accuracy of 77.616% which is promising
- PCA is tested to reduce the feature dimension from 92 to 30 which resulted in logistic regression model accuracy of 68.561%, hence supporting use of other techniques to reduce feature dimensions
- In the next step feature reduction by combining multiple features together has been tried. It can be seen from the results that the top 5 feature combinations based on classification accuracy, all have an accuracy that is less compared to training the model using all 92 one hot encoded features.
- These observations formed the basis of motivation to explore other feature engineering methods for dimensionality reduction.

We then perform 2 advanced feature engineering methods for dimensionality reduction Univariate Feature Selection (UFS) and Recursive Feature Elimination with Cross validation (RFECV), the following is a summary on of these experiments:

- There were 46 features selected using UFS with chi2 statistic test
- There were 51 features selected using RFE
- There were 32 features common to both UFS and RFE
- Running RFE on 46 features selected by UFS did not further reduce the features, REF considered all 46 features
- Accuracy with 46 UFS features was 77.971%
- Accuracy with 51 RFE features was 77.638%
- Accuracy with 32 common features was 75.804%

Result of analysis: UFS method gave the lowest number of features with highest accuracy. The model used for accuracy measurement is logistic regression.

---

### Model selection and hyperparameter tuning

We experimented with the following models: 
- SVM Classifier (with linear and RBF kernels)
- Multilayer perceptron (MLP)
- K Nearest Neighbors 
- Random Forest Classifier
---

### Results

We observed that the Random forest classifier provided the best accuracy of 99.53% and an F1 score of 0.9946. 
Along with this, we were also able to determine the features that are most common to poisonous mushrooms. If a mushroom satisfies more than 1 of the following properties then it can be assumed to be poisonous:
- cap-shape : o
- stem-color : r/b
- gill-attachment : p
- habitat : w
- cap-surface : h
- does-bruise-or-bleed : a • ring-type : l
- cap-color : l

For further details please consult the project report.

---

### Contributors:

#### Meghana Achanta  
MS ECE (Machine Learning and Data Science)  
vachanta@usc.edu   
University of Southern California  
LinkedIn: https://www.linkedin.com/in/meghana-achanta/  

#### Vishal Patil  
MS ECE (Machine Learning and Data Science)  
vspatil@usc.edu  
University of Southern California  
LinkedIn: https://www.linkedin.com/in/vshlpatil/  

---
