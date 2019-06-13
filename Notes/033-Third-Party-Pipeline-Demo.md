# Section 4: Building a Reproducible Machine Learning Pipeline
## 33. Third Party Pipeline: Create Scikit-Learn compatible Feature Transformers

So let me show you how to do that for our house price Project.

So in this script here, we're going to write all the pre processors that we need in order to engineer the variables from the house price data set and leave them ready to use in the linear regression model that will allow us to get the predictions.

So I mentioned that we need to build them so that they are compatible with Scikit-learn pipeline and I also told you that Scikit-learn already has templates(`BaseEstimator` and `TransformerMixin`) that will allows us to do this in a very simple manner.

```python
import numpy as np
import pandas as pd
from sklearn.base import BaseEstimator, TransformerMixin

from regression_model.processing.errors import InvalidModelInputError


class CategoricalImputer(BaseEstimator, TransformerMixin):
    """Categorical data missing value imputer."""

    def __init__(self, variables=None) -> None:
        if not isinstance(variables, list):
            self.variables = [variables]
        else:
            self.variables = variables

    def fit(self, X: pd.DataFrame, y: pd.Series = None
            ) -> 'CategoricalImputer':
        """Fit statement to accomodate the sklearn pipeline."""

        return self

    def transform(self, X: pd.DataFrame) -> pd.DataFrame:
        """Apply the transforms to the dataframe."""

        X = X.copy()
        for feature in self.variables:
            X[feature] = X[feature].fillna('Missing')

        return X


class NumericalImputer(BaseEstimator, TransformerMixin):
    """Numerical missing value imputer."""

    def __init__(self, variables=None):
        if not isinstance(variables, list):
            self.variables = [variables]
        else:
            self.variables = variables

    def fit(self, X, y=None):
        # persist mode in a dictionary
        self.imputer_dict_ = {}
        for feature in self.variables:
            self.imputer_dict_[feature] = X[feature].mode()[0]
        return self

    def transform(self, X):
        X = X.copy()
        for feature in self.variables:
            X[feature].fillna(self.imputer_dict_[feature], inplace=True)
        return X


class TemporalVariableEstimator(BaseEstimator, TransformerMixin):
    """Temporal variable calculator."""

    def __init__(self, variables=None, reference_variable=None):
        if not isinstance(variables, list):
            self.variables = [variables]
        else:
            self.variables = variables

        self.reference_variables = reference_variable

    def fit(self, X, y=None):
        # we need this step to fit the sklearn pipeline
        return self

    def transform(self, X):
        X = X.copy()
        for feature in self.variables:
            X[feature] = X[self.reference_variables] - X[feature]

        return X


class RareLabelCategoricalEncoder(BaseEstimator, TransformerMixin):
    """Rare label categorical encoder"""

    def __init__(self, tol=0.05, variables=None):
        self.tol = tol
        if not isinstance(variables, list):
            self.variables = [variables]
        else:
            self.variables = variables

    def fit(self, X, y=None):
        # persist frequent labels in dictionary
        self.encoder_dict_ = {}

        for var in self.variables:
            # the encoder will learn the most frequent categories
            t = pd.Series(X[var].value_counts() / np.float(len(X)))
            # frequent labels:
            self.encoder_dict_[var] = list(t[t >= self.tol].index)

        return self

    def transform(self, X):
        X = X.copy()
        for feature in self.variables:
            X[feature] = np.where(X[feature].isin(
                self.encoder_dict_[feature]), X[feature], 'Rare')

        return X


class CategoricalEncoder(BaseEstimator, TransformerMixin):
    """String to numbers categorical encoder."""

    def __init__(self, variables=None):
        if not isinstance(variables, list):
            self.variables = [variables]
        else:
            self.variables = variables

    def fit(self, X, y):
        temp = pd.concat([X, y], axis=1)
        temp.columns = list(X.columns) + ['target']

        # persist transforming dictionary
        self.encoder_dict_ = {}

        for var in self.variables:
            t = temp.groupby([var])['target'].mean().sort_values(
                ascending=True).index
            self.encoder_dict_[var] = {k: i for i, k in enumerate(t, 0)}

        return self

    def transform(self, X):
        # encode labels
        X = X.copy()
        for feature in self.variables:
            X[feature] = X[feature].map(self.encoder_dict_[feature])

        # check if transformer introduces NaN
        if X[self.variables].isnull().any().any():
            null_counts = X[self.variables].isnull().any()
            vars_ = {key: value for (key, value) in null_counts.items()
                     if value is True}
            raise InvalidModelInputError(
                f'Categorical encoder has introduced NaN when '
                f'transforming categorical variables: {vars_.keys()}')

        return X


class DropUnecessaryFeatures(BaseEstimator, TransformerMixin):

    def __init__(self, variables_to_drop=None):
        self.variables = variables_to_drop

    def fit(self, X, y=None):
        return self

    def transform(self, X):
        # encode labels
        X = X.copy()
        X = X.drop(self.variables, axis=1)

        return X
```

