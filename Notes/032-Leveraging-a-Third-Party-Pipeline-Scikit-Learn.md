# Section 4: Building a Reproducible Machine Learning Pipeline
## 32. Leveraging a Third Party Pipeline: Scikit-Learn

### Scikit-Learn and `sklearn.pipeline`

In this video I will show you how to write production code to deploy a machine learning pipeline leveraging the power of a third party pipeline. In this case, leveraging the power of the scikit-learn pipeline.

So, why scikit-learn?

- Scikit-Learn is a Python library that provides a solid implementation of a range of machine learning algorithms.
- Scikit-Learn provides efficient versions of a large number of common algorithms.
- Scikit-Learn is characterised by a clean, uniform, and streamlined API.
- Scikit-Learn is written so that most of its algorithms follow the same functionality

Once you understand the basic use and syntax of Scikit-Learn for one type of model, switching to a new model or algorithm is very straightforward.

Scikit-Learn provides useful and complete online documentation that allows you to understand both what the algorithm is about and how to use it from scikit-learn.

Scikit-Learn is so well established in the community, that new packages are typically designed following scikit-learn functionality to be quickly adopted by end users, e.g, Keras, MLXtend.

Scikit-Learn is a python library that provides a solid implementation of a range of machine learning algorithms. In fact, scikit-learn provides efficient versions of a large number of common algorithms.

Scikit-Learn is characterized by a clean uniform and streamlined API

Scikit-learn is written so that most of its algorithms follow the same functionality. This means that once you understand the basic use and syntax of scikit-learn for one type of model, switching to a new model or algorithm is very straightforward.

scikit-learn provides also useful and complete online documentation that allows you to understand both what the algorithm is about and how to use it from scikit-learn.

In fact, scikit-learn it is so well established in the community, that new packages are typically designed following scikit-learn functionality so that they can be quickly adopted by end users. And clear examples of these are Keras for neural networks and MLXtend.

#### How is scikit-learn organized?

- **Transformers** - class that have `fit` and `transform` method, it transform data

    - Scalers
    - Feature selectors
    - One hot encoders

- **Predictor** - class that has `fit` a `predict` methods, it fits and predicts.

    - Any ML algorithm like Lasso, decission trees, svm, etc

- **Pipeline** - class that allows you to list and run transformers and predictors in sequence

    - All steps should be transformers except the last one
    - Last step should be a predictor


scikit-learn has three main type of objects. The **Transformers** the **predictors** and the **pipeline**.

Transformers are objects that aim to transform the data. They typically carry the `feet` and `transform` methods.

And among the transformers, we find the **feature scalar**, the **feature selectors** and **one-hot encoders** for categorical variables.

**Predictors** are objects that make predictions. And this typically includes all the machine learning algorithms available in scikit-learn.

Predictor objects from scikit-learn carry the `feet` and the `predict` methods.

Finally the *pipeline* object is an object that will allow you to run the transformers and predictors in a sequence. So, the pipeline is a class that allows you to list and run transformers on predictors.

The characteristics of the scikit-learn pipeline is that you can list as many transformers as you want and all of them except the last one should be transformers and, the last step of the pipeline should be a predictor.

Let me show you an example of the scikit-learn pipeline.

[image]

Here it is a good example of how to use the scikit-learn transformers and predictors individually, which is what we have been doing in the notebooks in Section 2 and, otherwise, how to make them part of the scikit-learn pipeline instead.

In this example here, we are aiming to extract features from text using the `CountVectorizer` and then to transform this feature into frequencies related to the overall frequency of the term using the `TfidfTransformer` transformer and then we want to build a classifier `SGDClassifier`.

Therefore we would call these two transformers from sciket-learn (`CountVectorizer` and `TfidfTransformer`) and we will call one predictor from scikit-learn, the `SGDClassifier`.

```Python
vect = CountVectorizer()
tfidf = TfidfTransformer()
clf = SGDClassifier()

vX = vect.transform(Xtrain)
tfidfX = tfidf.transform(vX)
predicted = clf.predict(tfidfX)
```

So this is a sequence of events. First we transform the data with the `CountVectorizer`, then we transform the data with the `TfidfTransformer` and then we make the predictions `SGDClassifier`.

