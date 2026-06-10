# well-logs-for-lithology-classification
Well Logs for Lithology Classification | Machine Learning

Workflow:

For this project I developed the following steps:

1. Downloaded from kaggle the dataset with several well logs
2. I decided to choose data from one well to create a model that predicts the formation lithology given the values of the logs (multi classification model)
3. I performed EDA by taking a look at each variable and to see if there were any missing values.
4. I developed an algorithm that prints the analysis for categorical variables (group and formations) I realized how many formations were available
5. During EDA I also discovered outliers, considering they no affect the model I left them as they came
6. For missing values I imputed some values with the mean of the fromation to each data record belong to
7. Then I performed a visualization with a detail breakdown of the formations and well logs to see how data was spread
8. I split the data into training, validation and test. Then scale each one of them using min max scaler
9. I started developing multi classification models:
	- Decision tree, full growth: score of 94.85% of accuracy on validation set, then checked feature importance to maybe further analysis on best subset selection, then tested accuracy changing tree depth and both gini and entrophy index, finally grid search with result of 95.58% on validation set (8 max depth and min_split=5)
	- Logistic regression: score of 92.22% of accuracy on validation set, then tried gridsearch with 3 solvers (lbfgs, newton-cg and saga) and different C values and different penalties (l1, l2 and withouth) obtaining a result of 94.12% on validation set (C=0.001, without penalty, solver=newton-cg)
	- ANN: first tried one hidden layer with 256 nodes, score of 92.9%, then tried different optimizers and learning rate values (RMPProp, Adam, AdamW), best was AdamW with score of 94.35% on validation set with 2 hidden layers of 128 nodes each
	- KNN: performed a loop to select the best k value, then the best model was with k=5, accuracy on validation set 96.02%
	- Naive Bayes: fit a traditional model with accuracy on validation set 84.04%, then tried a gridsearch but obtained 81.8% of accuracy.