So see here that you need to do very little imports. So you import, of course, `numpy` and `pandas`. And then from Scikit-learn you need to import the `BaseEstimator` and the `TransformerMixin`. So these two other templates that you need to inherit all the methods already pre-coded inside Scikit-learn. And once we do that we only need to modify their `fit` and `transform` methods.

Let me show you how to do that.

### The `CategoricalImputer`

Here for example we have the `CategoricalImputer`. So we create a class that is called `CategoricalImputer` that inherits all the methods from the `BaseEstimator` and the `TransformerMixin`. And if you remember, what the `CategoricalImputer` needs to do is to take categorical variables and if they have missing data they need to replace that missing data by a label called "missing". So this is what we're going to code inside this class.

As in every class we first need to let her know how we're going to initialize the class.

```python
def __init__(self, variables=None) -> None:
    if not isinstance(variables, list):
        self.variables = [variables]
    else:
        self.variables = variables
```

And here we are going to initialize the class when we call it bypassing all the variables that we need to encode so all the categorical variables. So these bits of code here is just to make sure that if instead of a list you pass the string it should be transformed into a list `[variables]` or otherwise it will carry on with the list `variables`

```python
def fit(self, X: pd.DataFrame, y: pd.Series = None
        ) -> 'CategoricalImputer':
    """Fit statement to accomodate the sklearn pipeline."""

    return self
```

And then we had to rewrite the `fit` method. In this case the `fit` method doesn't need to do anything because there is no there is nothing that the class needs to learn from your data.

So we're going to call the `fit` method and we're just going to return `self`. And this is so that this statement can accommodate the Scikit-learn pipeline. Remember that the pipeline requires a `fid` method.

And the only thing that we need to modify is the `transform` method. And what is the transform method going to do?

Well you're going to tell it transform `X`, and `X` is going to be the data, so then the `transform` method is going to take a copy of the data and then, for each variable (`feture`) in the variables (`self.variabes`) that you told these transformer to modify (`varaibles = None`) it will fill the missing by use with the label "missing".

So that in this case, when you do `CategoricalImputer.transform()` it will transform, it will fill the missing data from categorical variables with the label "missing".

```python
def transform(self, X: pd.DataFrame) -> pd.DataFrame:
    """Apply the transforms to the dataframe."""

    X = X.copy()
    for feature in self.variables:
        X[feature] = X[feature].fillna('Missing')

    return X
```

### The `NumericalImputer`

so let me show you now the numerical

computer because it is a little bit more complicated so we create a new class called numerical pewter

and we inherit all the methods from the psychic learn base estimated and transform our mixing.

And now again we need to modify the way we initialize the transformer the way we fitted on the way we

transform it.

























How do we do that.

They need metal is exactly the same.

So we're going to initialize it with the variables that we want to modify.

This is the numerical variables that have missing values.

And now we need a fit method.

Why.

Because if you remember from previous notebooks.

So we want to replace missing values in numerical variables with the mode.

So the first thing our transformer needs to do is to learn the mode from the training data so when we

apply the fit we're going to pass the training data.

And here we indicate that the target equals none.

This is to accommodate the feed method with the pipeline and now we create a dictionary where we're

going to capture for each by level the mode.

So this is going to loop over all the variables that you pass here in this transformer.

And for each one of the variables it will perpetrate in this dictionary.

What is the mode that was scene in the training set for that buyable on irritants.

This computer dictionary.

So when we then next apply the transform and we passed the data that we want to transform that can be

the training set.

He can be tested.

It can be the future data that you want to score.

The first thing this transformer will do is it will stop a copy of the data and then for each and one

of the variables with which you initialized the transformer it will fill the DNA with the value that

was stored in the dictionary for that particular feature and that's it really.

