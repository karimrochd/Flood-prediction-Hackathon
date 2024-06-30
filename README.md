

## Introduction

This project is a participation in a Machine Learning Hackathon organized by Capgemini on Codabench. The code is based on the provided baseline, and this submission achieved **third** place in the [competition](https://www.codabench.org/competitions/1567/#/results-tab).
This report documents the development, evaluation, and analysis of a machine learning model designed for predicting flood events. The project utilizes various data processing techniques, machine learning models, and evaluation metrics to achieve a reliable flood prediction system. The primary objective is to optimize model performance while ensuring frugality in computational resources, robustness across different conditions, and explainability of the model's predictions.
Note: The code that was provided in the starter kit to download the dataset doesn't work, so the data was downloaded manually.
## 2. Performance Evaluation

### 2.1 Model Performance: AUC ROC

#### Data Processing and Feature Selection
The project commenced with preprocessing steps outlined in the starter kit, with enhancements made to the number of mini data cubes for the second model to improve the dataset's representativeness. The feature selection process involved a meticulous examination of the provided features, where each feature's relevance was assessed based on its impact on model performance. The selection process was iterative, toggling features on and off based on their performance impact.

#### Model Selection and Hyperparameter Optimization
The baseline model chosen for this project was a Random Forest classifier, but I preferred using Logisticregression because even though it has a lower AUC ROC score it has a better Brier Skill Score. The hyperparameter optimization process was manual and iterative. By adjusting hyperparameters such as the features given to the model, I aimed to find a balance between model complexity and prediction accuracy. This process was time-consuming but necessary to avoid the lengthy execution times of automatic hyperparameter tuning methods.

### 2.2 Use Case Performance: False Positive Rate
The project also emphasized minimizing the false positive rate, especially for predictions with a high confidence level (ypred ≥ 0.9) but where no flood event occurred (y = 0). This aspect was crucial for the model's practical application, ensuring that the predictions made would be reliable and not lead to unnecessary alarm.

## 3. Robustness

### 3.1 Calibration

The model's calibration was evaluated using the Brier Skill Score (BSS), with the Brier Score (BS) reflecting the accuracy of probabilistic predictions. The calibration process involved changing the model from random forest to logistic regression even though random forest had a better AUC ROC score but a higher BrierScore and adjusting the model to ensure that the prediction probabilities accurately represented the true likelihood of flood events. This step was critical for the model's trustworthiness and reliability in operational settings.

### 3.2 Validity Domain

Analyzing the model's validity domain revealed its performance variability across different geographical locations and times using the functions given in the stater kit, those function were commented from the submitted notebook to minimize the computational footprint (they take a lot of time to execute). The model showed a tendency to perform better in certain regions and periods, likely reflecting the varying characteristics of flood events and the representativeness of training data. This analysis led to recommendations for the model's deployment, highlighting its strengths and limitations in predicting floods under various conditions.

## 4. Frugality

To minimize the computational footprint, non-essential code sections were either removed or commented out, especially those contributing significantly to execution times without improving model performance. This approach not only streamlined the model training and inference processes but also aimed at reducing the overall CO2 footprint, adhering to the project's sustainability goals.

## 5. Explainability

### Important Features
The model's explainability was enhanced by identifying and highlighting the most significant features for flood prediction. Features related to soilgrid clay, altitude, slope, the water density, proximity to rivers, and the M1 score were found to be pivotal. The model's reliance on these features aligns with the theoretical understanding of flood mechanisms, emphasizing the importance of terrain and hydrological factors in flood dynamics.

### Insights on Flooding Patterns
The explainability analysis offered insights into flooding patterns, suggesting that certain terrain types and climatic conditions are more susceptible to flooding. This understanding can aid in flood preparedness and mitigation strategies, allowing for targeted interventions in high-risk areas.

## Conclusion

The project successfully developed a machine learning model capable of predicting flood events with a focus on robustness and frugality. The manual hyperparameter tuning process, although time-intensive, allowed for the optimization of model performance. The analysis of the model's validity domain and calibration provides valuable insights into its operational strengths and limitations. Finally, the project's emphasis on explainability sheds light on the underlying factors influencing flood occurrences, offering potential pathways for enhancing flood prediction and management strategies.
