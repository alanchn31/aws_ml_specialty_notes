## Data Processing using AWS EMR
* Collection of EC2 instances (also known as nodes)
	* Master node (single EC2) - manages the cluster
	* Core node - hosts HDFS data and runs tasks
	* Tasks node - run tasks, do not host data
		* No risk of data loss when removed
* Integration with other tools
	* VPC to configure virtual network when nodes are launched
	* S3 to store data (need not store In HDFS)
	* Cloudwatch to monitor cluster performance and configure alarms
	* IAM to configure permissions
	* Cloudtrail to audit requests made to the service
	* Data pipelines to schedule and start clusters
* EMR Storage
	* HDFS (ephemeral, once cluster is shut down, data is gone)
	* EMRFS (access S3 like it was HDFS)
	* Local File System
	* EBS for HDFS
* EMR Notebooks
	* Similar to Zeppelin but more integration with AWS tools
	* Notebooks backed up to S3
	* Can provision clusters from the notebook
	* Hosted inside a VPC
	* Accessed through AWS console
* EMR Security
	* IAM policies (allow users to access clusters through EMR via user groups and locations of EMRFS data)
	* Kerberos (secret key encryption, for passwords and credentials)
	* SSH (connect to cluster securely)
	* IAM roles (control how EMR access other AWS services)
* Choosing Instance Types
	* Master node: m4.large if < 50 nodes, m4.xlarge if >= 50 nodes
	* Core & task nodes: m4.large is usually good
		* If cluster waits on a lot of external dependencies, t2.medium
		* Improved performance: m4.xlarge
	* Spot instances
		* Good choice for task nodes
	    * Only use on core or master if testing or cost-sensitive, risk of partial data loss
