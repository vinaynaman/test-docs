# Reids Online Store

The Reids server will be used as a Online store for Kfs to materialize the features and provide with latest data at low-latency.

- The `publish_table()` will be used to store them in `Redis-Server`.

User had no need to configure or provide any details to setup the Redis-Server connection. It will be handled by the platform internally.

# Sample publishing code

```python
import datetime

fs.publish_table(
    start_ts = datetime.datetime(XX,XX,XXXX),
    end_ts = datetime.datetime(XX,XX,XXXX)
)
```
