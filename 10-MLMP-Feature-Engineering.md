> Written with [StackEdit](https://stackedit.io/).

# Machine Learning Model Pipeline
## Feature Engineering

  
If you've seen the first video, you're not familiar with the entire machine learning pipeline and you
got a flavor of what it is and that we need to deploy an entire pipeline and not just the machine learning
algorithms.

 In the previous section, we discussed that the first step of the pipeline that we need to consider is feature engineering. So what is feature engineering? In this video we're going to revisit many of the feature engineering steps that you can undertake depending on the machine learning model you're building to preprocess your data and leave it suitable to use to train machine learning mothers and make predictions.

So by the we need to engineer features that are a variety of problems that we can find in the variables

in our datasets.

One of the problems is missing data.

This is the absence of values for certain observations within a variable.

A second aspect that we need to tackle is the presence of labels in categorical variables.

This is the values of the variables are strings rather than numbers.

And we can't use them as such in machine learning mothers certainly not in python using so I could learn

a third consideration to keep in mind is the distribution of the variables fundamental variables and

specifically whether they follow a gosh distribution or if they are rather skewed for some algorithms.

The presence of outliers is also the true mental outliers are unusual or unexpected by use within a

variable.

This is values that are extremely high or extremely low compared to the majority of all the other values

for that same variable

so missing data as I said is the absence of values for certain observations within a variable and it

affects of course all machine learning models in the sense that we can't really feed observations to

a machine learning more than that contained missing values not a few since I could learn at least.

So there are a variety of reasons why data could be missing a value can be lost or not stored properly

for example during data storage or the value does not exist.

For example if the variable comes from the deviation of two other variables and the second variable

takes a value zero the division by zero does not exist.

But he did it that was obtained from a survey say and the person refuses to answer a question that could

also be a missing value.

So we need to be prepared to fill in those missing values with some sort of number to use in machine

learning.

The second problem I mentioned is the presence of flavors or strings in categorical variables.

These problems come in three flavors.

The first is the cardinality of the variable.

And by this by cardinality I mean the number of different flavors or categories that the variable can

take in fact variables with big number of categories tend to dominate over variables with smaller number

of categories at the time of with the machine learning models and this is particularly true for three

based algorithms three base methods tend to over fit two variables with high cardinality second problem

is the presence of rare labels rare labels may also cause trees to outfit.

But most importantly they represent an operational problem because they are rare.

Some of these labels because they are rare because they are infrequent because they are present only

in a small proportion of the observations will appear only in the training set and some of them will

appear only on the test set.

So the mother will not know what to do with those labels that are present only in the test set and have

never been seen during training as they were not were present in the training set.

So this step is extremely important at the time of modern deployment because it involves additional

steps that we need to take to tackle unseen by use.

We will show you more on this in an inner dedicated section.

And finally for categorical variables the presence of labels themselves.

This is the presence of strings when we actually need numbers to fit machine than mothers use since

they could learn is something that we need to address in a step that is called categorical variable

encoding

speaking of numerical variables instead what we normally consider when building machine and mothers

is the distribution of the vibes.

What do I mean by this linear motors assume that the variables follow a Gaussian distribution.

So if the variables in our data sets are not Gaussian we may choose to apply some transformations.

Other mothers like support vector machines and neural networks do not make any variable assumptions.

However a better spread of the values over a larger range tends to improve the predictive performance

of these algorithms.

We also mentioned outliers was our outliers but if you remember outliers are values that are extremely

low or extremely high compared to the remaining values for that variable outliers may affect certain

machine learning mothers.

You're probably familiar with how an outlier may affect a linear regression.

Look for example at this illustration.

Here you see clearly how the presence of the outlier deviates the straight line from what otherwise

seems to be the relationship of the majority of the values with the target.

And there are other algorithms that are sensitive to outliers as well.

Think for example are the boost at the most is sensitive to outliers because this algorithm puts tremendous

weights to the outliers as the different threes are built to try and correct the prediction that the

previous three made wrongly.

And this tends to cost over fitting and above generalization.

And finally the magnitude of the features affect us.

Well model performance think for example in a length variable.

If the variable is in meters and we change it we transform it into kilometers.

The coefficient that multiplies that bearable will also change if what we are building is a linear in

than from a different perspective.

If you're trying to predict house price and we have one body able that is the area intense of square

kilometres and a different barrel is the number of rooms that varies from one to 10 in a linear model

the variable that takes the larger values will have a predominant role over the house price.

So in this case the area variable will be more important to determine the price of the house.

However we know that the number of rooms also plays a role.

So what can we do to make that variable count as well.

In fact most of the algorithms are sensitive to scale.

If you look at this light I have listed those algorithms that for one reason or another are sensitive

to the magnitude of the variable.

So linear mothers who've seen y but also support vector machines and neural networks are supposed to

converge faster and find the optimal hyper plane faster when using features with a similar scale.

And of course all the distance based algorithms are also sensitive to the scale of the features.

So I hope I gave you a flavor about why we need to engineer the variables that we're going to use in

our machine learning models and because this is important to build good algorithms.

We need to make sure that this step takes part of our deployed machine learning pipeline so that closes

the lecture and see you in the next one.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU0MTY4MjcwOCwtMTMxNDI5NzgzMF19
-->