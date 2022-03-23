# Entity

We define an Entity key for a Feature view, this will be used to map the data records with the unique id, so that when we want to get the features for that particular key, Feature store will able to recognize that particular data records among all. Entity keys will act as Primary keys. They are used during the lookup operation to retrieve the features from the online store, and they are also used to match feature rows across feature views during point-in-time joins.

- to create an entity key -

```python
# Entity
driver = Entity(name="driver_id", value_type=ValueType.INT64)
```

we need to provide the feature name along with it's datatype in order to define a entity key.

Example of Entity key:

![entity_key_ref](https://github.com/katonic-dev/katonic-feature-store/blob/dev-2.0/docs/sources/entity_key.jpg)
