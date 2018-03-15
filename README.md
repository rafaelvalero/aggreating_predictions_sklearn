
# Answer
The best way to do it (as far as I know is using methods http://scikit-learn.org/stable/modules/ensemble.html#forest.


# Question 
in Stackoverflow [here][4].

When training the model the results depend on the sampling. In order to obtain something better you could repeat the training (in another randomly create training sample, using [Ffolds][1], [StratifiedKFold][2] ... ), somehow aggregate the results and have this way a result that will be more robust that one create in a particular case alone. **Question: is it already implemented in sklearn or similar?**. Apologies is this is a straighforward question, I haven't see a simple solution.

I see that there is a function called [cross_val_predict][3] however my first impresion having a quick look to the source code is that it predecits as many times as trains and I would like to predicts only ones, so I can piclke the, somehow aggregate results, and predict later, instead of repeat the whole training thing again.


  [1]: http://scikit-learn.org/stable/modules/generated/sklearn.model_selection.KFold.html#sklearn.model_selection.KFold
  [2]: http://scikit-learn.org/stable/modules/generated/sklearn.model_selection.StratifiedKFold.html#sklearn.model_selection.StratifiedKFold
  [3]: http://scikit-learn.org/stable/modules/generated/sklearn.model_selection.cross_val_predict.html
  [4]: https://stackoverflow.com/q/49262367/7127519

# Objectives

* Create a training function that train the model many time and store the results.
* Create a function that collect previous trained model and provide predictions.
* I want to do it in parallel using joblib [this library is used to parallelize in Sklearn]

# Why


1. For deployment we may prefer and estimator aggregate as the second one, which provide a most consistent prediction accurracy than the first one.
2. When you parallelize the process could be interesting to be able to aggregate the results later.

You can see below a real and example.

References

1. http://scikit-learn.org/stable/modules/cross_validation.html#cross-validation
2. https://stackoverflow.com/questions/41458834/how-is-scikit-learn-cross-val-predict-accuracy-score-calculated
3. For mmap https://pythonhosted.org/joblib/parallel.html#automated-array-to-memmap-conversion



15 March 2018 Rafael Valero Fernandez