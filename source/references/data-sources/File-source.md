# File Source

Description :

A data source will be used to write the historical features to an offline store this will get used to build training datasets. Also materializing the features into an online store(Redis-server). File sources are suggested to use for developement purposes and is not optimized if you want to use it in production.
|Make sure about the data types in your File source for avoiding any confict while doing the Join Operations.|
| :----------------------------- |
You can use either CSV or Parquet as File Sources for Kfs.

# Example :

```python
from kfs import FileSource

batch_source = FileSource(
        path=r"C:\Users\vinay namani\Desktop\Katonic.ai\katonic-feature-store\driver ranking demo\driver_stats.csv",
        file_format="csv",
    )
```
