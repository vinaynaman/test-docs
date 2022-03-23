# Offline stores

Kfs uses offline stores to store all the feature views. They will store all the historical feature values. Kfs does not generate any of these features instead of that these will get created when the user writes the features to a feature view. These offline store will be used as a interface for querying existing features through out an organization or among teams.

Offline store advanteages and usage:

- Offline stores are mainly used to generate a training dataset from the previous historical features.
- Also these will be helpful when you publish the data from an offline store to online store for serving purpose at low laterncy.

Offline stores will get configured whenever a user initialize a feature store. To bulid training datasets or materializing features into online store, Kfs will use these configured offline stores along with the data sources you have defined as a part of feature definitions to execute the necessary operations.

You can create multiple Offline stores for a single project with various features.

When you run the function `write_table` on top of Feature Store object it will create a offline store.

```python
fs.write_table([entity, feature_view_name])
```

- entity : Previously defined entity key
- feature_view_name : The name of your defined feature view.
