# week14_deep_learning_project
In this project, a LSTM model is used to predict the Bitcoin price using just the previous day closing price and also using the Fear aNd Greed (FNG) Index.

## Libraries/ library functions
- numpy
- pandas
- hvplot
- tensorflow
- from sklearn.preprocessing, MinMaxScaler
- from tensorflow.keras.models, Sequential
- from tensorflow.keras.layers; LSTM, Dense, Dropout

## Tools/ technologies
- Github
- Gitbash
- Gitlab
- Slack
- Jupyter lab
- Deep Learning
- Bitcoin FNG

## Task to accomplish
- Predict the closing price of the Bitcoin
- Determine if the FNG indicator provides a better prediction for Bitcoin closing prices than only the normal closing price.

## Notebooks created
- lstm_stock_predictor_closing
- lstm_stock_predictor_fng
---
## Data preparation
- The FNG Index and the closing prices are concatenated and sorted by the earliest date index.

### Defining the function
- A function is defined to iterate over the rows, to split the data into feature and target
- Closing prices notebook: The feature (input) and target (output) data are the same, which is the Bitcoin closing price
- FNG notebook: The feature is the FNG index and the target is the closing price.
- Apart from the above 2 steps, the rest of the preparation is the same for both the notebooks.

### Train-test split
- For the train and test split, 70% of the weight is assigned for training and the rest 30% of the weight is assigned for testing.
- X_train, X_test, y_train and y_test are scaled using the MinMaxScaler.

### Reshaping the feature
- Because the LSTM model uses a vertical vector for prediction, the X_train and X_test are reshaped into a single column vector
---
## Build and train custom LSTM RNN
- The number of LSTM units is 30.
- The dropout fraction is 0.2, 20% of the data is randomly excluded from analysis to prevent overfitting.
- The number of LSTM layers is 3.
- When summarized, the total number of trainable parameters is 18,511
- The model is fit with `X_train_reshaped` and `y_test_scaled`, desired number of epochs and batch size

## Model performance
- Target values are predicted from the test values `X_test_reshaped`
- Predicted and real prices are transformed to the original format using `inverse_transform`
- The predicted and real prices vector are then converted to a Pandas dataframe using the `.ravel()` attribute.
- A graph is plotted to visualize the results.

## Comparison of performance
- Which model has a lower loss?
    - The normal closing price model has a lower loss of 0.35%, compared with the FNG model which has a 7.6% loss

- Which model tracks the actual values better over time?
    - Upon using the same values of hyper-paramaeters for both the models, the normal closing price model's graph very closely resembles the real closing price, while the FNG model's graph is flat.

- Which window size works best for the model?
    - A window size of 1, gives results that are near the actual price and follows the actual trend.

## Hyper-parameter tuning
- Various values of hyper-parameters were tested to achieve a better accuracy. The following are the values of the hyper-parameters that narrowed the gap between the predicted and actual price of the Bitcoin.
- A snapshot of the various sets of hyper-parameter values that were tested has been attached.
- window size= 1 day
- number of LSTM units= 30
- dropout fraction= 0.2
- epochs= 10
- batch size= 5

## Figure
- trail_error.png (various sets of hyper-parameter values tested)
- normal_closing.png
- fng.png

## Challenges/ Difficulties
- This is my first deep learning project. The tuning process consumed more time than coding. Manually and repeatedly assigning values to the hyper-parameters was taxing. My tutor taught me to apply a for-loop to select the best values for hyper-parameters.

## Conclusion
- While the normal closing price graph closely follows the actual price, the graph of the FNG model is way off from the original price. I was suprised to discover how a particular feature could drastically alter the target.
- Thus far, the comparison of actual versus the predicted values has been performed. It would have been more intriguing if the task of future price prediction were assigned.
- Nevertheless, the project was exciting. With more practice, I will become competent with tuning.

## Contributors
- Satheesh Narasimman

## People who helped
- Khaled Karman, Bootcamp tutor

## References
- https://keras.io/guides/sequential_model/

- Bootcamp Class Materials-> Week 14: Deep Learning-> Day 3-> Activities 4 and 5.