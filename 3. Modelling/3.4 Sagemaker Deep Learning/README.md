## Seq2seq
* Takes in RecordIO-wrapped protobuf
	* Tokens must be integers
* Start with tokenized text files
* Pack into integer tensors with vocabulary files
* Must provide training, validation and vocabulary files
* Hyperparameters
	* Batch_size
	* Optimizer_type - RMSProp, Adam, SGD
	* Learning_rate, Num_layers_encoder, Num_layers_decoder
* Can optimize on accuracy, BLEU score (for machine translation), perplexity (for machine translation)
* Can only use GPU instance types
* Can only use single machine for training (but can use multiple GPUs in one machine.

## DeepAR
* JSON lines format - gzip or parquet
* Each record must contain
	* Start: starting timestamp
	* Target: time series values
* Each record can contain
	* Dynamic_feat: dynamic features
	* Cat: categorical features
* Include entire time series for training, validation and test
* Evaluate on hold out series
* Hyperparameters
	* Context_length - no. of time points given to the model before prediction
	* Epochs, Mini_batch_size, Learning_Rate, Num_cells
* Can use CPU/GPU
* Single or multi-machine
		

## Blazingtext
* Usage:
	* Text classification - only for sentences
	* Word2vec
* Training Input
	* Text classification (supervised mode):
		* One sentence per line
		* First word in the sentence is "_label_" followed by the label
	* Word2vec
		* One sentence per line
* Hyperparameters
	* Word2vec:
		* Mode (batch skipgram, skipgram, cbow)
		* Learning_rate, Window_size, Vector_dim, Negative_samples
	* Text classification
		* Epochs, Learning_rate, Word_ngrams, Vector_dim

## Object2vec
* Data must be tokenized into integers
* Training data consists of pairs of tokens and/or sequences of tokens
* Hyperparameters
	* Dropout, early stopping, epochs, learning_rate, batch_size, layers, activation_function,
	* Optimizer, weight_decay
	* Enc1_network, enc2_network - hcnn, bilstm, pooled_embedding
* Can only train on a single machine - CPU, GPU or multiGPU
	* Training
		* MI.m5.2xlarge or MI.p2.2xlarge or scale to MI.m5.4xlarge/MI.m5.12xlarge
	* Inference
		*  MI.p2.2xlarge
		* Use INFERENCE_PREFERRED_MODE environment variable to optimize for encoder embeddings rather than classification or regression

## Object Detection
* RecordIO or image format (jpg or png)
* For image format, supply a JSON file with annotation data for each image
* Uses CNN with Single Shot multibox Detector (SSD) algorithm
* Hyperparameters:
	* Mini_batch_size, learning_rate
	* Optimizer - sgd, adam, rmsprop, adadelta
* Use GPU instances for training
	* Supports multi-GPU single machine or multi-machine
* CPU for inference
		
## Image Classification
* Input Format:
	* Apache MXNet RecordIO
	* JPG or PNG images (requires .lst files to associate image index, class label and path to image)
	* Augmented Manifest Image Format (enables pipe mode, streaming from s3)
	* Using ResNet CNN
	* Default: 3 channels, 224x224
* Hyperparameters:
	* Batch_size, learning_rate, optimizer, weight_decay, beta_1, beta_2, eps, gamma
* GPU instances for training (multi-GPU single machine or multi-machine)
* CPU or GPU instances for inference

## Semantic Segmentation
* Algorithms:
	* Fully Convolutional Network (FCN)
	* Pyramid Scene Parsing (PSP)
	* DeepLab V3
* Hyperparameters:
	* Epochs, learning_rate, batch_size, optimizer, algorithm, backbone
* Only GPU is supported (single machine, P2 or P3)
* Inference on CPU (C5 or M5) or GPU (P2 or P3)