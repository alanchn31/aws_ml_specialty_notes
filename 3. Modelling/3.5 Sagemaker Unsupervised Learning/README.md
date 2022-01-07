## Random Cut Forest
* Anomaly Detection - detects unexpected spikes in time series data
* Breaks in periodicity and unclassifiable data points
* Input: RecordIO-protobuf or CSV
	* Can use File or Pipe mode
* Create a forest of trees, looks at expected complexity of tree after adding a data point to it
* Data is sampled randomly then trained
* Can work on streaming data (Kinesis Analytics)
* Important hyperparameters:
	* Num_trees - increasing reduces noise
	* Num_samples_per_tree - should be chosen such that 1/num_samples_per_tree approximates the ratio of anomalous data to normal data

## Neural Topic Model
* Organize documents into topics
* Classify/summarize documents based on topics
* Four data channels:
	* Training, validation (optional), test (optional) and auxiliary (optional)
* Words must be tokenized to integers
* Each document must contain a count for every word in the vocabulary in CSV
* Auxiliary channel is for vocabulary
* File or pipe mode
* Hyperparameters: batch_size, learning_rate, num_topics

## Latent Dirichlet Allocation (LDA)
* Topic Modelling
* Train channel, optional test channel
* Input: recordIO-protobuf or CSV
* Each document must contain a count for every word in the vocabulary in CSV
* Pipe mode only supported for recordIO
* Hyperparameters: 
	* num_topics
	* Alpha0 - initial guess for concentration parameters
		* Smaller values generate sparse topic mixtures
		* Larger values produce uniform mixtures

## K-means clustering
* Train channel - ShardedByS3Key, test - FullyReplicated
* recordIO-protobuf or CSV
* File or Pipe on either
* Hyperparameters: K, mini_batch_size, extra_center_factor, init_method
* CPU or GPU available but CPU recommended
* Only one GPU per instance

## Principal Components Analysis (PCA)
* Project high dimensional data to lower dimensional data while minimizing information loss
* recordIO-protobuf or CSV
* File or Pipe on either
* Creates covariance matrix then perform SVD
* Modes
	* Regular - for sparse data and moderate no. of features & observations
	* Randomized - For large number of observations & features, uses approximate algorithm
* Hyperparameters: algorithm_mode, subtract_mean - unbias data
* GPU & CPU (depending on input data)

## IP Insights
* Unsupervised learning of IP address usage patterns
* Identifies suspicious behavior from IP addresses
	* Identify logins from anomalous IPs
	* Identify accounts creating resources from anomalous Ips
* Username, account IDs can be fed directly
* Training channel, optional validation
* CSV only - entities, IP
* Use neural networks to learn latent vector representations of entities and IP addresses
* Entities are hashed and embedded
* Automatically generates negative samples during training by randomly pairing entities with Ips
* Hyperparameters:
	* Num_entities_vector - hash size, set twice the number of unique entity identifiers
	* Vector_dim - size of embedding, too large results in overfitting
    * Epochs, learning_rate, batch_size
* CPU or GPU