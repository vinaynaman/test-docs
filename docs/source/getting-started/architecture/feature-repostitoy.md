# Feature Store

Users need to setup two of the most important configurations while using KFS :

- Setting up Kfs to run on their infrastructure.
- Defining the Feature views.

both the configurations need to be defined parametically and they got stored in the central repostitoy called feature store which consists of offline and online stores alond with a feature registy. This feature store will be the source for what the defined state of feature store should be.

An example structure of a feature store repostitoy is shown below:

# Structure of Feature Store :

```text
| -- data
   | ____ Offline table on (`Private bucket`)
   | ____ Registry table (Postgres)
   | ____ Online Store on (Redis server)
```
