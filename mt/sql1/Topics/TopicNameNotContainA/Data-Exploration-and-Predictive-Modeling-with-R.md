---
title: "Data Exploration and Predictive Modeling with R"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-05-31
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bf6de7e2-f394-4b8a-a4b7-0b8dadf25426
caps.latest.revision: 20
caps.handback.revision: 0
manager: paulettm
---
# Data Exploration and Predictive Modeling with R
Data scientists often use R to explore data and build predictive models. This is typically an iterative process of trial and error until a good predictive model is reached. As an experienced data scientist, you  might connect to the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database and fetch the data to your local workstation using the RODBC package, explore your data, and build a predictive model using standard R packages.  
  
 However, this  approach has drawbacks. Data movement can be slow, inefficient, or insecure, and R itself has performance and scale limitations. These drawbacks become more apparent when you need to move and analyze large amounts of data, or use data sets that don’t fit into the memory available on your computer.  
  
 You can overcome these challenges by using the new scalable packages and R functions included with [!INCLUDE[rsql_rre-noversion](../../Topics/TopicNameNotContainA/tokens/rsql_rre-noversion_md.md)]. The **RevoScaleR** package contains implementations of some of the most popular R functions, which have been redesigned to provide parallelism and scale. The RevoScaleR package also provides support for changing *execution context*. What this means is that, for an entire solution or for just one function, you can indicate that computations should be performed using the resources of the computer that hosts the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance, rather than your local workstation. There are multiple advantages to doing this: you avoid unnecessary data movement, and you can leverage greater computation resources on the server computer.  
  
 This section provides guidance for the data scientists on how to use [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] and how to perform tasks related to developing and testing R solutions.  
  
##  <a name="bkmk_RDevTools"></a> R Development Tools  
 The client components in  [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] give the data scientist a complete environment for developing and testing predictive models.  
  
-   By installing  [!INCLUDE[rsql_rro-noversion](../../Topics/TopicNameNotContainA/tokens/rsql_rro-noversion_md.md)] on the client workstation, the data scientist gets a distribution of the R runtime and a set of packages, such as the Intel math kernel library, that boost the performance of standard R operations.  
  
-   By installing [!INCLUDE[rsql_rre-noversion](../../Topics/TopicNameNotContainA/tokens/rsql_rre-noversion_md.md)] on the client workstation, the data scientist gets the powerful RevoScaleR package that lets you push computations to an instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. [!INCLUDE[rsql_rre-noversion](../../Topics/TopicNameNotContainA/tokens/rsql_rre-noversion_md.md)] also includes a set of common R functions that have been redesigned to provide better performance and scalability. You can identify these improved functions  by the **rx** prefix.  
  
-   In [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] CTP3, the [!INCLUDE[rsql_developr](../../Topics/TopicNameNotContainA/tokens/rsql_developr_md.md)] IDE is also included as part of [!INCLUDE[rsql_rre-noversion](../../Topics/TopicNameNotContainA/tokens/rsql_rre-noversion_md.md)]. [!INCLUDE[rsql_developr](../../Topics/TopicNameNotContainA/tokens/rsql_developr_md.md)] provides a complete R development environment,  with Intellisense as well as improved tracing and debugging support.  
  
     However, you can use any other Windows-based code editor that support R, such as [!INCLUDE[rsql_rtvs](../../Topics/TopicNameContainA/tokens/rsql_rtvs_md.md)]. The download of [!INCLUDE[rsql_rro-noversion](../../Topics/TopicNameNotContainA/tokens/rsql_rro-noversion_md.md)] also includes common command-line tools for R such as RTerm.exe.  
  
##  <a name="bkmk_packages"></a> R Environment and Packages  
 The R environment supported in [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] consists of a runtime, the open source language, and a graphical engine supported and extended by multiple packages. The language allows a variety of extensions that are implemented using packages.  
  
 There are several sources of additional R  packages that you can use with [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] :  
  
