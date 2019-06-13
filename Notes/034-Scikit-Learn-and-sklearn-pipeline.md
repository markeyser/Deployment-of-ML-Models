# Section 4: Building a Reproducible Machine Learning Pipeline
## 34. Scikit-Learn and sklearn pipeline

### Advantages

- Can be tested, versioned, tracked and controlled
- Can build future models on top
- Good software developer practice
- Leverages the power of acknowledged API
- Data scientists familiar with Pipeline use, reduced over-head
- Engineering steps can be packaged and re-used in future ML models

### Disadvantages
- Requires team of software developers to build and maintain
- Overhead for software developers to familiarise with code for sklearn API ⇒ difficulties debugging

### Advantages

So what are the advantages of using the Scikit-learn pipeline?

Well again, this code is well designed from the start, so it can be tested, versioned, tracked and controlled just like every normal piece of software.

We can build future models on top or we can embedded as part of pre-existing pipelines.

It follows good software developer developer practice

And it leverages the power of unacknowledged API which in this case is scikit-learn

In addition data scientists are familiar with this pipeline so it reduces the overhead between research and production and empowers data scientists to participate in the deployment of models.

And the feature engineer steps can be made part of a python package and then shared across multiple machine learning deployment projects.

So in this sense you can write your Transformers, your feature engineer in steps once, and then you can use them over and over across all your different models all the different modes that you want to deploy.

### Disadvantages

On the downside it does require software development skills and there is an overhead in this case cost by the fact that software developers may not be familiar with scikit-learn pipeline and then they will find they may find debugging challenging.

Overall, This is my recommended solution to deploy models as it capitalizes on the use of a very well established python library and allows full versatility and the possibility to incrementally build new code new pre-processors that can be part of a library that you can call from all your various different deployed machine learning models.

Before closing the video, I have gathered here in this slide a list of resources on why we should be using scikit-learn as part of deploying models in business and also several tutorials to get you more familiar with the use of scikit-learn pipelines If you are in yet so.

- [Introduction to Scikit-Learn](https://www.oreilly.com/ideas/intro-to-scikit-learn)
- [Six reasons why I recommend Scikit-Learn](https://www.oreilly.com/ideas/six-reasons-why-i-recommend-scikit-learn)
- [Why you should learn Scikit-Learn](https://hub.packtpub.com/learn-scikit-learn/)
- [Deep dive into SKlearn pipelinesfrom Kaggle](https://www.kaggle.com/baghern/a-deep-dive-into-sklearn-pipelines)
- [SKlearn pipeline tutorial from Kaggle](https://www.kaggle.com/sermakarevich/sklearn-pipelines-tutorial)
- [Managing Machine Learning workflows with Sklearn pipelines](https://www.kdnuggets.com/2017/12/managing-machine-learning-workflows-scikit-learn-pipelines-part-1.html)
- [A simple example of pipeline in Machine Learning using SKlearn](https://towardsdatascience.com/a-simple-example-of-pipeline-in-machine-learning-with-scikit-learn-e726ffbb6976)
