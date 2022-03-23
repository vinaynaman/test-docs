# File Source ->

We are using local file source as an Offline store to store all the Feature Views. An offline store file will be created inside a data folder within the private bucket. This file will be used to get historical feature information and to generate training datasets.

- parquet

For offline store it will create a repository as `data` . Which consisits of `offline_store` as an parquet file. (Parquet file compresses the data size and holds all the data type information where as a CSV can't store the data types.)

```bash
directory : current working directory
folder : data
file name : offline_store.parquet

```
