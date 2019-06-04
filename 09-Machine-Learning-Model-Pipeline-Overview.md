> Written with [StackEdit](https://stackedit.io/).

# Section 2
## Machine Learning Model Pipeline Overview

In this section I will give you an overview of the typical machine learning pipeline. What do I mean by this? What I mean is that in this section we are going to revisit together, you and me, the different sequential steps of a typical machine learning model building project. What do we do first? What do we do next? Essentially what are the things that we normally do when we are building or developing a machine learning model.

Clearly these are the steps that we follow in business but maybe these are also the steps that you follow when you're building a project as a hobby.

In this lecture I will take you through the different steps of the machine learning model building pipeline. I will tell you what they are why they are important and which steps of the pipeline we need to consider when deploying a machine learning model. 

In the following videos, I will explain each one of the steps that we need to deploy in more detail. So let's go ahead and get started.

Here we can see a typical machine learning pipeline.

1. Gathering Data Sources
2. Data Analysis
3. Data Pre-processing - Feature Engineering
4. Variable selection - Feature Selection
5. Machine Learning Model building
6. Model building Business uplift evaluation

You can see that it is composed of several different steps. 

### 1. Gathering Data Sources

The first step is gathering the data. But what do I mean by gathering the data?  I mean collecting the data making the data available to the data scientists so they can go ahead and build the machine learning models. 

The data typically comes from different areas of the business itself, but also sometimes business by data from third parties or use data that is publicly available.

So we need to think, how are we going to make these data available to the data scientists so they can start analyzing it and making the machine learning models.

### 2. Data Analysis

Once the data is made available to the data scientists, the next step is **data analysis**. We need to get a good understanding of what the data is telling us. It is good practice to know the data well to get familiar with the variables to know how the variables are related to each other and to what we want to predict if this was a supervised case. We need to know what variables we can use, surely there are regulations in your business on which variables we cannot use.

### 3. Data Pre-processing - Feature Engineering

Once we have analyzed our data we are familiar with the variables under nature. The next step is **feature engineering**. After data analysis,  we should help gain a good understanding of whether we can use the variables as they are, but if we need to transform them before passing them onto a machine learning algorithm.

 During feature engineering we transform the variables to make them ready to be utilized in a machine learning model. I will go in more detail in the next lecture about this step because this is extremely important, but just to give you a flavor here by feature engineering I mean feel in missing values and coding categorical variables and dates among other things.

### 4. Variable selection - Feature Selection

After feature engineering, the next step is **features selection**. Why do we need to select features in the first place? Well there is a lot to say on why this tape is vital for modern deployment, and I will cover that in a dedicated lecture in this section as well, so stay tuned. But in a nutshell, feature selection means finding those variables that are the most predictive ones and build the mothers using only those variables instead of the entire dataset.

### 5. Machine Learning Model building

Finally the step that we take to like the most which is **model building**. Here we will typically build many, or maybe a few, different machine learning algorithms, analyze their performance and choose the one, or the few ones, that give us the best results.

We typically evaluate many statistical metrics like the **means squared error** for regression or the **accuracy** or **area under the ROC curve** for classification. 

But these metrics are not enough in business. In business we need to go ahead and see how the model performance that we evaluated using statistical metrics relate to business value. So we evaluate what is the **uplift** in the business value. And here we can measure different things depending on the business area that we're working on. For example, if we were building models for fraud we would evaluate the amount of money that we would not disburse to fraudulent applications or if we were building mothers for advertising, we can estimate the value that the new customers would bring if we were to use the model. 

And once and only once all these stages are complete, once we build the model and it brings real business value, then we're happy to proceed to the main topic of this course which is more the deployment.

### Model Deployment
Now we are ready to deploy our model and what do I mean by being ready to deploy our model?  by this, by deploying our machine learning model, I mean putting our model in the cloud or in any other system where it can be then accessed by our other systems in the business in order to get its predictions, this way and only by deploying our models by making our models available to other business systems we can then extract the real and maximum value of our machine learning algorithm.

Okay. So what does it mean deploying a model in practical terms what do we need to do?  So going back to the machine learning pipeline which steps of the pipelines are the ones that we need to deploy. Is it just the model? Not really.That would be really easy. We need to deploy at least these three steps of the pipeline we need to make sure that the model that we put in the cloud or in any other of our computer systems is capable of taking into data and transforming its variables and then use only the selected variables to then make the predictions utilizing the mothers or algorithms that would build.

So in essence we need to deploy an entire data and machine learning pipeline. That is why we speak of pipelines and not just of models. We need to deploy an entire pipeline, an entire sequence of steps that will allow us to get the data into where our mode is located, transform the data, field missing values and called categorical variables etc. Then select or somehow use only the variables that we agreed are the most predictive ones and then
utilize those variables to make a mathematical calculation utilized in either bespoke or off the shelf algorithms and then be able to get those predictions out and send them back to our business systems.

So this is what more than a deployment means. This is what we need to deploy onto our other systems or onto the cloud. So in the rest of this section I will take you through each one of these steps so we get a better understanding of what they are and why they are important and in the rest of the course we will explain what we need to do to deploy each one of them in the form of an entire machine learning pipeline.

See you in the next lecture.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTk1NjExMjM1NywtMTUyMDI2MjI2MywxNz
c1OTgyOTI4XX0=
-->