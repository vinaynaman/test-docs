# Get Online Features

Note : You will get online features only when you publish feature table to an online store using `publish_table` function.

We will use Online features to get the latest features at low latency and also for the serving purpose. We need to provide the entity key values in order to retrieve the features from Online Store. To get online features we need to use the function `get_online_features()` on feature store object. We are using `Redis` server as an Online store for Kfs.

```python
customer_ids = [100198, 100756, 101653]
    df = fs.get_online_features(
    entity_rows=[{"customer_id": customer_id} for customer_id in customer_ids],
    feature_view=["subscription_stats_fv"],
    features=["year","no_of_days_subscribed","minimum_daily_mins","maximum_daily_mins","videos_watched","maximum_days_inactive"],
    ).to_df()
```

It will return a Dataframe with all the latest features.
![Retrieved Online Features](https://github.com/katonic-dev/katonic-feature-store/blob/dev-2.0/docs/sources/online_features.jpg)
