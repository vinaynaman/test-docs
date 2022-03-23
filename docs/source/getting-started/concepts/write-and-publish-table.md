# write table

This `write_table()` function will take entity key and defined feature view as parameters and store the data to a offline storage (Private Bucket). All the metadata like user name, project name, description, feature names and their data types will get stored inside the registy(PostgreSQL).

```python
feature_store.write_table([entity, subscription_stats])
```

# Publish table with

You can also use `publish_table()` function to materialize the latest features from the Offline view to an Online store. For that you need to specify a `start_timestamp` and `end_timestamp` so that the features that are in between this time period will get materialized. But you need to give them in datetime format.

```python
from datetime import datetime

fs.publish_table(
    start_ts = datetime(2021,10,1),
    end_ts = datetime(2021,11,1)
    )
```
