# Data source

A data source, is a source from where Kfs will get the data to create feature view and store them in Offline & Online Stores. A data source can be anything that consists of the desired data to generate a feature view and materrialize the features.

Currently we are providing Local and Postgres services as data sources. You can use any of these things to provide the data.
If you choose file source as a data source then you've to use `FileSource` function to directly provide your file whether it can be CSV or Parquet or if you choose a table from postgres as data source you need to use `PostgreSQLSource`.

| If you're using dataframe as a source, you have to use `DataFrameSource` function to provide the data. |
| :----------------------------------------------------------------------------------------------------- |

<p align="center">
  <img 
    width="500"
    height="300"
    src="https://github.com/katonic-dev/katonic-feature-store/blob/dev-2.0/docs/sources/Data_sources.png"
  >
</p>
