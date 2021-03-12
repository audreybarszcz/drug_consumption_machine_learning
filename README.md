# MSDS699 Final Project
USF MSDS Machine Learning Laboratory Final Project
Contributors: Audrey Barszcz

The dataset can be found [here](https://archive.ics.uci.edu/ml/datasets/Drug+consumption+%28quantified%29#)

** Note that the original data on the UCI website has been transformed from categorical values to a scaled numeric value, I simply converted the scaled numeric values back to their original categorical values and use the converted data in this notebook.

## Goal
This project aims to predict level of cannabis use based on demographic information and personality inventory scores. Two different classification models (LogisticRegression and RandomForest) are used, ultimately a RandomForestClassifier model is used to predict on the test data.

## About the dataset
The dataset includes responses from 1885 participants. Demographic information such as age, gender, education, country, and ethinicity and personality inventory scores for certain traits were collected from each participant. In addition to demographic information and personality scores, level of use of various drugs was collected as well. The dataset includes level of consumption for 18 different drugs as well as responses for a fake drug called "Semeron" to identify participants that wanted to over-report drug use. Use of each drug was reported using an ranked scale ranging from "Never used" to "Used in the last day".
For this project specifically, I used the cannabis use column as my target variable of interest.

## Data Preprocessing
There is no missing data in this dataset to impute. The distribution of classes was examined to see if there were class imbalances. There are class imbalances that are later accounted for by SMOTE in the modeling pipeline. Further, the y-values are stratified in the train test split to maintain the same relative distribution of labels in each subset of y.

Each column of the data was transformed using its optimal transformer as chosen using cross validation.

## Models
I tried predicting cannabis use using two different classification models, logistic regression and Random Forest. Ultimately, the Random Forest classifier performed better on the validation set so it was used to predict on the test set.

## Metrics
Models were compared and evaluated based on balanced accuracy and f1-weighted scores. These metrics were chosen for their ability to evaluate multi-class classification problems. Particularly, f1-weighted was chosen for its consideration of relative class frequencies in the full dataset.

Ultimately, the Random Forest classifier yielded a f1-weighted score of 0.351 and a balanced accuracy score of 0.303. The poor performance of the model may be attributed to the diffculty of the classification problem itself since there are 7 classes to choose from and the separation between labels is not highly distinguishable. A better classification problem may be to predict whether someone has used a drug before or has never used a drug before.

## Limitations of the data
Based on the demographic information collected in this dataset, a majority of the participants are between the ages of 18-34 years old, are white, are in either the UK or the USA, and have some college experience. Based on the demographic information, I would not try to use a model trained on this data to try and predict drug consumption for the general population. The demographics of this dataset are not well distributed and therefore, are probably not representative of the population as a whole.
