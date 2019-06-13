# Section 4: Building a Reproducible Machine Learning Pipeline
## 29. Production Code: Overview

### Machine Learning Pipeline: Production

In this section we will introduce you to the different ways in which you can write code to deploy a machine learning pipeline. And then we will give you our preferred option and explain to you why we think this is the best solution for the majority of business cases. So let's go ahead and get started.

In Section 2, we covered the different steps of the machine learning pipeline. We went over them with slides and then we walk you through a practical example. And then, by the end of section 2, we produced a Jupiter notebook that contains the sequence of steps that we need to create our machine learning model.

The notebook contains steps to engineer the variables, to use only the selected features,  and then to train the models and make predictions using these models. So, briefly, these three steps of the pipeline which are cycled in red are the ones that we need to write production code for.

[image pipeline]

### Towards deployment code

For most of you in the course, if you have never deployed a machine learning model, the most likely scenario is that you will have your models and the feature engineering steps in Jupyter notebooks. Just like the one we had at the end of section 2 of this course.

And from that starting point, so from your Jupiter notebook, you want to transition into production code for model deployment.

Specifically, you want to write production code to create and transform features, to select the variables that you're going to use and, to build and train the machine learning algorithms. And finally you want to make the predictions with this machine learning algorithms.

So in essence, you need to write production code for the entire machine learning pipeline.

Remember that we do not deploy models using Jupyter notebooks, we deploy models using scripts. So you have to transition from a Jupiter notebook onto a Python script. Just like the one I show you here on the right.

### How to write deployment code for ML

- Procedural programming
- Custom Pipeline
- Third Party Pipeline Code

How can we write production code for an entire machine learning pipeline?

There are three main ways.

The first one is using procedural programming, which in essence, consists of writing a sequence of functions like the one we were writing all alone in our Jupiter notebooks.

The other two ways involve using object oriented programming and building either a custom pipeline that calls the procedures in order or leveraging the power of a third party pipeline which for us is going to be the scikit-learn pipeline.

In the next three videos, I will describe in more detail these three ways of writing production code.
