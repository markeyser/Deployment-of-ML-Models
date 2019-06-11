
# Data Science Chat notes

## Sections [01 & 02]

- What is Model Deployment?
- Role of Data Scientists in Model Deployment
    - Model monitoring
    - Testing challenging new Models
    - **Writing production-level code**: how to transform that code (prototyping / research) into code that can be used in production. So first we will show you the best practices around writing production code.
    - **Testing**: Then we'll introduce you to testing to corroborate that research and production models produced the same outcome given the same data - continuous integration.
- Machine Learning - Research Environment: Machine Learning pipeline overview [02] `*`:
    - Data Gathering
    - Feature engineering
    - Feature selection
    - Machine Learning model building
    - Model assessment
    - Finally you will learn about the importance of building reproducible machine learning pipelines right from the start of any machine learning project.[02]
- Building a reproducible ML pipeline: how to transform your Jupyter notebook into production ready code [02]:
    - Different ways utilized in the industry
    - Procedural programming
    - OOP with a custom pipeline
    - OOP with third party pipeline
    - Recommendations
    - Bonus: should we integrate feature selection into the production pipeline?

`*` Here we will focus mostly on the deployment aspect of things only covering things about machine learning when they are important for more deployment.[03]

## Some notes to use

- No machine learning model brings true value until it is fully integrated and can be used to score real data. So model deployment is the most important and yet most difficult part of any typical **machine learning pipeline**.

- A slide covering the whole model deployment process - overview.
- In section 13: Deploying with Big Data - Deep Learning: this out of the spoke of this chat.
- Talk about the most popular ML libraries for model deployment: scikit-learn, PySpark and Keras on the top of TF.
- Include resources to get familiar with each area i.e. scikit-learn pipeline.[03]
- From[03] mention some where that being able to manage Environments, Git, scikit-learn pipelines, OOP, etc. are the required skills for model deployment for a data scientist.
- From [04] first paragraph about going from Jupyter notebook to integrated API. and see the paragraph for data engineers.
- From [05] how to download the Kaggle dataset of this course. Explain why this dataset is a better dataset than the classical Boston house pricing dataset.

## What is model deployment? [01]

- Model deployment is the process of integrating a machine learning model into an existing production environment so that we can use it to make business decisions based on live or future data. It is one of the latest stages in the machine learning pipeline and potentially the most challenging.

## Why is model deployment so important? [01]

- For a business to be able to leverage the power of a machine learning model the model needs to be fully deployed into production. If we cannot get practical insight from the model; that is, if we cannot score like data or real data with it, then the impact of the model is severely limited.
- Model deployment is one of the most difficult processes in the machine learning pipeline and also the one that will allow us to extract real value from our model.
- Model deployment requires coordination between data scientists, I.T. teams and DevOps, software developers and business professionals to make sure the model works reliably in their organization's production environment.
- This represents a major challenge because there is often a discrepancy between the programming language in which the machine learning model is written and the languages your production system can understand, and recoding the model can extend the project timeline by weeks or months.
- In order to get the most value out of the machine learning models, It is important to deploy them into production as seamlessly as possible so the business can start using them to make practical decisions.
