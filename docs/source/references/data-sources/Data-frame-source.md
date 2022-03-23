# File Source

Description :

A data frame source will be used to write the historical features to an offline store this will get used to build training datasets. Also materializing the features into an online store(Redis-server). Using data frames is very straightforward and convenient.

| Make sure about the data types in your Data frame to avoiding any confict while doing the Join Operations. |
| :--------------------------------------------------------------------------------------------------------- |

You can use pandas data frame or spark data frame.

# Example :

```python
from kfs import DataFrameSource

batch_source = DataFrameSource(
        df=pandas_df, # Provide your dataframe
        event_timestamp_column="event_timestamp", # Event Timestamp
    )
```
