<p align="center">
  <img 
    width="350"
    height="80"
    src="https://github.com/katonic-dev/katonic-feature-store/blob/opensource/docs/sources/logo.png">
</p>
# KFS - Katonic Feature Store :bar_chart:

KFS is a library which we can use in various phases of Machine Learning Project. We can use KFS to store the needed features from the Online and Offline sources and store them in Offline and Online databases. We can use these features across the Organizatoin with `low latency` and `high performance`.
It also very useful with the `Streaming` and `Real-time data` to get the neccesary features in the Real-time manner.

## Major Componenets in KFS

- Katonic Feature Store - It is a place where we store all the features and keep track of all the features to understand the `drift` and `variation` in them. It also includes a `Feature Registry` with which we can log all the operations and meta-data.
- Feature View - A set of features from the data will get mapped with a Feature view. All these mapping will be done by setting the entity key (Unique Identifier). It will store the General Information which is helpful for the organization. Examples: Project Name, Owner, Description, etc.
- Registry - It is a Logging engine which will keep track of all the changes inside a feature store. :ledger:

## Feature Store contains following Components.

| Metadata - All the General Information regarding the Project.                                                     |
| :---------------------------------------------------------------------------------------------------------------- |
| Key Attributes - The Entity Keys we defined for that Feature View.                                                |
| Features - Required features we defined for the storing and inference purpose.                                    |
| Sources - Online, Offline Data sources and Data Frames (pandas & spark) for the data ingestion into Feature View. |

<p align="center">
  <img 
    width="1000"
    height="400"
    src="https://raw.githubusercontent.com/katonic-dev/katonic-feature-store/kfs-platform-dev/workflow/kfs-workflow.png?token=GHSAT0AAAAAABRWQKY4SZ7HHAAD3PJIYKOOYSCV55A"
  >
</p>
## User Guide (Getting Started)
# Technical Stack

- Python
- Offline Source : Parquet file (Private Bucket)
- Online Source : Redis
- Data frame Sources : Pandas & Spark

## House Price Prediction

# Feature Store Demo

1. Importing the Requried Modules

```python
from kfs import FeatureStore
```

#### Then you need to Initialize a Feature Store by Giving several parameters .

```python
fs = FeatureStore(
    user_name = "username",
    project_name = "demo_project",
    description = "house_price_prediction",
)
```

#### This will configure with the Offline store and Online store along with Registry and Initializes an registry table in the Postgres server.

Now, we configured and initialized a Feature Repository and a Feature store in it. We can store and retrieve the features from it.

### Using File source as a Data Source.

```python

from kfs import Entity, Feature, FeatureView, ValueType, FileSource

# Entity
entity = Entity(name="id", value_type=ValueType.INT64)

data_source = FileSource(
    path = "datasets/housing_data.csv", # Provide a path for your data source file.
    file_format = "csv", # format of your data sourse CSV or PARQUET.
    event_timestamp_column = "event_timestamp"  # The column which represents the time of Event occurance.
)
```

#### In this we are Defining a Entity key along with the _DataType_ for mapping the data records along with the Entity ID. So we can use them when we are ingesting and retrieving the features with the feature store.

#### We've also given a timestamp column so we can do the point-in-time joins. As well as to retrieve the latest features for inference.

These Feature views allow users to store required features in their organizations into Feature Store for Offline and Online stores, and then use them for both offline training and online inference.

The preceding feature view definition tells Feature Store how to store features in the feature view.

#### Let's Define a `Feature View` by using the above _Entity_ Identifier and the _BatchSource_.

```python
cols = ['bedrooms', 'bathrooms', 'sqft_living',
       'sqft_lot', 'floors', 'waterfront', 'view', 'condition', 'grade',
       'sqft_above', 'sqft_basement']

driver_hourly_stats_view  = FeatureView(
    name="house_price_prediction",
    entities=["id"],
    ttl="2h", # no of days/months/years/hours
    features=cols,
    batch_source=batch_source,
)
```

#### Now that we have defined our feature view, we can apply the changes to create our Offline store and configure our infrastructure:

Registering and Deploying the Features to Offline Store.

```python
====== Writing data into Offline Store.
fs.write_table([entity_key,house_price_prediction_view])

```

The preceding `write_table` function will:

- Store all entity and feature view definitions in a table in Postgres.
- Create an `Offline Store` on `Private-Bucket`.
- Create an empty table in `Redis-server` with the infrastructure for Online store.
- Ensure that your data source on `batch_source` was available.

# Building a Training Dataset.

As we already know the features that we want to use for Modelling. We can directly call them from Offline Store of the Kfs.

| Please make sure that your entity dataframe should contain both entity key column and event timestamp column. Then only it will perform the point-in-time joins. |
| :--------------------------------------------------------------------------------------------------------------------------------------------------------------- |

```python
import pandas as pd

orders = pd.read_csv(data.csv")

training_df = fs.get_historical_features(
    entity_df=orders,
    feature_view = ["house_price_prediction"], # Your feature view name
    features = cols, # Columns you want to retrieve
).to_df()

```

Then we make a query internally from Feature Store to enrich our housing dataset. Feature Store will automatically detect the `id` column and join the feature data in a point-in-time correct way and Return a `Pandas` DataFrame.

Once we have retrieved the complete training dataset, we can use this dataset in order train a model.

# Modelling:

By using the above pandas dataframe we can build a model.

```python
from joblib import dump
from sklearn.linear_model import LinearRegression

# Train model
target = `target_feature`

====== #Splitting data into train and test sets.

X_train = training_df.drop(["event_timestamp","price","id","house_price_prediction_postgres__entity_row_unique_id","entity_timestamp"],axis=1)
y_train = training_df["price"]

======= #Model Training.

model = LinearRegression()
model.fit(X_train,y_train)
dump(rfc,"ouse_price_prediction.bin")
```

Before we can make online predictions with our house_price_prediction model, we must populate our online store with latest feature values. To load features into the online store, we use `publish_table` function:
It will load all the latest into Online store(`Redis`) for the low-latency inference.

```python

import datetime

fs.publish_table(
    start_ts = datetime.datetime(2021,10,1),
    end_ts = datetime.datetime(2021,11,1)
)
```

This function will load features from our `offline store` from `start_date` up to the `end_date`. The `publish_table` function can be repeatedly called as more data becomes available in order to keep the online store updated.

```python
ids = [540100056,1138010520,3524039060]

test = fs.get_online_features(
    entity_rows=[{"id": id} for id in ids],
    feature_view=["house_price_prediction_postgres"],
    features=cols,
).to_df()

```

It will returns a `Pandas` DataFrame which we can use for making prediction from a `Pre-trained Model`.

![Pandas DataFrame with Features retrieved from Online Source](https://raw.githubusercontent.com/katonic-dev/katonic-feature-store/kfs-platform-dev/docs/sources/Online_feat_df.jpg?token=GHSAT0AAAAAABRWQKY5VMDG4HEKMXSSLU44YSCWCCA)

### Then we can make inferences for the Data that we received from the Feature Store using Pre-trained model.

```python

model = load("house_price_prediction.bin")
# Make prediction
model.predict(test.drop("id",axis=1))

```

## Output

```python

> array([668436.1048679 , 426522.67860638, 172935.54659541])

```
