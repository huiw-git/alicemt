---
title: Getting Started with Microsoft R Server (Standalone)
ms.custom: na
ms.prod: r-server
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 52347d0d-ce60-4bb8-98d2-6163e87716b0
---
# Getting Started with Microsoft R Server (Standalone)
  Microsoft R Server \(Standalone\)  helps you bring the popular open source R language into the enterprise, to enable high\-performance analytics solutions and integration with other business applications.  
  
## What is Microsoft R Server?  
 Microsoft R Server \(Standalone\) includes the enhanced R packages developed by Revolution Analytics and supports connections to diverse data source such as Hadoop, Teradata and more. By installing the standalone server, you can create a server environment for running complex, scalable R jobs.  
  
## Benefits of  Using Microsoft R Server \(Standalone\)  
 R is the world’s most powerful programming language for statistical computing, machine learning, and graphics, and is supported by a thriving global community of users, developers, and contributors. Traditionally, using R in an enterprise setting presents certain challenges, especially as the volume of data rises, or when you need to deploy solutions to production environments. Microsoft R Server solves the problem of deployment and operationalization of R code.  
  
 Microsoft R Server can be installed on any Windows computer and includes all the R packages and connectivity tools to enable remote compute context and to support scalable, parallelizable solutions.  
  
 Microsoft R Server supports these scenarios:  
  
-   **Using a central server to operationalize R solutions**  
  
     The standalone server gives you improved R performance without reliance on [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Complex or resource\-intensive computations can be executed on the server rather on a laptop or development computer that might have limited resources.  
  
     You can also centralize jobs, for example, if you need to score against a predictive model in production, or use the R Server as a single contact point for R plots and predictions used in reporting.  
  
-   **Enabling more powerful data exploration and predictive modeling**  
  
     The data scientist can use any client workstation and any R development tool to build R solutions. If the solution uses the RevoScaleR package APIs, computations can be performed on the server, which typically has far greater processing power and memory. thus your solutions can work with far larger datasets and leverage multi\-threaded, multi\-core, multi\-process computations.  
  
## How Do I Get It?  
 For installation instructions, see [Create a Standalone R Server](../../Topics\TopicNameContainA/Create-a-Standalone-R-Server.md). All components, including the tools for remote data science clients, can be installed by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup.  
  
## Install Additional R Tools  
 If you don't have a preferred R development already installed, there are many options. For details, see [Setup or Configure R Tools](../../Topics\TopicNameNotContainA/Setup-or-Configure-R-Tools.md).  
  
## Running R Script on Microsoft R Server \(Standalone\)  
 After you have set up the server components and installed  your favorite R IDE, you can begin developing your solution using the RevoScaleR package. These APIs let you send R commands to a remote server for execution.  
  
-   [ScaleR](https://msdn.microsoft.com/microsoft-r/rserver/rserver-getting-started): Start by exploring this collection of distributable analytical functions that provide high performance and scaling to R solutions. Includes parallelizable versions of many of the most popular R modeling packages, such as k\-means clustering, decision trees, and decision forests, and tools for data manipulation. You can also use HPC to construct your own parallel algorithm.  
  
-   [ConnectR](https://msdn.microsoft.com/microsoft-r/rserver/rserver-getting-started): Move your data efficiently and work  with data in a variety of formats, including SAS, SPSS, Hadoop, and text files. You can analyze data in place, or load it into your local R development environment using the .xdf file format.  
  
-   [DeployR](https://msdn.microsoft.com/microsoft-r/rserver/rserver-getting-started): This optional framework provides the tools for R programmers to use Java, JavaScript or .Net to integrate the R analysis output with a third party package.  
  
-   **Samples**  
  
     To get started with R Server, see this guide in the MSDN Library: [R Server \- Getting Started](https://msdn.microsoft.com/microsoft-r/rserver/rserver-getting-started)  
  
     To start working with the ScaleR packages right away, see this tutorial: [An R Tutorial in 25 Functions](https://msdn.microsoft.com/microsoft-r/rserver/rserver-getting-started)  
  
## See Also  
 [Getting Started with SQL Server R Services](../../Topics\TopicNameNotContainA/Getting-Started-with-SQL-Server-R-Services.md)  
  
  