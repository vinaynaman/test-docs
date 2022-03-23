# Feature View:

- Feature
  A is an individual measurable property. It is typically a property observed on a specific entity, but does not have to be associated with an entity. Features are defined as part of feature views.Since KFS does not transform data, a feature is essentially a shcema that only contains a name and a data type.

- Feature View
  A feature view is a group of one or more features.Every feature view will have an entity key and data source.

These feature views be will used in generation of training datasets by using the offline stores. This will find the historical features by using a entity dataframe and features list.

| The `ttl` parameter is nothing but how much time your Feature View need to stay in side your Feature Store.You can pass the duration as a string like '2d' or you can provide it in years '2y', months '1m' or hours '6h'. |
| :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| The `name` arguement will take a string, to store your feature view with that name. This will be helpful when you want to retrieve historical or online features you need to call the features by giving this feature view name. |
| :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

```python
# Feature View
    subscription_stats  = FeatureView(
    name="subscription_stats_fv",
    entities=["customer_id"],
    ttl="2h", # no of days/months/years/hours
    features=["year","no_of_days_subscribed","minimum_daily_mins","maximum_daily_mins","videos_watched","maximum_days_inactive"],
    batch_source=batch_source,
    )
```

Above code will create a Feature view with the name of subscription_stats_fv with customer_id as entity key,features as features.

| You can see all the details of an Feature view as a Dictionary by `.to_dict()` on the Feature View object. It will return a dictionary with all the details. |
| :----------------------------------------------------------------------------------------------------------------------------------------------------------- |

```python
subscription_stats_fv.to_dict()
```

# Output

```bash
{'name': 'subscription_stats_fv',
    'entities': ['customer_id'],
    'feature': ['year',
    'no_of_days_subscribed',
    'minimum_daily_mins',
    'maximum_daily_mins',
    'videos_watched',
    'maximum_days_inactive'],
    'ttl': "2h",
    'online': True,
    'batch_source': {'type': 'BATCH_FILE',
    'custom_options': {'configuration': {'query': 'SELECT * FROM subscription_data'}},
    'event_timestamp_column': 'time_stamp',
    'created_timestamp_column': '',
    'data_source_class_type': 'kfs.core.offline_stores.postgres_source.PostgreSQLSource'}}
```
