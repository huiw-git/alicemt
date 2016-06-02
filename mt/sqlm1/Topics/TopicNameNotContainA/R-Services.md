---
title: R Services
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 341e80f5-3b59-4122-bbaa-969d7904297d
---
# R Services
  Microsoft R Services provides two server platforms for integrating the popular open source R language with business applications: **SQL Server R Services \(In\-Database\)**, for integration with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], and **Microsoft R Server**.  
  
-   **R Services \(In\-Database\)**  
  
     The goal of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] is to enable rapid development, deployment, and operationalization of R solutions based on the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] platform and related services.  
  
     [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] brings the compute to the data by allowing R to run on the same computer as the database. It includes a database service that runs outside the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] process and communicates securely with the R runtime. You can train R models, generate R plots, perform scoring, and easily move data between R and [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Data scientists who are testing and developing solutions can communicate with the server from a remote development computer to run R code on the server, and deploy completed solutions to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] by embedding calls to R in stored procedures.  
  
     This download includes a distribution of the open source R language, as well as ScaleR, a set of high\-performance, scalable R packages. It also includes providers for easier, faster connectivity with all [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] technologies.  
  
     For more information, see [SQL Server R Services](../../Topics\TopicNameNotContainA/SQL-Server-R-Services.md). For sample scenarios, see  [SQL Server R Services Tutorials](../Topic/SQL%20Server%20R%20Services%20Tutorials.md).  
  
-   **Microsoft R Server**  
  
     This standalone server system supports distributed, scalable R solutions on multiple platforms and using multiple enterprise data sources, including Linux, Hadoop, and Teradata.  
  
     For more information, see [Microsoft R Server \(MSDN\)](https://msdn.microsoft.com/microsoft-r/index).  
  
## Related Technologies  
 Microsoft provides broad support for the open source R language ecosystem, including tools, providers, enhanced R packages, and integrated development environments.  
  
-   **R Tools for Visual Studio**  
  
     In 2016, Visual Studio provides a full development environment for the R language, much like the Python Tools for Visual Studio. The plug\-in includes an editor, interactive window, plotting, debugger, and more. You can use .NET languages from R or invoke R from .NET via open source libraries such as R.NET and rClr.  
  
     For more information, see [R Tools for Visual Studio](https://www.visualstudio.com/features/rtvs-vs.aspx).  
  
-   **R in Azure Machine Learning**  
  
     Create your own workspace in Azure Machine Learning Studio, where you can access over 400 preloaded R packages. Build and train models to deploy as a Web service, or write custom scripts to transform data. Create your own R packages and upload them to Azure to run as custom modules, and publish solutions to the [Machine Learning Marketplace](http://datamarket.azure.com/browse/data?category=machine-learning).  
  
     For more information, see [Extend your experiment with R](https://azure.microsoft.com/documentation/articles/machine-learning-extend-your-experiment-with-r/) and [Author custom R modules in Azure Machine Learning](https://azure.microsoft.com/documentation/articles/machine-learning-custom-r-modules/).  
  
-   **Microsoft Data Science Virtual Machine**  
  
     You can deploy a pre\-installed and pre\-configured version of [!INCLUDE[rsql_platform](../../Token\Other/rsql_platform_md.md)] Developer Edition in Microsoft Azure, making it easy to get started with data exploration and modeling right away on the cloud without setting up a fully configured system on premises.  
  
     The Microsoft Data Science  Virtual Machine is available in the Azure Marketplace, and comes pre\-configured with Python \(Anaconda distribution\), a Jupyter notebook server, Visual Studio Community Edition, Power BI Desktop, the Azure SDK, and SQL Server Express edition.  
  
## See Also  
 [Making R the Enterprise Standard for Cross Platform Analytics On\-Premise and in the Cloud](http://blogs.technet.com/b/machinelearning/archive/2016/01/12/making-r-the-enterprise-standard-for-cross-platform-analytics-both-on-premises-and-in-the-cloud.aspx)   
 [Install SQL Server Database Engine](../../Topics\TopicNameNotContainA/Install-SQL-Server-Database-Engine.md)  
  
  