### In this repository, there are four Jupyter notebooks:

#### 1. Exploratory Data Analysis:
---
Right after we received the huge dataset from Humana, we had no idea what every feature was (800+ features), so I performed a basic EDA to understand some features such as drug usage, patient gender, smoking status, and frequency of hospital visits. Basically, I used pandas and numpy to clean up data, and matplotlib and seaborn to perform data visualizations. 
As I was exploring these features, I also did feature engineering on some interesting features such as grouping and binning, creating different drug usage/hospital visit levels. 

#### 2. Final Feature Engineering:
---
Before the modeling stage, we were trying to create as many features as possible. We utilized mainly four techniques: group binning, weighted metrics, K-means Clustering, and deep feature synthesis. With these four techniques, we ended up with more than 8000 features. 

#### 3. Feature Selection: Logistic Regression & XGBoost:
---
We ran a forward selection using a Logistic Regression to identify the most relevant features to avoid overfitting our model. This forward selection process worked by running different models in a series of rounds, where each round a single, new feature was placed into the model. We selected 250 features based on the highest ROC AUC score. With these 250 features, our model was not performing very well, so we thought we might have overfitted our model. Therefore, we ran another forward selection using XGBoost to return the features that were contributing the most to improving the ROC AUC score, and we ended up with 74 features. This low number of features helped prevent building an overly complex model that would significantly reduce computational time, generating much quicker predictions.

#### 4. Final XGBoost Model:
---
Since the original business question centered around predicting individuals that will have transportation issues, we decided that constructing a binary classification model would be the most appropriate way to address this question. Therefore, we tried a few binary classifical models and concluded that XGBoost was the most accurate one with the highest ROC AUC Score (0.74) compared to Logistic Regression (0.71), Random Forest (0.71).
Our final model finished with a ROC AUC metric of 0.7508 and a model accuracy of 72%.  The weighted average scores for the precision, recall, and F-1 scores were 0.83, 0.72, and 0.75.

### Conclusion 
From these model insights, we discovered that disability, age, prescription claims, Stress, and motor vehicle percentage are all major factors for transportation issues and we can use these variables as foundations for forming user groups.  While we believe that our model performs well enough to give a general estimate, we recognize that our model has potential flaws, in particular the poor precision score for positive cases.  Our recommendation would be to use this model’s predictions as a guide and dedicate more time on its specific components to identify customized solutions for each member.  
