README

To run the Naive Bayes algorithm, these are the functions we need to call in order:
preprocess(train_file)
train(train_file)
prediction(test_file)

Preprocess Function :

The function will preprocess the input data by converting string values to float, replacing all missing values with NaN. To run the preprocess function, we get a csv file containing the train and test data as an input, such as:
train_file=preprocess(‘train.csv’)
test_file=preprocess(‘test.csv’)

Train Function :

This function returns the mean, standard deviation based on each feature and using those values to find prior probabilities and likelihood of training data. To run this function, we need input of a train csv file.
mean_list, sd_list, d_prior, keys_list = train(train_file)

Test Function :

This function predicts our test set by imputing the mean , standard deviation from the train set that we has calculated before in the train function and using the Gaussian naive bayes to calculate the prior probability and the likelihood.This function will return the class label based on the highest probability that we calculate from the sum of each instance.
prediction = predict(test_file.iloc[:,1:], mean_list, sd_list, d_prior, keys_list)

Evaluate Function :

This function will return to the accuracy, precision, recall, F score by comparing the prediction results and ground truth from the test file.
evaluate(prediction, test_file.iloc[:,0])
