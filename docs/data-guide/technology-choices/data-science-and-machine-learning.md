---
title: Choosing a machine learning technology
description: 
author: zoinerTejada
ms:date: 02/12/2018
---

# Choosing a machine learning technology in Azure

Data science and machine learning is a workload that is usually undertaken by data scientists. It requires specialized tools, many of which are designed specifically for the type of interactive data exploration and modeling tasks that a data scientist must perform.

Machine learning solutions are built iteratively, and have two distinct phases:
* Data preparation and modeling.
* Deployment and consumption of predictive services.

## Tools and services for data preparation and modeling
Data scientists typically prefer to work with data using custom code written in Python or R. This code is generally run interactively, with the data scientists using it to query and explore the data, generating visualizations and statistics to help determine the relationships within it. There are many interactive environments for R and Python that data scientists can use. A particular favorite is **Jupyter Notebooks** that provides a browser-based shell that enables data scientists to create *notebook* files that contain R or Python code and markdown text. This approach for modeling using notebooks has become a paradigm for data science, and as a result there now many other notebook options including Databricks Notebooks and Azure Notebooks. This is an effective way to collaborate by sharing and documenting code and results in a single document.

Other commonly used tools include:
* **Spyder**: The interactive development environment (IDE) for Python provided with the Anaconda Python distribution.
* **R Studio**: An IDE for the R programming language.
* **Visual Studio Code**: A lightweight, cross-platform coding environment that supports Python as well as commonly used frameworks for machine learning and AI development.

In addition to these tools, data scientists can leverage Azure services to simplify code and model management.


