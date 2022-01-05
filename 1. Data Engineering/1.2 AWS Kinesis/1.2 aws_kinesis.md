## 1. Kinesis Data Streams
	a. Properties
		* Streams are divided into ordered shards / partitions
		* Shards have to be provisioned in advanced
		* Data Retention from 24 hours to 365 days
		* Multiple application can consume the same stream
		* Once data is inserted in Kinesis, cannot be deleted
		* Records can be up to 1MB in size

	b. Limits
		i. Producer:
			1) 1MB/s or 1000 messages/s at write per shard
			2) "ProvisionThroughputException" otherwise
		ii. Consumer Classic:
			1) 2MB/s at read per shard across consumers
			2) 5 API calls per second per shard across consumers

## 2. Kinesis Data Firehose
	a. Properties
		i. AWS destinations:
			* Amazon S3
			* Amazon Redshift (COPY through S3), (data warehouse)
			* Amazon Elasticsearch (data index service)
			* Splunk (external 3rd party service)
		ii. Fully managed service
		iii. Near real time (60 s latency min for non-full batches)
		iv. Auto scaling
		v. Data conversion from CSV/JSON to PARQUET/ORC (for s3)
		vi. Data transformation through AWS lambda
		vii. Supports compression when target is s3 (gzip, zip, snappy)
		viii. Pay for amount of data going through

## 3. Kinesis Data Analytics
	a. Use cases
		* Streaming ETL: simple transformations on stream data
		* Continuous metric generation: live leaderboard
		* Responsive analytics: Look for criteria and provide alerts
	b. Features
		* Pay for resources consumed
		* Serverless (auto scaling)
		* Use IAM permissions to access stream source and destination
		* SQL/Flink to write computation
		* Schema discovery
		* Lambda can be used for preprocessing
	c. ML algorithms
		i. Random Cut Forests: SQL function used for anomaly detection
		ii. Hotspots: Locate and return information on relatively dense regions in the data

## Kinesis Video Stream