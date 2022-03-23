# Overview :

What is Kfs?

Kfs is a python library which we can use in various phases of Machine Learning Project. We can use Kfs to store the defined features from the Online and Offline data sources and writes them in Online and Offline stores. We can use these features across the Organizatoin with low latency and high consistency. It is also very useful with the Streaming and Real-time data to get the neccesary features in the Real-time manner.

# Kfs Advantages :

# Feature Consistency

Machine Learning models are completely dependent on the data that was provided by the `Data Scientist`. So if there was a change in the Infrastructure of the data, it may lead to break the ML models. So The transformations and Logics that used for training data will also implies for the serving data, For that we can retrieve the processed features from an existing feature store for serving purpose. This will improve the consistency between the training data and serving data otherwise it will lead to training-serving skew.

# Feature Reusability

A machine learning system may build by number of data scientists or teams. Often they need to use the similar features across the teams and persons. In the process there may be a chance to create the duplicate features or losing the integrity of the data. Feature Store will also solve this problem, if once we have done the feature transformations and ingested those features into a feature store, we can use those features through out the organization,data scientists and also for different projects.

# Feature Versioning

Versioning the features in the process of Machine learning is very much crucial to have an insightful view on the features, with the versioing of them we can keep the transformed features in stages. If we don't get the desired performance from the model. We can transform them again while keeping the Old featrues in stage. It is impossbile to keep track of all the transformations that are happening in the data while processing it. To tackle this issue we can do versioning of the features and store them anytime we want. As we are maintaining a `Registy` to store all the information like feature names, their data types, updates and inserts , We can use this information to track any modifications and transactions within the feature store. This will helps the versioning of the features.
