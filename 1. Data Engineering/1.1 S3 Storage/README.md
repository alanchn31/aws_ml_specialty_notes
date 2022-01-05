## 1. Properties
1. Store objects in buckets with unique global names
2. Objects have keys (full file paths)
3. Support any file format
4. Data partitioning: pattern for speeding up range queries

## 2. Storage Tiers
1. Standard
2. Standard Infrequent Access (IA)
3. One-zone Infrequent Access
4. Intelligent Tiering
5. Glacier

From most frequent access (Standard) → least frequent access (Glacier)
S3 Lifecycle Rules dictates movement between different tiers

## 3. S3 object Encryption
1. Most commonly used: SSE-S3 & SSE-KMS
2. SSE-S3: Use S3 managed key for encryption
3. SSE-KMS: Use KMS customer master key for encryption

## 4. S3 Security
1. User-based:
	1. IAM - which API calls allowed for specific user
	2. Bucket Policies:
	3. Bucket wide rules from the S3 console, allows cross account

2. JSON based policies
	* Resources: Buckets & objects
	* Actions: Set of APIs that allows or denies
	* Effect: Allow/Deny
	* Account/user to apply policies to

3. Security:
	1. Networking - VPC Endpoint Gateway (allow traffic to stay within VPC instead of public web)
	2. Logging & Audit - S3 logs can be stored in other buckets, API calls can be logged in AWS CloudTrail
    3. Tagged Based - can assign IAM & bucket policies based on tags