### Azure Databricks 
[Azure Databricks](/azure/azure-databricks/what-is-azure-databricks) is the premiere place to run Spark workloads in Azure, and provides data scientists with an environment that supports the entire data science process. Owing to their deep integration with Azure Databricks, [Azure Databricks notebooks](https://docs.azuredatabricks.net/user-guide/notebooks/index.html) provide the most comprehensive notebook experience, supporting the entire data exploration and modeling life-cycle including purpose built features that support notebook authoring, dependency management, workspaces for organization and sharing of notebooks and artifacts, version control and automation. 

Databricks notebooks support Python, R, SQL and Scala. Out of the box they include interactive and eye-pleasing visualizations, but also support the open source charting libraries like ggplot, matplotlib, bokeh and seaborn that data scientists are already familiar with.

Databricks notebooks provide an enhanced experience for the execution of Spark code that includes things like live-updating status bars that report on distributed job progress, error highlighting that make it easier to see what went wrong both in the code and with clear error messages, and built-in support for running structured streaming jobs and showing updated data in tables and visualizations in near real-time and widgets that allow notebook authors to provide better interactive experiences when providing inputs to the notebook. Notebooks authored in Azure Databricks can be exported to a file and downloaded, or checked directly into version control repositories (such as GitHub).

Azure Databricks enhances the overall notebook experience through an organizing feature called workspaces. Within a workspace, data scientists can organize their folder hierarchy of notebooks, scripts and libraries (e.g., python or R packages). They can securely share notebooks with specific users or drop them in shared folder for access by all users who have access to the workspace. Additionally, they can define tables that represent prepared data stored in Blob storage, Data Lake Store, SQL Data Warehouse or Cosmos DB enabling other data scientists on the team to query the prepared data in their own notebooks using SQL or the Spark Dataframe/Dataset API's. The workspace also allows the data scientist to configure role-based access controls against these tables, for example restricting which other members of the workspace can query them.   

The workspace also provides access to the clusters that are available for the data scientist to use in executing their notebook code, and simplifies the tasks of switching between existing clusters (which can be done within an open notebook), configuring clusters with settings and libraries, and creating new clusters. 

The clusters supported by Azure Databricks come in multiple flavors. There are standard clusters that are pre-provisioned by data scientists or data engineers to have a certain minimal capacity for both the Spark driver node and the Spark worker nodes. There are also serverless pools, where the resources to support interactive Spark workloads are provided dynamically by Azure Databricks itself,  where the Spark tasks are managed to ensure fairness across users and isolation between executing notebooks. Additionally, the clusters provide different Databricks runtime version. For example, the ML runtime provides clusters that pre-configured specifically for doing deep-learning, including the necessary scale-out GPU drivers and deep learning libraries. All options support autoscale, whereby the cluster will automatically scale compute up or down within a specified number of worker nodes according to the load (measured in terms of pending Spark tasks) on the cluster.  

When it comes to model training and evaluation, Spark in Azure Databricks includes Spark MLlib, a framework and library for machine learning. The Microsoft Machine Learning library for Spark (MMLSpark) is also available and provides scale-out deep learning algorithm support for the training and evaluation of predictive models in Spark.

Key benefits:

* A managed experience for doing data science end-to-end in Azure, requiring only a browser.
* Provides the best experience for authoring and running Spark applications, providing a distributed platform that offers high scalability for high-volume machine learning processes.
* Organizes and secures all artifacts of the data science process, from notebooks, to data, to clusters.
* Enables simplified collaboration between all collaborators.
* You can view notebook contents without a running cluster.
* Supports multiple layers of access control, enabling control over who can use which clusters, which notebooks users can access and what table data users can query. 

Considerations:

* You will be unable to access your notebooks when offline.
* Running a cluster incurs charges and some operations will require a running cluster, such as listing, creating or querying tables or executing notebooks.


### Azure Notebooks
Azure Notebooks is an online Jupyter Notebooks service that enables data scientists to create, run, and share Jupyter Notebooks in cloud-based libraries.

Key benefits:

* Free service&mdash;no Azure subscription required.
* No need to install Jupyter and the supporting R or Python distributions locally&mdash;just use a browser.
* Manage your own online libraries and access them from any device.
* Share your notebooks with collaborators.

Considerations:

* You will be unable to access your notebooks when offline.
* Limited processing capabilities of the free notebook service may not be enough to train large or complex models.

### Data science virtual machine
The data science virtual machine is an Azure virtual machine image that includes the tools and frameworks commonly used by data scientists, including R, Python, Jupyter Notebooks, Visual Studio Code, and libraries for machine learning modeling such as the Microsoft Cognitive Toolkit. These tools can be complex and time consuming to install, and contain many interdependencies that often lead to version management issues. Having a preinstalled image can reduce the time data scientists spend troubleshooting environment issues, allowing them to focus on the data exploration and modeling tasks they need to perform.

Key benefits:
* Reduced time to install, manage, and troubleshoot data science tools and frameworks.
* The latest versions of all commonly used tools and frameworks are included.
* Virtual machine options include highly scalable images with GPU capabilities for intensive data modeling.

Considerations:
* The virtual machine cannot be accessed when offline.
* Running a virtual machine incurs Azure charges, so you must be careful to have it running only when required.

### Azure Machine Learning

Azure Machine Learning is a cloud-based service for managing machine learning experiments and models. It includes an experimentation service that tracks data preparation and modeling training scripts, maintaining a history of all executions so you can compare model performance across iterations. A cross-platform client tool named Azure Machine Learning Workbench provides a central interface for script management and history, while still enabling data scientists to create scripts in their tool of choice, such as Jupyter Notebooks or Visual Studio Code.

From Azure Machine Learning Workbench, you can use the interactive data preparation tools to simplify common data transformation tasks, and you can configure the script execution environment to run model training scripts locally, in a scalable Docker container, or in Spark.

When you are ready to deploy your model, use the Workbench environment to package the model and deploy it as a web service to a Docker container, Spark on Azure HDinsight, Microsoft Machine Learning Server, or SQL Server. The Azure Machine Learning Model Management service then enables you to track and manage model deployments in the cloud, on edge devices, or across the enterprise.

Key benefits:

* Central management of scripts and run history, making it easy to compare model versions.
* Interactive data transformation through a visual editor.
* Easy deployment and management of models to the cloud or edge devices.

Considerations:
* Requires some familiarity with the model management model and Workbench tool environment.

### Azure Batch AI

Azure Batch AI enables you to run your machine learning experiments in parallel, and perform model training at scale across a cluster of virtual machines with GPUs. Batch AI training enables you to scale out deep learning jobs across clustered GPUs, using frameworks such as Cognitive Toolkit, Caffe, Chainer, and TensorFlow. 

Azure Machine Learning Model Management can be used to take models from Batch AI training to deploy, manage, and monitor them. 

### Azure Machine Learning Studio

Azure Machine Learning Studio is a cloud-based, visual development environment for creating data experiments, training machine learning models, and publishing them as web services in Azure. Its visual drag-and-drop interface lets data scientists and power users create machine learning solutions quickly, while supporting custom R and Python logic, a wide range of established statistical algorithms and techniques for machine learning modeling tasks, and built-in support for Jupyter Notebooks.

Key benefits:

* Interactive visual interface enables machine learning modeling with minimal code.
* Built-in Jupyter Notebooks for data exploration.
* Direct deployment of trained models as Azure web services.

Considerations:

* Limited scalability. The maximum size of a training dataset is 10 GB.
* Online only. No offline development environment.

## Tools and services for deploying machine learning models

After a data scientist has created a machine learning model, you will typically need to deploy it and consume it from applications or in other data flows. There are a number of potential deployment targets for machine learning models.

### Web service in a container

You can deploy a machine learning model as a Python web service in a Docker container. You can deploy the model to Azure or to an edge device, where it can be used locally with the data on which it operates.

Key Benefits:

* Containers are a lightweight and generally cost effective way to package and deploy services.
* The ability to deploy to an edge device enables you to move your predictive logic closer to the data.
* You can deploy to a container directly from Azure Machine Learning Workbench.

Considerations:

* This deployment model is based on Docker containers, so you should be familiar with this technology before deploying a web service this way.

### Microsoft Machine Learning Server

Machine Learning Server (formerly Microsoft R Server) is a scalable platform for R and Python code, specifically designed for machine learning scenarios.

Key benefits:

* High scalability.
* Direct deployment from Azure Machine Learning Workbench.

Considerations:

* You need to deploy and manage Machine Learning Server in your enterprise.

### Microsoft SQL Server

Microsoft SQL Server supports R and Python natively, enabling you to encapsulate machine learning models built in these languages as Transact-SQL functions in a database.

Key benefits:

* Encapsulate predictive logic in a database function, making it easy to include in data-tier logic.

Considerations:

* Assumes a SQL Server database as the data tier for your application.

### Azure Machine Learning web service

When you create a machine learning model using Azure Machine Learning Studio, you can deploy it as a web service. This can then be consumed through a REST interface from any client applications capable of communicating by HTTP.

Key benefits:

* Ease of development and deployment.
* Web service management portal with basic monitoring metrics.
* Built-in support for calling Azure Machine Learning web services from Azure Data Lake Analytics, Azure Data Factory, and Azure Stream Analytics.

Considerations:

* Only available for models built using Azure Machine Learning Studio.
* Web-based access only, trained models cannot run on-premises or offline.

### Azure Databricks

Models can be loaded and utilized by Azure Databricks notebooks for the purposes of scoring in batch, in a scale out fashion across large data sets. Azure Databricks also allows you to schedule the execution of notebooks using its Jobs feature. This enables you to perform batch scoring on a regular schedule, using models you load from external storage like Azure Blob storage. 

Key benefits:

* Scalable approach for performing batch scoring over large data sets.
* Can execute batch scoring on a schedule. 

Considerations:

* Not suitable for single record at a time style scoring via a web service.  
