---
title: Machine learning at scale
description: 
author: zoinerTejada
ms:date: 02/12/2018
---

# Machine learning at scale

Machine learning (ML) is a technique used to train predictive models based on mathematical algorithms. Machine learning analyzes the relationships between data fields to predict unknown values.

Creating and deploying a machine learning model is an iterative process:

* Data scientists explore the source data to determine relationships between *features* and predicted *labels*.
* Data scientists prepare the data, typically this step involves cleaning the data and identifying or creating the features that will be used to train the model.
* The data scientists train and validate models based on appropriate algorithms to find the optimal model for prediction.
* The optimal model is deployed into production, as a web service or some other encapsulated function.
* As new data is collected, the model is periodically retrained to improve its effectiveness.

Machine learning at scale addresses two different scalability concerns. The first is training a model against large data sets that require the scale-out capabilities of a cluster to train. The second centers on operationalizating the learned model in a way that can scale to meet the demands of the applications that consume it. Typically this is accomplished by deploying the predictive capabilities as a web service that can then be scaled out or by making the model available to scale-out clusters that apply predictions in bulk. In other cases, the model, while trained against data at scale, may be embedded within a mobile or desktop application to support prediction without requiring Internet access.

Machine learning at scale has the benefit that it can produce powerful, predictive capabilities because better models typically result from more data.  

## Model data preparation and model training

During the model preparation and training phase, data scientists explore the data interactively using languages like Python and R to:

* Extract samples from high volume data stores.
* Find and treat outliers, duplicates, and missing values to clean the data.
* Determine correlations and relationships in the data through statistical analysis and visualization.
* Generate new calculated features that improve the predictiveness of statistical relationships.
* Train ML models based on predictive algorithms.
* Validate trained models using data that was withheld during training.

To support this interactive analysis and modeling phase, the data platform must enable data scientists to explore data using a variety of tools. Additionally, the training of a complex machine learning model can require a lot of intensive processing of high volumes of data, so sufficient resources for scaling out the model training is essential.

## Model deployment and consumption

When a model is ready to be deployed, it can be encapsulated as a web service and deployed in the cloud, to an edge device, or within a scale-out execution environment. The use of the model for prediction is referred to as scoring and this deployment process is referred to as operationalization.

## Challenges

Machine learning at scale produces a few challenges:

- You typically need a lot of data to train a model, especially for deep learning models.
- You need to prepare these big data sets before you can even begin training your model.
- The model training phase must access the big data stores. It's common to perform the model training using the same big data cluster, such as Spark, that is used for data preparation. 
- For scenarios such as deep learning, not only will you need a cluster that can provide you scale out on CPUs, but your cluster will need to consist of GPU-enabled nodes.
- Some models, particularly deep learning models, might require specialized nodes providing FPGA's to perform scoring efficiently and with the minimal possible latency. 

## Machine learning at scale in Azure

Before deciding which ML services to use in training and operationalization, consider whether you need to train a model at all, or if a prebuilt model can meet your requirements. In many cases, using a prebuilt model is just a matter of calling a web service or using an ML library to load an existing model. Some options include: 

- Use the web services provided by Microsoft Cognitive Services.
- Use the pretrained neural network models provided by Cognitive Toolkit or other pretrained models available from the community.
- Embed the serialized models provided by Core ML for an iOS apps. 

If a prebuilt model does not fit your data or your scenario, options for building a custom model in Azure include Azure Machine Learning, using Azure Databricks (along with MLlib, MMLSpark, SparklyR, TensorFlow or Cognitive Toolkit), SQL Machine Learning Services and Azure Batch AI. If you decide to use a custom model, you must design a pipeline that includes model training and operationalization. 

![Model options in Azure](./images/machine-learning-model-training-and-deployment.png)

For a list of technology choices for ML in Azure, see the following topics:

- [Choosing a cognitive services technology](../technology-choices/cognitive-services.md)
- [Choosing a machine learning technology](../technology-choices/data-science-and-machine-learning.md)
- [Choosing a natural language processing technology](../technology-choices/natural-language-processing.md)
