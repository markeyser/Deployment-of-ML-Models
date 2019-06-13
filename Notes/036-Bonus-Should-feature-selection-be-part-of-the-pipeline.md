# Section 4: Building a Reproducible Machine Learning Pipeline
## 36. Should feature selection be part of the Machine Learning automated pipeline?

Should we make feature selection part of the automated machine learning pipeline?

In this section we will introduce the challenges and advantages of doing so and hopefully live you in a position where you can make the best decision that fits your business needs.

[image]

Often in business we want to build pipelines that can be continuously integrated and continuously deployed.

This means that we build a model once, for the first time, we create the entire deployment pipeline, as we will show you throughout the course.

We create tests for the continuous integration, and we make it so that once those tests are fulfilled, the model is automatically deployed. So that it is available to the other business systems to make calls to it.

If say the models lose performance or for business reasons we want to refresh it every say three or six months. We would then refresh or retrain the model over the newly acquired or more recent data.

And as the pipeline is set in continuous integration continuous deployment framework, the pipeline will
automatically run the integration tests and if passed it will deploy the model into production. This means that you retrained model is automatically available to your business systems.

### Feature selection in CI/CD

Advantages

- Reduced overhead in the implementation of the new model
- The new model is almost immediately available to the business systems

Disadvantages

- Lack of data versatility
- No additional data can be fed through the pipeline, as the entire processes are based on the first dataset on which it was built

This continuous integration continuous deployment pipeline has a tremendous advantage which is that it reduces the overhead to the implementation or deployment of the new machine learning model.

The model as soon as it is retrained is made available to the business systems, the new version of it. However, as an entire pipeline is built over one original data set it is not versatile enough to accommodate for new variables coming from other data sources.

In business, as we improve our machine learning models, together we create them better models. We also include new sources of data that we acquire from third parties and new vendors. So integrating featuring selection as part of the continuous integration continuous deployment pipeline is often not the best solution.

Implementing feature selection in the continuous integration continuous deployment machine learning pipeline ensures that from all the available features only the most predictive ones will be selected to train the model. And this potentially helps to reduce overfitting at the time that enhances model interpretability.

However, it does not bring forward the other benefits from feature selection that we discussed in previous sections which are the need to write less code to handle all the features. Because a feature selection is made part of the deployment pipeline. This means that we still need to write production code to engineer all the available features in the data set. We need to write more unit and integration testing code as well as more code to handle potential errors.

### Feature selection in CI/CD

### Suitable:

- Model build and refresh on same data
- Model build and refresh on smaller datasets

### Not suitable,
- If model is built using datasets with a high feature space
- If model is constantly enriched with new data sources

So what is it suitable to introduce features election as part of the pipeline?

### Suitable

If the model is generally built and refreshed on the same data and not a lot of change in the data sources is in the roadmap then this is probably the best long term solution particularly if the models are trained on data sets with a reduced number of features.

However, if the models are built over data sets within immense number of features that is from a production perspective not the way forward as it will involve a very big piece of production code to engineer and handling errors and tests for all those features.

### Not suitable

Implementing features election as part of the pipeline is also
not suitable, if we are constantly adding new data sources to train and make our models more predictive. This means that our additional features are always changing.

In this case it is more convenient to spend some time on the research and development of the machine learning model, make sure we understand the features well, and select only those that are real value, and then create the pipeline only utilizing those selected features.

### Feature selection in the scikit-learn pipe

So how can you integrate feature selection as part of the machine learning pipeline in production code?

What very easily.

[image]

You only need to add these transformations step right in front of the training of the machine learning model.

This is the pipeline that we wrote to deploy our house regression model.

If we wanted to add a layer of dimensionality reduction in this case I chose BCA I only need to add

this algorithm in the pipeline right here so what about if you want to implement a selection algorithm

that is not available inside could learn.

Well there's not a problem either.

You only need to write a transformer following the psychic learn style as we did for the different steps

of feature engineering.

Here I show you the skeleton.

You can initialize your transformer with some parameters that suit your selection algorithm in the FIT

section.

You will write the code that actually selects the features whatever that is and then returns the list

of the selected features and you can also return other attributes if you need to do so.

And the transform method will reduce your training set to only the selected features.

Then the pipeline will train the machine learning model you specify on the reduced training set and

that's it really.

So that will be all for this video.

I hope you enjoyed it and see you in the next one.
