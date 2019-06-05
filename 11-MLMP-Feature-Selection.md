
> Written with [StackEdit](https://stackedit.io/).

# Machine Learning Model Pipeline:
## Feature Selection

  
In this video we will discuss the next step of the machine learning pipeline which is features election. What do I mean by features selection? Features selection refers to algorithms or procedures that will allow us to find the best subset of features from all the variables present in our dataset. This is, the process to identify the most predictive features. 

At the beginning of the feature selection process, we start with the entire dataset with all the variables and by the end of the feature selection process we end up with a smaller number of features which are typically the most predictive ones.

## Why Do We Select Features?

- Simple models are easier to interpret
- Shorter training times
- Enhanced generalization by reducing overfitting
- Easier to implement by software developers -> Model production
- Reduced risk of data errors during model use
- Data redundancy

But the way that we select features to begin with.

I couldn't possibly emphasize more the importance of selecting features when the machine learning models that you are building are to be used within a business. 

Why is feature selection so important? For multiple reasons really.

- First simpler mothers are easier to interpret by the consumers of the models. So those people who act on the decisions that the mothers make will need to understand those decisions. In this sense mothers built using ten features are easier to understand than models built using hundreds of features.

- Second, shorter training times. It takes less time to train, but more importantly, less time to score if the mother uses fewer features.

- Third, we may achieved enhanced generalization by reducing overfitting if we use less features.

- Fourth,  and particularly important for this course is that models that are built on smaller datasets utilizing fewer features are easier to implement, and by this I mean to fully integrate with the business systems by the software developers. Models built using fewer features are easier to put into production. Why is that?

	- First, we need to ship smaller Jason messages between the business systems and the model.
	- Second, we need to write less code to process those features and we also need to write less code to handle potential errors.

- But let's continue with the advantages of feature selection utilizing less number of features minimizes the risk that we may encounter due to data errors. 

- And of course more often than not data is redundant which means that many features provide the same information. So why should we use them all when we're building our models.

## Reducing features for model deployment

- Smaller json messages sent over to the model
	- Json messages contain only the necessary variables / inputs
- Less lines of code to error handling
	- Error handlers need to be written for each variable / input
- Less information to log
- Less features engineering code

Let's go back to why it is important to deploy models using the less amount of features possible. As

I said we will need to build smaller Jason messages to be sent to and from the model to our other business systems. This Jason messages contains the variables that we need to input into our model and then they will take the predictions out onto our systems.

We also need to write less lines of code for error handling. For example lines to handle the previously unseen values, as we were discussing in the previous lecture, typically we write error handlers for each and every variable we send into our model.

If we use less features also then we need to log less information toward databases. Typically when we put our mothers in production and we write production code, we log all the intermediate steps to have some sense of how the process is working. 

And of course the less variables we use the less code we need to write to engineer those variables. Remember that we need to include this step as part of the pipeline.

As a data scientists, we need to keep this in mind so that we don't build models that will overwhelm our developers and also our business systems.

## Variable Redundancy

- Constant variables: only 1 value per value
- Duplication: same variable multiple times in the dataset
- Quasi - constant Variables: >99% of observations show same value
- Correlation: Correlated variables provide the same information

We often find that many of the body was present in our data sets are redundant. So why should we ship them all to our models in the cloud? 

What do I mean by redundancy? What often we find variables that are constant, these are variables that take one and only one value, the same value for all the observations, 

We also find quasi-constant variables. This is variables that take the same value for the great majority of the observations except for a tiny proportion. These variables tend to be quite useless to make predictions. So we may as well get rid of them.

We also find duplications. This is two variables potentially even with different names but that otherwise identical in all of their values.

And finally we also find correlation and correlated parables tend to provide the same information about the target that we want to predict. So there is no need to use the two variables if they're correlated including one of them already adds most of the value that can be extracted.

## Feature Selection Methdos

- Embedded methods
- Wrapper methods
- Filter methods

There are several ways in which we can select features. I am not going to go into much detail because this is not the scope of this course, but just to give you a flavor, there are three umbrella terms under which we group the different feature selection algorithms.

- One group corresponds to the embedded methods.

- Another group to the wrapper methods.

- And then we have as well the filter methods.

All of these group of algorithms have advantages and disadvantages. Let's go over them.

### Filter methods

Let's for example think about filter methods. Among the filter methods we find for example simple statistical tests like ANOVA or keys squared. These methods are independent of the algorithms we intend to build at the end, and they discriminate features based only on the features characteristics.

Why are these methods good? 

- Well they often provide a quick first step to remove a big chunk of your features, particularly if you're using big datasets with lots of variables. 
- These methods filter methods are model agnostic. So the selective features should be suitable for any one algorithm you want to build and they are of

course fast for computation on the downside features and methods look at one feature at the time so

they do not capture feature redundancy or feature interaction.

And at the end of the day they tend to provide the lowest model performance.

Let's move on to wrapper methods.

Wrapper methods do take the algorithm we intend to build into account when selecting the features and

they do not evaluate one feature at the time they rather evaluate a group of features wrapper methods

are also known as greedy algorithms because in theory they evaluate all possible feature combinations

and only then decide which one is the best.

There are a few ways in which we can achieve this but I will not go over them right now.

So let me just tell you that the advantages of using wrapper methods are that they consider feature

interaction and that they tend to find the best feature combination for a given algorithm.

On the downside they are not model agnostic which means that the combination of features they found

for a certain algorithm may not be the best for a different algorithm and proper methods in both building

a different machine learning model for each feature combination.

So they are computationally very expensive to the point that they are often impracticable.

So then we come to embedded methods and they tend to have the suite of both worlds embedded methods

referred to those features election procedures that could occur with actually training the machine learning

algorithm the classical example of a Method Method is the loss of regression and also the feature importance

that we derive from fitting tree based algorithms on the good side.

These methods do consider that feature interaction and tend to provide a very good model performance.

They are faster than rapid methods and tend to produce models that are more predictive than those based

on features selected by filter methods.

On the downside they are not model agnostic so features selected by random forest for example may not

be the best to use in a linear model.

So what do we do with feature selection and how though we make it part of the pipeline we can of course

make feature selection part of the pipeline.

But the issue is better resolved if we select the features ahead of building the pipeline that we want

to deployed and then make the list of the selected features.

Part of the pipeline that we want to deploy and this is what we're going to do in this course.

We're not going to make the algorithm to select features part of the pipeline.

We're rather going to come up with a list of features that we think that are most important and we are

going to make that list of features.

Part of the pipeline in the next section of the course I will cover more why we think that this is the

way forward.

And what are the advantages and disadvantages of making the feature selection algorithm per say part

of the pipeline for now.

See you in the next video where I will go over building the machine learning models.
<!--stackedit_data:
eyJoaXN0b3J5IjpbODgwODIzMDQ5LDE4NzQ3MTA0MTEsLTIxND
E2MzkxNDEsLTc2NjczNzk2Nl19
-->