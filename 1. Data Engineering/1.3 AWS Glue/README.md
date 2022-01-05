## 1. Data Catalog & Crawlers  
**Data Catalog**  
* Metadata repository for all tables  
* Integrates with Athena/Redshift Spectrum for schema discovery  
   
**Crawlers**  
* Go through data in S3 to infer schema and partition  
* Works for CSV, JSON, Parquet, relation store  
* Works for S3, Amazon Redshift and RDS  
* Can run on schedule or on demand  
* Need IAM roles/credentials to access data stores
  
## 2. Transformations
**Bundled Transformations**
* DropFields, DropNullFields  
* Filter  
* Join  
* Map - add/delete fields, external lookups  
  
**ML Transformations**  
FindMatches ML - identify duplicate/matching records in data even when records do not have common identifier and no fields match exactly        