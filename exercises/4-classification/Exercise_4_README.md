Exercise 4 README.md

For this exercise, I worked with Shreya Sreeram and Ritika Batte. I had some difficulty running the models using Visual Studio Code so I opted to run them in Google Colab. I used the code breakdown provided on our class website as a foundation to run the models. 

Part 1: Classify letters a --> g 

For part 1, I decided to use a random forest model since it can be used for classifcation. These were the following hyperparameters I used: rf_param_grid = {'n_estimators': [50, 100, 150], 'max_depth': [None, 10, 20]}. After running the model, the best hyperparameters for the model were: RandomForestClassifier(max_depth=20, n_estimators=150). After checking the model performance on the validation holdout data, the model performed pretty well! The accuracy, precision, recall, and f1 score were all above 90%. When looking at the confusion matrix, it seemed that the lettters that had similar structures (a&g, b&d, etc.) were the ones that got mixed up the most. 

Part 2: Uppercase vs. Lowercase on abcxyzABCXYZ 

For this part, I decided to use XGBoost, random forest, and logistic regression model. These are the following hyperparamters respectively: 
xgb_param_grid = {'n_estimators': [50, 100, 150], 'max_depth': [3, 5, 7], 'learning_rate': [0.01, 0.1, 0.2]}
rf_param_grid = {'n_estimators': [50, 100, 150], 'max_depth': [None, 10, 20]}
lr_param_grid = {'C': [0.1, 1.0, 10.0], 'solver': ['liblinear', 'lbfgs'], 'max_iter': [100, 200, 300]}
The reason I went with these models was because they are suited for classification tasks and suitable for larger datasets like the ones we were dealing with. Random forest and XGBoost do not require you to scale the data while with logistic regression, it is generally good practice to do so. That being said, the data was not scaled since my model ran without scaling the data and it was mentioned that it was not required to scale the data for the assignment. After running the three models, the best model and associated hyperparamters were: LogisticRegression(C=10.0, max_iter=300). After checking this model on the validation test set, the model performance was slighlty above average. The accuracy was 77% while the precision, recall, and f1 score ranged from 68%-70%. When looking at the confusion matrix, we see that the model struggled with classifying upper and lower case letters that have similar structures (C&c, X&x, Y&y, and Z&z). This would explain the lower precision, accuracy, and f1 scores.  