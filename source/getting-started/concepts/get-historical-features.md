# Historical Feature Retrieval

Historical features are nothing but the features that we used to create the feature view. These features can be in any number. You can create a training dataset using these features. For that you need to provide a entity dataframe which contains the entity key and the timestamp column so that it will give point-in-time records accurately. These features will come your offline store.

- Sample Entity Dataframe
  ![Entity Dataframe](https://github.com/katonic-dev/katonic-feature-store/blob/dev-2.0/docs/sources/entity_df.jpg)

```python
# Retrieve training data from Historical Features .
    training_df = fs.get_historical_features(
    entity_df=df,
    feature_view=["subscription_stats_fv"],
    features=["year", "no_of_days_subscribed", "minimum_daily_mins", "maximum_daily_mins", "videos_watched", "maximum_days_inactive"],
    ).to_df()
```

![Features retrieved from featrue view](https://github.com/katonic-dev/katonic-feature-store/blob/dev-2.0/docs/sources/training_df.jpg)
