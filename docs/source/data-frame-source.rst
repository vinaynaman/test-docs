Data Frame source
=================

Data frame source is nothing but, providing the batch source as a
DataFrame Object. It can be pandas or spark.

For this you need to pickup your data source whether it can be CSV or
Parquet and convert it into a pandas or Spark Dataframe, then All you
need to do is import the ``DataFrameSource`` function and pass that
DataFrame into it along with the event time stamp column and created
time stamp column(if available).

.. code:: python

   from kfs import DataFrameSource

   batch_source = DataFrameSource(
           df=pandas_df,
           event_timestamp_column="event_timestamp",
           created_timestamp_column="created",
       )

.. figure:: https://github.com/katonic-dev/katonic-feature-store/blob/opensource/docs/sources/dataframesource.jpg
   :alt: Pandas & Spark data frame source

   Pandas & Spark data frame source
