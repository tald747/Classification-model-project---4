<img src="https://user-images.githubusercontent.com/42075039/153004513-7171c3a0-6213-4c83-aa17-743b064855de.jpg" width="700">

# Fraudulent electricity and gas customers in Tunisia

The goal of this project is to predict fraudulent electricity and gas customers, using various machine learning classification models.

### Background:
- Societe Tunisienne del'Electricite at du Gaz (STEG) is the leading electricity and gas provider in Tunisia.
- STEG has almost 5 million customers (4mill electricity and 1mill gas consumers) and provides over 15k GW/H annually. 
- STEG suffered tremendous losses in the order of 200 million Tunisian Dinars (~70 million USD) due to fraudulent manipulations of meters by consumers.

### Objective:
While all of STEG’s clients are metered, electricity theft has been a growing challenge since the Revolution, reflecting a deterioration of the social contract. This project focuses on predicting the fraudulent customers.

## Data source:
Kaggle - Fraud Detection in Electricity and Gas Consumption:
 - https://www.kaggle.com/mrmorj/fraud-detection-in-electricity-and-gas-consumption
## EDA process:
340MB csv file with 4.47m records and 22 columns, 137K clients
- I have found a problem with the timeline continuity and decided to focus on the meter readings as a feature representing the timeline.
<img src="https://user-images.githubusercontent.com/42075039/153003906-77c1235b-7af3-4e34-a114-7235dead71cf.png" width="700">
- Gas and electricity have different tariff types.
- Certain districts and regions showed higher proportion between fraudulent and regular clients.
- Fraudulent clients were identified as more likely to change meters during their lifetime. 
- I have noticed a higher percent of average monthly consumption values for fraudulent clients in particular segments of the consumption scale.

## Feature engineering:
- I had gone through the process of feature engineering 3 times, with the aim of improving models’ performance and ended up with 9 features.
- Our guideline in performing this task was reaching a “wide form” format in the most efficient way, with 1 line remaining per client.
- For features with higher fraudulent clients’ proportion, we calculated the ratio between them and all clients.
- Irregular meter readings between ending and starting points, led us to chose it as an indication of fraud.
<img src="https://user-images.githubusercontent.com/42075039/153004187-2efd9ed4-02a8-4d20-bd4d-ae20dffece89.png" width="700">
## Models' performance:
- The models used: LR, DT, RF, XGB, LGBM and Voting.
- I tried PCA for dimensionality reduction, which was fruitless.
- Our data was imbalanced (1 to 17 ratio) which had to be taken into account during data splitting and models’ class weight.
- I performed Cross validation and Grid search for optimization.
- AUC score was our main metric for model evaluation.
- I used the Voting model but there was no improvement in the result.
- For the business requirements I chose f-beta as the score for optimizing the Recall/Precision ratio. Few Betas were tested in order to find the optimal.

## Results and conclusions:
- Changing the class weight from ‘balanced’ to a lower ratio improved the model.
- Feature engineering was the key for improving the models.

<img src="https://user-images.githubusercontent.com/42075039/153004323-ad9c0923-0803-4555-b41f-ba9220939d06.png" width="500">
<img src="https://user-images.githubusercontent.com/42075039/153004409-1c3a1796-d8a1-4b72-9c6f-ad614a5a6d3f.png" width="700">
