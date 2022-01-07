## Linear Learner
* Takes in RecordIO-wrapped protobuf or CSV
* File or Pipe mode supported (Use pipe to optimize training time)
* Training data must be normalized (Linear Learner can also do this for us automatically)
* Input data must be shuffled
* Multiple models optimized in parallel
* L1, L2 regularization tuned
* Important hyperparams:
	* Balance_multiclass_weights - gives each class equal importance in loss function
	* Learning_rate
	* Mini_batch_size
	* L1
	* Wd - weight decay / L2 regularization

## XGBoost
* Takes in RecordIO-wrapped protobuf, CSV, libsvm, parquet
* Important hyperparameters
	* Subsample - subsample ratio of training instances for each tree, prevents overfitting
	* Eta - step size shrinkage, prevents overfitting
    * Gamma - Min loss reduction to create a partition
	* Alpha - L1 regularization term
	* Lambda - L2 regularization term
	* Eval_metric - evaluation metric
	* Scale_pos_weight - adjust balance of postive and negative weights (for imbalanced data)
	* Max_depth - max depth of tree, deeper the tree, higher the chance of overfitting

## K Nearest Neighbours
* Classification - find K nearest points to a sample point and return most frequent label
* Regression -  find K nearest points to a sample point and return average value
* Input:  train and test channel
* recordIO-protobuf or CSV training
	* First column is label
* File or pipe mode on either
* How is it used?
	* Data is first sampled
	* Dimensions are reduced
	* Build an index for looking up neighbors
	* Serialize the model
	* Query the model for given value of K
*  Hyperparameters: K, sample_size
* Train on either CPU or GPU
* Inference: CPU for lower latency, GPU for higher throughput

## Factorization Machines 
*  Deal with sparse data
	* Click predictions
	* Item recommendations
* Limited to pairwise interactions (for eg, user -> items)
* recordIO-protobuf with float32
* Used in recommender systems
* Hyperparameters: Initialization methods for bias, factors and linear terms
* CPU or GPU (CPU recommended, GPU only works with dense data)