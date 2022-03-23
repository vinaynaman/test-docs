# Feature Store

| To do any Operations by using the feature store, You need to initialize the feature store first by giving certain parameters regarding the user and project. |
| :----------------------------------------------------------------------------------------------------------------------------------------------------------- |

```python

from kfs import FeatureStore

fs = FeatureStore(
    user_name = "user",
    project_name = "project_name",
    description = "project_description",
)
```

- user_name : `string`
- project_name : `string`
- description : `string` [optional]
