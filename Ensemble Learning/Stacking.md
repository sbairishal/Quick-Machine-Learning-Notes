# Stacking:
- short for stacked generalization.
- simple idea: instead of using trivial functions (such as hard voting) to aggregate the prediction for all the predictors in an ensemble, why don't train a model to perform this aggregation.
- Bottom line predictors (m in numbers) predcits different values(classes) and then the final predcitor (called meta learner or blender) takes these predictions as inputs and make final prediction.

### How to train Blender and First/ Bottom layer?
- Use hold-out set approach. 
- divide the training set into two subsets.
- Use first subset to train the predcitors in first layer.
- Next, the first layer predictors are used to make predictions on the second (held-out) set.
- This ensures that the predictions are clean, since the predictors never saw these instances during training.
- Now for each instances in held-out set, predcitors from first layer will have some predictions. 
- We will create a new training set using these predictied values from predcitors from first layer using held-out set.
- and, then blender is trained on this new training set, so it learns to predict the target value gievn the first layers predictions.

- We can have multiple layers.
- We can train several different blenders (one using linear regression, another using random forest regression, and so on.)
- 