So now this transformer does both things at the same time it's able to store the information it store

the modes of all the variables that you need.

And then with these modes it will replace the missing values in all the variables that you need.

The missing values to be replaced

so let's go ahead and discuss the temporary body of a calculator.

Remember that we captured the elapsed time between one bar level and the year in which the house was

sold so this transformer is going to do that again.

We create the class and we inherit from the cyclone time plates and then we initialize as we initialize

always.

And in this case we're going to add one extra parameter so here we will pass all the variables that

we want to calculate the elapsed time.

And here we pass the reference value.

So this is the variable against which we want to calculate the reference time in our case it was the

year in which the house was sold so we store here the list of variables that we want to calculate elapsed

time form and we store the reference value the reference variable in this field here we don't really

need to fit anything that is nothing that our transformer needs to learn from the training set.

So here we just return served to try and accommodate the cycle and pipeline and in the transform part

of the class again so we're going to pass a data set can be the train set can be the test said the transformer

will create a copy for each of the variables that we want to transform what the transformer is going

to loose to replace the regional variable by the difference in years between the reference variable

and the variable of interest and that's it.

So now we call this transformer we call dot.

It doesn't really do anything.

We call dot transform and it replaces the original value.

That was a year by the elapsed time between that year and the year in which the house was sold.

And as you can see it's very easy and it's quite repetitive.

So it is the same structure over and over.

So now if we want to replace the real labels in categorical variables with exactly the same we inherit

the basis Demeter and the transformer mixing and now we need to initialize with some additional parameters.

We pass the list of variables as we have been doing so far and we pass also the frequency that allows

us to define if a label is frequent or not.

So we store the tolerance in this attribute and then we store the variables in these other attributes

as we have been doing and now we need to learn something.

This transformer does need to learn and it needs to learn the frequent labors because every label that

is not within the frequent labels will be replaced by rare.

So in the fit part of the transformer we're going to create the dictionary which here I cold and colder

and colder dictionary where I will persist the frequent labels for each one of the variables.

So as you can see I loop over all the variables that we used to initialize the encoder and then we calculate

the least of the frequent variables.

This is exactly the same code as we used in the notebook.

So there's nothing new here except that I add this list to the encoder dictionary.

So now I have for each one of the variables here the list of frequent labels will learn this from the

training set when we fit this encoder.

This transformer and then when I transform with pass the data again any data training data test data

it makes a copy and then he goes but it will provide payable and he's going to have a look if the label

of that valuable is within the frequent labors it keeps it.

If he's not within the frequent labels it will replace it by rare.

Let's go now to the categorical encoder is very similar to the real label encoder.

So we create a new object we inherit from the base estimated and transformer mixing.

Again we're initialized with the variables making sure that if we didn't pass the list it transforms

it into a list.

And now the fifth method needs to learn the numbers that is going to use to replace each one of the

labels for each one of the valuables and in this case we do need the target because remember that we

were going to assign digits to the labels but these digits are going to be ordered following the mean

of the house price.

So what they're going to do here is we're going to concatenate them together here I renamed the columns

so that we pass the target as the name of the new data frame.

And now we create the dictionary and this dictionary is going to store their valuable for each variable.

The Dictionary of key value pairs on this label to number parts that are needed to encode the strings

of the variables into the numbers on this string number pairs.

We learn from the dataset we learned during the fifth part of the method.

And then we use them to transform the data.

So when we apply fit and we pass the training set this method is going through a variable per variable

over all the variables that we want to encode and is going to calculate to find the dictionary the list

of key value pairs label number pairs that it needs to encode to transform the strings into numbers.

And this piece of code here don't be put off is exactly the same as the one that we used in the notebook

and now that we have calculated these dictionaries.

When we apply the transform and we passed either the training said all the test set or whatever later

we want what is going to Lewis is going to make a copy and then it's going to look very valuable and

is going to replace the strings by numbers utilizing the dictionary that we built during the fit part

of the method.

Remember that for numerical variables we wanted to transform them using it logarithmic transformation.

So again we create a new class we inherit from the cycle learn templates we initialize it with the variables

with the list of variables that we want to transform we fit.

There is nothing to learn here.

So it will return self to accommodate the cycle line pipeline and then will we transform what we want

to do is variable per variable.

Just apply the log transformation and that's it really.

So now we have all feature engineering steps in I could learn compatible Transformers.
