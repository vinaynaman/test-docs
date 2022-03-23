Kfs will use Online store to retrieve all the infered feature values at low-latency. This will be helpful when you try to do the inferenceing with the entity keys. The features that are defined in the offline store will get materialized to the online store via a function called `publish_table()` upon the feature store object.

The data types for the feature views in the online store will be same as the data source provided by the user to publish the tables with latest features.

# Advantage of Online Store.

- Not like offline store or data source , Online store will only keeps the latest data record per an entity key. No historical values will be stored for all the entity keys. This process be done at low-latency.

We are using `Redis` server as an online store for Kfs, It is as an in-memory data store to ingest, process, and analyze real-time data with sub-millisecond latency. Redis is an ideal choice for real-time analytics use cases.

Example data source:
![Katonic Feature Store Flow Diagram](https://github.com/katonic-dev/katonic-feature-store/blob/dev-2.0/docs/sources/entity_df_redis_refer.png)

If you pick the have the entity keys , they will get used by Online store to retrieve the latest feature values per key.
