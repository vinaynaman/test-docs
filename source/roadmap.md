# Roadmap

The list below contains the functionality that we are planning to develop for KFS

- Items below that are in development \(or planned for development\) will be indicated in parentheses.
- We welcome contribution to all items in the roadmap!

## Data Sources
  - DataFrame Source
  * [x] Pandas
  * [x] Spark
  * [x] File Source
  * [x] Parquet file source
  * [x] CSV file source
  * [x] PostgreSQL Source
  * [ ] Redshift source
  * [ ] BigQuery source
  * [ ] Kafka source \(Planned for Q4 2021\)
  * [ ] HTTP source
  * [ ] Snowflake source
  * [ ] Synapse source
## Offline Stores
  * [x] PostgreSQL
  * [ ] Parquet File 
  * [ ] In-memory / Delta
  * [ ] In-memory / Hudi
  * [ ] Redshift
  * [ ] BigQuery
  * [ ] Custom offline store support
  * [ ] Hive
  * [ ] Snowflake
  * [ ] Synapse
## Online Stores**
  * [x] SQLite
  * [x] Redis
  * [x] PostgreSQL
  * [ ] DynamoDB
  * [ ] Datastore
  * [ ] Custom online store support
  * [ ] Bigtable
  * [ ] Cassandra
## Feature Registry**
  * [x] PostgreSQL
  * [x] SQLite
  * [ ] MongoDB
## Streaming**
  * [ ] Custom streaming ingestion job support
  * [ ] Streaming ingestion on AWS \(Planned for Q4 2021\)
  * [ ] Streaming ingestion on GCP
## Feature Engineering**
  * [ ] On-demand Transformations \(Development in progress. See [RFC](https://docs.google.com/document/d/1lgfIw0Drc65LpaxbUu49RCeJgMew547meSJttnUqz7c/edit#)\)
  * [ ] Batch transformation \(SQL\)
  * [ ] Streaming transformation
## Deployments**
  * [ ] AWS Lambda \(Development in progress. See [RFC](https://docs.google.com/document/d/1eZWKWzfBif66LDN32IajpaG-j82LSHCCOzY6R7Ax7MI/edit)\)
  * [ ] Cloud Run
  * [ ] Kubernetes
  * [ ] KNative
## Feature Serving**
  * [ ] Python Client
  * [ ] REST Feature Server \(Python\) \(Development in progress. See [RFC](https://docs.google.com/document/d/1iXvFhAsJ5jgAhPOpTdB3j-Wj1S9x3Ev_Wr6ZpnLzER4/edit)\)
  * [ ] gRPC Feature Server \(Java\) \(See [\#1497](https://github.com/feast-dev/feast/issues/1497)\)
  * [ ] Java Client
  * [ ] Go Client
  * [ ] Push API
  * [ ] Delete API
  * [ ] Feature Logging \(for training\)
## Data Quality Management**
  * [ ] Data profiling and validation \(Great Expectations\) \(Planned for Q4 2021\)
  * [ ] Metric production
  * [ ] Training-serving skew detection
  * [ ] Drift detection
  * [ ] Alerting
## Feature Discovery and Governance**
  * [x] Python SDK for browsing feature registry
  * [x] REST API for browsing feature registry
  * [ ] KFS Web UI \(Development in progress\)
  * [ ] CLI for browsing feature registry
  * [ ] Model-centric feature tracking \(feature services\)
  * [ ] Feature versioning
  * [ ] Amundsen integration
## KFS Distribution**
  * [ ] Dask
## Code Standards**
  * [ ] PEP 517
=======
## Streaming**
  * [ ] Custom streaming ingestion job support
  * [ ] Streaming ingestion on AWS \(Planned for Q4 2021\)
  * [ ] Streaming ingestion on GCP 
* **Feature Engineering**
  * [ ] On-demand Transformations \(Development in progress. See [RFC](https://docs.google.com/document/d/1lgfIw0Drc65LpaxbUu49RCeJgMew547meSJttnUqz7c/edit#)\)
  * [ ] Batch transformation \(SQL\)
  * [ ] Streaming transformation 
* **Deployments**
  * [ ] AWS Lambda \(Development in progress. See [RFC](https://docs.google.com/document/d/1eZWKWzfBif66LDN32IajpaG-j82LSHCCOzY6R7Ax7MI/edit)\)
  * [ ] Cloud Run
  * [ ] Kubernetes
  * [ ] KNative 
* **Feature Serving**
  * [ ] Python Client
  * [ ] REST Feature Server \(Python\) \(Development in progress. See [RFC](https://docs.google.com/document/d/1iXvFhAsJ5jgAhPOpTdB3j-Wj1S9x3Ev_Wr6ZpnLzER4/edit)\)   
  * [ ] gRPC Feature Server \(Java\) \(See [\#1497](https://github.com/feast-dev/feast/issues/1497)\)
  * [ ] Java Client
  * [ ] Go Client    
  * [ ] Push API
  * [ ] Delete API
  * [ ] Feature Logging \(for training\) 
* **Data Quality Management**
  * [ ] Data profiling and validation \(Great Expectations\) \(Planned for Q4 2021\)
  * [ ] Metric production
  * [ ] Training-serving skew detection
  * [ ] Drift detection
  * [ ] Alerting 
* **Feature Discovery and Governance**
  * [x] Python SDK for browsing feature registry
  * [x] REST API for browsing feature registry
  * [ ] KFS Web UI \(Development in progress\)
  * [ ] CLI for browsing feature registry
  * [ ] Model-centric feature tracking \(feature services\)
  * [ ] Feature versioning
  * [ ] Amundsen integration
* **KFS Distribution**
  * [ ] Dask
* **Code Standards**
  * [ ] PEP 517
