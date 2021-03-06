# Overview

Human pose recognition, and related tasks like gesture recognition and action recognition, are important tasks for AI systems that interact with people. There are many algorithms for classifying pose; for example, deep convolutional neural networks can be trained to classify pose directly from images. However, these methods tend to be “black boxes” and it’s difficult to understand what features they are using. Another approach, which we will use in this Project, uses neural networks to first identify key points corresponding to the main parts of the body (as shown above), and then learns to recognize pose based on the positions of these body parts. In this project, I will implement a supervised naïve Bayes learner to classify pose from key points provided by a deep convolutional neural network. I will train, test, and evaluate my classifier on a provided dataset, and then I will have a choice of either extending this basic model in various ways, or using it to answer some conceptual questions about naïve Bayes.

# Naive Bayes classifier
 There are some suggestions for implementing the learner in the “Naïve Bayes” and “Discrete & Continuous Data, my implementation will perform the following functions: 
• preprocess() the data by reading it from a file and converting it into a useful format for training and testing 
• train() by calculating prior probabilities and likelihoods from the training data and using these to build a naive Bayes model 
• predict() classes for new items in a test dataset 
• evaluate() the prediction performance by comparing my model’s class outputs to ground truth labels
 	My implementation will be able to handle numeric attributes and it will assume that numeric attributes are Gaussian-distributed. My model will not be expected to handle nominal attributes. My implementation will compute the priors, likelihoods, and posterior probabilities for the naïve Bayes model and not simply call an existing implementation such as Gaussian NB from scikit-learn. 1 11 2 10 3 4 5 7 6 8 9 Key point diagram 
# Data 
The data for this assignment is drawn from a yoga pose classification dataset created by Anastasia Marchenkova and released online here. Separate training and test datasets are provided. 
The pose key points were produced by a computer vision algorithm based on OpenPose. The algorithm identifies 11 key points on the body and returns their x and y values. The data is provided as a csv file; the first column is the name of the yoga pose and the remaining columns are the key points (11 x values followed by 11 y values). The body parts represented by each of the 11 keypoints are shown to the right. 
Since the key point data was generated by a computer vision algorithm, it may contain some errors. Some instances have missing keypoints because a part of the body was not visible in the original image or the algorithm failed to detect it. Missing keypoints have x and y values of 9999.
