# Sentiment-analysis-Udacity-project 

The goal of this project was to create and deploy a simple Long short term (LSTM) model that would be able to accurately predict the sentiment of 
a movie review entered in a sentiment web app by an online user.
The model was built, trained and deployed using amazon sage maker and the deep learning framework used for training the model was Pytorch.

## Project Overview
+ The project was entirely done on amazon sage maker using two GPU instances (ml.p2.xlarge & ml.m4.xlarge) to train and implement the model. In order to be able to train the model on the 
processed data, the data was uploaded to the S3 instance. 

+ Furthermore, the trained model was deployed in sagemaker where an endpoint was created which serve as an interface to our trained model (note that amazon sagemaker launches a compute instance that hosts the model once the endpoint is created and this compute instance runs until the endpoint is deleted or shutdown).
To use the deployed model for our sentiment web app, a lambda function was constructed that sends data to the sagemaker endpoint and also receive the predicted output from the sagemaker endpoint.

+ Finally, to execute or trigger the lambda function to perform its job, a new endpoint was created using Amazon's API Gateway. This new endpoint will be a url that 
listens / wait for data to be sent to it. Once it gets some data it will pass that data on to the Lambda function and 
then return the predicted output (that the Lambda function sends back) to our web app. 
Essentially it will act as an interface that lets our web app communicate with the Lambda function.

+ The project instructions and the code executed for this project can be found in the `sagemaker project.ipynb` file.
