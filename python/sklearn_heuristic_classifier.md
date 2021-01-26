# Example heuristic classifier in sklearn 

Use as baseline classifier in cases where e.g. if value < threshold it's class 1 other wise class2.

```python
from sklearn.base import BaseEstimator, ClassifierMixin
import pandas as pd
import numpy as np


class HeuristicClassifier(BaseEstimator, ClassifierMixin):
    """Class to emulate a predictive model using simple heuristic of whether the feature from perspective is > threshold"""

    def __init__(self, feature_index=0, classification_threshold=0.94):
        """Set the classes for binary classification"""
        self.n_classes_ = 2
        self.classes_ = np.array([0, 1])
        self.feature_index = feature_index
        self.classification_threshold = classification_threshold

    def fit(
        self, X, y
    ):
        """
        Mocks out the fit function for a standard scikit-learn estimator. Since
        the heuristic doesn't rely on any previous data, the function simply
        returns self.
        :return:
            Returns the estimator without any changes.
        """
        return self

    def predict(self, features: np.ndarray) -> np.ndarray:
        """
        Emulate a machine learning model's behavior. This function will return
        the most probable class for each instance. It only uses the first
        feature of the `features` array.
        If the feature value is less than or equal to classification_threshold, it will return a
        class 0. If feature value is greater than classification_threshold, it will return a
        class 1.
        :param features:
            Ndarray that corresponds to features used in a classification model.
        :return:
            Predicted class for all instances of `features`.
        """
        return np.where(features[:, self.feature_index] < self.classification_threshold, 1, 0)
    
    
    def predict_proba(self, features: np.ndarray) -> np.ndarray:
        """
        Emulate a machine learning model's behavior. This function will return
        the most probable class for each instance. It only uses the first
        feature of the `features` array.
        If the feature value is less than or equal to classification_threshold, it will return a
        probability of 0. If feature value is greater than classification_threshold, it will return a
        probability of 1.
        :param features:
            Ndarray that corresponds to features used in a classification model.
        :return:
            Predicted class for all instances of `features`.
        """
        positive_probas = np.where(features[:, self.feature_index] > self.classification_threshold, 1., 0.)
        negative_probas = np.where(features[:, self.feature_index] > self.classification_threshold, 0., 1.)
        
        output = np.vstack([negative_probas, positive_probas]).T
        
        return output
    
    
def build_heuristic_classifier(df, feature_column, threshold):
    feautre_index = df.columns.get_loc(feature_column)
    model = HeuristicClassifier(feautre_index, threshold)
    model.fit(1, 1)
    return model
```