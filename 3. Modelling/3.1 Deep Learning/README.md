## Deep Learning on EMR & EC2
* EMR supports Apache MXNet and GPU instances
* Instance Types:
    * P3: 8 Tesla V100 GPUs
	* P2: 16 K80 GPUs
	* G3: 4 M60 GPUs 

## Tuning Hyperparameters
* Small batch sizes tend to not get stuck in local minima
* Large batch sizes can converge on the wrong solution at random
* Large learning rates can overshoot correct solution
* Small learning rate takes up more training time

## Issues with gradients
* Gradients can become smaller and smaller (or bigger and bigger) when backpropagated through deeper layers
* Solutions: 
    * Break network into subnetworks and train individually
	* Use architectures like LSTMs, ResNets
	* Better choice of activation function like ReLU

## Regularization Techniques for NNs
* Dropout
* Early Stopping
* Reduce no. of neurons/layers
* Batch Norm