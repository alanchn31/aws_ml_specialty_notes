## Amazon Comprehend
* Entity Recognition
* Sentiment Analysis
* Syntax Recognition

## Amazon Translate
* Input format supported: CSV or TMX format
* Language Translation

## Amazon Transcribe
* Input format supported: MP3, MP4, FLAC or WAV
* Use case
	* Speaker Identification
	* Channel Identification - two callers transcribed separated
* Custom Vocabularies - Vocabulary Lists: names, acronyms, brand names
* Vocabulary Tables

## Amazon Polly
* Text to Speech
* Lexicons - customize pronunciation of specific words and phrases
* SSML - Speech Synthesis Markup Language. Give control to over emphasis, pronunciation, breathing, whispering, speech rate, pitch, pauses
* Speech Marks - Can encode when sentence / word starts and ends in audio stream
* Useful for lip-syncing animation

## Amazon Rekognition
* Computer Vision
* Object and Scene Detection
* Image moderation
* Facial analysis
* Celebrity recognition
* Text in Image
* Video Analysis
* Images from S3
* Facial recognition depends on visibility, lighting, angle, eyes, resolution
* Videos come from Kinesis Video Streams
* Can use Lambda to trigger image analysis upon upload

## Amazon Forecast
* Time Series Forecasting
* AutoML choose best model between ARIMA, DeepAR, ETS, NPTS, Prophet

## Amazon Lex
* NLP chatbot engine


## Amazon Personalize
* Fully managed recommender engine
* Feed in data via S3 or API integration
* Needs an explicit schema in Avro format, javascript or SDK
* 2 main APIs:
	* GetRecommendations - recommended products, content
	* GetPersonalizedRanking - Ranks a list of items
* Datasets - Users, Items, Interactions
* Recipes - what kind of model to build
	* USER_PERSONALIZATION
	* PERSONALIZED_RANKING
	* RELATED_ITEMS
* Solutions 
	* Trains the model
	* Optimize for relevance and additional objectives
		* Video Length, Price 
	* Hyperparameter Optimization
* Campaigns
	* Deploys solution "version"
	* Deploys capacity for real-time recommendations
* Amazon Personalize Hyperparameters
	* User-Personalizing, Personalized-Ranking
		* Hidden_dimension (HPO)
		* Bptt (backpropagation through time - RNN)
		* Recency_mask (weighs recent events more)
		* Min/max_history_length_percentile
		* Exploration_weight (0-1), controls relevance
		* Exploration_item_age_cutoff - how far back in time you go
	* Similar-items
		* Item_id_hidden_dimension (HPO)
		* Item_metadata_hidden_dimension (HPO with min & max range specified)
* Amazon Personalize Security
	* Data not shared across accounts
	* Data may be encrypted with KMS or at rest in your region (SSE-S3)
* Pricing
	* Data Ingestion - per GB
	* Training: per-training hour
	* Inference - per TPS hour
	* Batch recommendations - per user or per item
	
## Amazon Textract
* OCR - tables, forms, fields


## Amazon Lookout
* Equipment, metrics, vision
* Detect abnormalities from sensor data automatically to detect equipment issues
* Monitor metrics from S3, RDS, Redshift, 3rd party SAAS app
* Vision uses computer vision to detect silicon wafers, circuit boards etc

## Amazon Monitron
* End to end system for monitoring industrial equipment and predictive maintenance
	
## Torchserve
* Model serving framework for Pytorch

## AWS Neuron
* SDK for ML inference, specifically for AWS inferentia chips
* EC2 Inf1 instance type
* Integrated with Sagemaker or deep learning AMI's, containers, Tensorflow, Pytorch, MXNet

## AWS Panorama
* Computer Vision at the edge, brings computer vision to existing IP cameras

## AWS Kendra
Enterprise search with natural language