So the way we normally run it is like you can see here. We take the first transformer, we fitted to the training set (`CountVectorizer(Xtrain)`) and then we transformed the training set, and we captured the transformed  training set in `vX`.

Now we need to fit the next transformer. In this case the `TfidfTransformer` so we fitted to the transformed data coming from the previous step `TfidfTransformer(vX)`.

And then we transform this data again and this transform data that now we call `tfidfX` is the one that we're going to use to fit the classifier `SGDClassifier(tfidfX)`, which is what we do in the next step.

And by combining the feet with the predict we are able to obtain the predictions as well from the same training set `predicted`.

```Python
# Now evaluate all steps on test set
vX = vect.transform(Xtest)
tfidfX = tfidf.transform(vX)
predicted = clf.predict(tfidfX)
```

If now we want to evaluate the transformations and predictions in a different set, let's say for example the test set, what we need to do is to just call the transformers in a sequence, transform the data, store the transformed version into a different version of the data and then call the second transformer, and transform the previously transform data and then call the predictor and make the predictions on these data that was already transformed by the two Transformers.

So this is a pipeline in essence, this is a sequence of transformations followed one by one by the other and then the prediction.

So we can write it like this or, we can make all of these steps part of the scikit-learn pipeline as follows:

```Python
pipeline = Pipeline([
    ('vect', CountVectorizer()),
    ('tfidf', TfidfTransformer()),
    ('clf', SGDClassifier()),
])
predicted = pipeline.fit(Xtrain).predict(Xtrain)
# Now evaluate all steps on test set
predicted = pipeline.predict(Xtest)
```

So here, we create an object called `pipeline` and we call the pipeline from scikit-learn `Pipeline()`. So this one is an object from scikit-learn and then we indicate the order of the transformers that we want to run.

So the first transformer we give it the name. In this case we call it `vect` and we pass the object from scikit-larn `CountVectorizer()`.

Then we pass the second transformer. We use the name `tfidf` and, we indicate the transformer that we want to use `TfidfTransformer()`.

And finally we pass the classifier again. We give it a name `clf` and then we pass the classifier that we want to use from scikit-learn `SGDClassifier()`.

So now we have the pipeline, we have the ordered sequence of transformations and predictions that we want to make. Remember that all of the objects need to be transformers except of the last one, that can be a predictor, but you cannot put more than one predictor.

And once you have the pipeline the only thing that you need to do is to call the `pipeline.fit(Xtrain)` on the train set. And this will fit all the transformers and predictors. And if you want to get the predictions out of it you need to add `.predict(Xtrain)`.

Also on the training set the original version, the raw data, and you will get the predictions that come after a fit in the transformers and the predictors `predicted` and then making the predictions and transformations on the data.

If instead you want to use the pipeline to predict a new data like the test set, the only thing that you need to do is to call the `pipeline.predict(Xtest)` and pass the raw test set.

So this way you can see how in two lines of code you can concentrate this block of code on this block of code here (first code).

So the pipeline is a very elegant way to order, to determine the sequence in which you're going to run all your transformations and finally use your predictions. And this is what we're going to use to deploy our machine learning mothers.

#### How can we leverage the use of the scikit-learn pipeline then?

**Feature Creation and Feature Engineering steps as Sckit-Learn Objects**

- **Transformers** - class that have `fit` and `transform` method, it transform data
- Use of scikit-learn base transformers (templates)
    - Inherit class and adjust the fit and transform methods
- Click here for and [example](https://github.com/solegalli/deploying-machine-learning-models/blob/master/packages/regression_model/regression_model/processing/preprocessors.py)

Well first by using this I could learn pipeline.

We do not need to write a custom pipeline because I could learn already took care of that part.

So instead but we need to do is to write code for all of our feature engineering steps in a way that

can be used.

Within this I could learn pipeline.

So we need to build individual transformers that allow the fit transform cycle land functionality so

this way we can integrate these transformer.

This feature engine steps as part of this I could learn pipeline ahead of calling the predictor.

It sounds really more difficult than what it is.

Why.

Well because sacred land already has templates for these transformers so that the only thing that you

need to do is to call this template inherit all its methods and only modify the fit and transform parts

of it so that they do what your future engineers steps require them to do.

So let me show you how to do that for our house price data set project.
