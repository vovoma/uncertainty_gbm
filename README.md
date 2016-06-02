# uncertainty_gbm
Sklearn implementation of GBM to predict mu(X) and std(X) on heteroscedastic
data.

The traditional application of GBM is to predict y_hat(X) using an additive
ensemble of decision trees, minimizing squared error loss on known true
observations y(X).

In uncertainty-GBM, we assume the data is heteroscedastic, meaning that the
variance of the observed values y(X) is not constant everywhere, but rather is
described by some other function.  That is, we assume our data is generated
via some functions mu, std: given X, the targets y are generated by taking a
sample from a normal distribution with mean mu(X) and standard deviation
std(X).  Thus, the GBM predicts both mu_hat(X) and std_hat(X) to minimize
negative log-likelihood (NLL).

See dummy_demo.py for a demonstration of the model on constructed data.

See simple_demo.py for a demonstration of the model on slightly more
sophisticated constructed data.  This demo also provides a visual plot to
see how the model's predictions match the true generation of the data.

![alt tag](https://github.com/ofirnachum/uncertainty_gbm/blob/master/simple_demo.png)

See boston_demo.py for a demonstration of the model on Boston real estate data.
On the generated plots, note the relationship between the predicted y and the
true y in the high-risk/high-reward and low-risk/low-reward settings.  The
high-risk/high-reward setting successfully pushes the most of the below-average
true examples to the bottom.  However, some very low true examples receive
disproportionally high scores.  On the other hand, the low-risk/low-reward
setting successfully pushes the above-average true examples to the top.
However, at the top, there is little observed relationship between especially
high true examples and simply above-average true examples.

![alt tag](https://github.com/ofirnachum/uncertainty_gbm/blob/master/boston_demo.png)