-   Ad hoc R scripts. You can write your own R code and save your code as a stored procedure, or as a text file that can be called as a SQL variable.  
  
-   General purpose R scripts from public repositories. You can obtain the most popular open source R packages from public repositories such as CRAN, which hosts has over 6000 packages that can be used by data scientists.  
  
     Additional packages are available to support predictive analytics in special domains such as finance, genomics, and so forth.  
  
     For the Windows platform, R packages are provided as zip files and can be downloaded and installed under the GLU license.  
  
     For information about how to install third-party packages for use with [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)], see [Install Additional R Packages on SQL Server](../../Topics/TopicNameNotContainA/Install-Additional-R-Packages-on-SQL-Server.md)  
  
-   Additional packages and libraries provided by [!INCLUDE[rsql_rre-noversion](../../Topics/TopicNameNotContainA/tokens/rsql_rre-noversion_md.md)]. A set of scalable, high performance packages is included when you install [!INCLUDE[rsql_rre-noversion](../../Topics/TopicNameNotContainA/tokens/rsql_rre-noversion_md.md)].  
  
     The **RevoScaleR** package includes ready to use high performance big data analytics, improved versions of functions that support common data science tasks, optimized learners for Naive Bayes, linear regression, time series models, and neural networks, as well as advanced math libraries and packages to support development of parallelized machine learning algorithms.  
  
     The **RevoPemaR** package lets you develop your own parallel external memory algorithms in R.  
  
     For more information about these packages and how to use them, see [Tutorial: Using SQL Server R Services for Data Science](assetId:///65589d17-bd34-4baa-8ba1-998f60d0344f).  
  
## Using Data Sources and Compute Contexts  
 When using the RevoScaleR package to connect to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], there are two new functions to use in your R code:  
  
-   `RxSqlServerData` is a function provided in the RevoScaleR package to support improved data connectivity to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
     You use this function in your R code to define the *data source*. The data source object specifies the server and tables where the data resides and manages the task of  reading data from and writing data to [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
-   The `RxInSqlServer` function can be used to specify the *execution context* or *compute context*.  In other words, you can indicate where the R code should be executed: on your local workstation, or on the computer that hosts the[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance.  
  
     Note that when you set the compute context, it affects only computations that support remote execution context, which means R operations provided by the RevoScaleR package and other high-performance analytics provided by [!INCLUDE[rsql_rre-noversion](../../Topics/TopicNameNotContainA/tokens/rsql_rre-noversion_md.md)]. Typically, you cannot create an R solution using standard CRAN packages and run them in the server context; however, you can call individual R functions on the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] computer by using the **rxExec** function.  
  
 For examples of how to create and work with data sources and execution contexts,  see [Tutorial: Using SQL Server R Services for Data Science](assetId:///65589d17-bd34-4baa-8ba1-998f60d0344f).  
  
## Deploying Your R Code to Production  
 An important part of data science is providing your analyses to others, or using predictive models to improve business results or processes. In [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)], it is easy to move to production when your R script or model is ready.  
  
 For more information about how you can move your code to run in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)], see [Operationalizing Your R Code](../../Topics/TopicNameNotContainA/Operationalizing-Your-R-Code.md).  
  
 Typically the deployment process begins with cleaning up your script to eliminate code that is not needed in production.  
  
 You might also consult with the database developer about ways to move, summarise, or present data more efficiently. If you were performing extensive data preparation as part of your code, talk to your database developer about requirements for data cleansing or modification. It may be that changes to ETL processes are needed to ensure that workflows for building or scoring a model don't fail, and that input data is available in the right format.  
  
##  <a name="bkmk_SQLInR"></a> In This Section  
  
> [!NOTE]  
>  The version of [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] included in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] is  a preview release. This section is under construction.  
  
## See Also  
 [SQL Server R Services Features and Tasks](../../Topics/TopicNameNotContainA/SQL-Server-R-Services-Features-and-Tasks.md)   
 [Operationalizing Your R Code](../../Topics/TopicNameNotContainA/Operationalizing-Your-R-Code.md)