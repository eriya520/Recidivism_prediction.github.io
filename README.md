# Predict Recidivism

## Problem Statement
* Can we use machine learning models to predict recidivism within a period of three years?

## Background
* We started off wanting to find a correlation between mental health spending and incarceration rates. 
* We then reviewed state-level data to find if states could reduce incarceration rates using mental health services.
* During the latter part of discovery, we found a recidivism challenge from the US Department of Justice and that influenced how we approach recidivism, mental health, and incarceration. 

* We hope to understand the **risks associated with recidivism.** 

* We’re also hoping to find possible correlations between mental health spending and incarceration rates, which might provide insight into which states should invest more in mental healthcare services.

## Datasets
|Data description|link|
|---|---|
|Census_incarceration_data|![link](https://observablehq.com/@themarshallproject/adults-in-correctional-facilities-from-decennial-census)|
|Public_health_spending_data|![link](https://knoema.com/SHPCPHF2020/per-capita-public-health-funding-in-u-s-states)|
|Mental_health_spending_data|![link](https://rehabs.com/explore/mental-health-spending-by-state-across-the-us/)|
|Recidivism_data|![link](https://data.ojp.usdoj.gov/stories/s/daxx-hznc)|

## EDA 

* Correlations and visualizations:
    * recidivism by gender and race had show low correlation with recidivism. --Model is not biased toward race and gender therefore there is less chance of enthical issue.
    * recidivism by prison offense is showing property offense has the highest chance for recommiting within 3 years
    * Inmates with confirmed gang affiliation record showed a much higher rate of recommitting 
* Missing data handling: 
    * Over 10% of the data in gang affiliation and prison offenses is missing. 
    * There are columns that are unreasonable to impute. 
    * We cannot assign gang affiliation and/or a prison offense to individuals. 
* In this study we are using recidivism score as a measurement of successful and effective state mental health spending. 
* Correlations between
* For the remaining features, not a very strong correlation with target variable.


## Modeling approach

### Baseline model accuracy
* baseline model has about 57% accuracy

### ML models

* KNN model:
    * Neural network modeling performed moderately well. 
    * KNN analysis yielded a score of ~68.6% with grid searching over neurons and 1 or 2 layers.  And Model was slightly overfitted.
    * Additional and “deeper” grid searching over parameters and 4  hidden and dropout layers with (drop rate 0.2) achieved a score of ~68.74%, not improvement on accuracy score, but model is not overfitted.
    * F1_score: 75.2%
    * Recall_score: 81.7%

* XGBoost model:
    * XGBoost model had an accuracy score of 67.2%, before hyperparameter tuning. 
    * F1_score: 69%
    * Recall_score: 63%
    * Grid Search results showed overfitting. 

* Random Forest:
    * Random Forest was the worst model performed. 
    * It achieved a score of ~66.70% with no hyperparameter tuning
    * After grid searching over parameters, it was able to achieve a score of ~67.71% which only went up 1% 
    * F1 score: 74.9%
    * Recall score: 82.4%
    * Both models were definitely an overfit.*


|Model|Accuacy|F1-score|Recall_score|
|---|---|---|---|
|Baseline|57%|-|-|
|KNN-deep|68.7%|75.2%|81.7%|
|XGBoost|67.2%|69%|63%|
|Random Forest|67.7%|74.9%|82.4$|


## Conclusions
* Found negative or low correlation between select features (gender, age, race, etc.) and recidivism within three years.
* Next steps would be to find similar recidivism data for another state in order to compare mental health spending with incarceration rates and recidivism predictions between states.
