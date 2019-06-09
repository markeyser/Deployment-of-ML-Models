


> Written with [StackEdit](https://stackedit.io/).

# Machine Learning Model Pipeline 
## Model Building

In this section I will cover very briefly how we build the machine learning algorithms. You probably know these parts very well. 

So we come to a point where we have our data. We have processed or engineered our variables. We have already selected the features that we want to use. So now it is time to build the machine learning models.

There are several models that we can build. We can build for example linear models like linear logistic regressions or models. We can also build decision trees based algorithms like random forest or gradient boosted trees. We can also build neural networks. This is just for supervised models but we can also build clustering algorithms or recommender systems you name it. 

And then when we pass the pre process data through our mothers we are able to get the predictions that they make.  Within need to evaluate the predictions that these models make to make sure that the models bring good business value. We evaluate the performance using different metrics depending on the project for classification.

- ROC-AUC
	- For each probability value:
		- How many times the model made a good assessment
		- How many times the model made a wrong assessment.

For example we can measure the ROC AUC you see which gives us an indication of how many times the more than makes a good assessment versus how many times the model makes the wrong assessment.

- Accuracy 

We can also measure the accuracy. Say for example the model gets it right 80 percent of the times.

- MSE, RMSE, etc

And we can measure as well the mean square error or the root squared error for linear models.

In fact there are multiple metrics that we can use and that you probably know very well but they're not the scope of the course.

So let's move on.

## Model Stacking - Meta Ensembling

Some of us may even go ahead and build the multiple machine learning algorithms and then build the meta model that takes in the predictions of all the initial models and combines them to make a better assessment of the target. This is called metal and assembly and we call if we wanted make this aspect part of the machine learning pipeline as well. 

In this course we will not introduce meta and assembling as part of the pipeline that we want to deploy because we want to keep it simple, but we will teach you enough to make you feel comfortable to include the meta assembling as part of your deployed pipeline if this is what you want and need to do. 

## Model Deployment

And now we are ready to begin the process of modern deployment. So far we have covered the machine learning pipeline from a theoretical perspective, in the next set of videos, I will walk you over the pipeline utilizing a Kaggle data set so we can see in action how we build a machine learning pipeline as data scientists and what steps we will need to deploy. What code we will need to deploy? 
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjk5ODg2OTY3LC0yMDM5MDA2NzUxLDE2MD
M2NDQzNywyMDU1OTA5NDQ3LDE0OTMyNTk3MjldfQ==
-->