# Section 4: Building a Reproducible Machine Learning Pipeline
## 35. Scikit-Learn Pipeline - Code

Below the code for the Scikit-Learn pipeline, utilising the transformers we created in the previous lecture. Briefly, we list inside the pipeline, the different transformers, in the order they should run. The final step is the linear model. Right in front of the linear model, we should run the Scaler.

You will better understand the structure of the code in the coming lectures. Briefly, we write the transformers in a script within a folder called processing. We also write a config file, where we specify the categorical and numerical variables. Bear with us and we will show you all the scripts. For now, make sure you understand well how to write a scikit-learn pipeline.

```python
from sklearn.linear_model import Lasso
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import MinMaxScaler

from regression_model.config import config
from regression_model.processing import preprocessors as pp

price_pipe = Pipeline([
                ('categorical_imputer', pp.CategoricalImputer(variables = config.CATEGORICAL_VARS_WITH_NA)),
                ('numerical_inputer', pp.NumericalImputer(variables = config.NUMERICAL_VARS_WITH_NA)),
                ('temporal_variable', pp.TemporalVariableEstimator(variables=config.TEMPORAL_VARS, reference_variable=config.REFERENCE_TEMP_VAR)),
                ('rare_label_encoder', pp.RareLabelCategoricalEncoder(tol = 0.01, variables = config.CATEGORICAL_VARS)),
                ('categorical_encoder', pp.CategoricalEncoder(variables=config.CATEGORICAL_VARS)),
                ('log_transformer', pp.LogTransformer(variables = config.NUMERICALS_LOG_VARS)),
                ('drop_features', pp.DropUnecessaryFeatures(variables_to_drop = config.DROP_FEATURES)),
                ('scaler', MinMaxScaler()),
                ('Linear_model', Lasso(alpha=0.005, random_state=0))
            ])
```
