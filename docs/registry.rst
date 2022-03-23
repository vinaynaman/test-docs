Registry
========

Kfs Registy is a tracking engine for the feature definitions and their
related metadata. It will be used for catalog all the transactions and
modifications through out the feature store. So, when a user want to
filter out their feature views or related operations this will be useful
to discover them.

Each of the Feature store will consists of a registy which have al the
metadata of multiple feature views also, user & projects.

It will supports ``Postgres`` to store all the metadata.

-  ``Postgres`` - It will create a table on Postgres at the backend for
   storing the actions.

The Registry will get updated during different operations when using
Kfs. More Specifically when the modifications or additions will done
inside the Kfs. Like adding a feature view or entity keys.

This will get used for the Kfs User interface where users will get a
simplified view of feature store.

Interpreting the Feature Registry.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

You can view the registry inside a feature store with the following
code.

.. code:: python

   # You can provide a project name, user name or both, As needed.
   fs.get_registry_info(project_name,user_name)

Schema for the Feature Store Registry:
======================================

.. code:: python

   # Registry Schema

    id # Serial key which acts as Primary key,
   project_name # your project name,
   user_name # User name,
   description # project description,
   feature_table # Feature table name,
   feature_table_version # version of the feature view,
   created # created timestamp for the feature view,
   last_modified # last modified time of the feature view,
   last_modified_by # user name of the person who modified the feature view recently,
   primary_key # entity key of the feature view,
   no_of_features # no.of features in the feature view,
   features # features name along with their data types,
   event_timestamp_column # event timestamp column name,
   created_timestamp_column # created timestamp column if provided else none,
   data_source # details of the provided data source,
   offline_store # offline store details,
   online_store # onlien store details,
   type # status of the feature view,
   online # whether the feature view can be used for serving purpose,
   stage # whether the feature view is updated or inserted
