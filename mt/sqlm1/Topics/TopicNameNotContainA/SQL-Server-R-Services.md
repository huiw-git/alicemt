---
title: SQL Server R Services
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ba1dea65-40ea-484a-b767-53680c954934
---
# SQL Server R Services
  [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] provides a platform for developing and deploying intelligent applications that uncover new insights. You can use the rich and powerful R language and the many packages from the community to create models and generate predictions using your [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] data. Because [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] integrates the R language with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you can keep analytics close to the data and eliminate the costs and security risks associated with data movement.  
  
 [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] supports the open source R language with a comprehensive set of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] tools and technologies that offer superior performance, security, reliability and manageability. You can deploy R solutions using convenient, familiar  tools, and your production applications can call the R runtime and retrieve predictions and visuals using [!INCLUDE[tsql](../../Token\Other/tsql_md.md)]. You also get the [ScaleR](http://www.revolutionanalytics.com/revolution-r-enterprise-scaler) libraries to improve the scale and performance of your R solutions.  
  
In [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] provides both server and client components.  
  
+   **R Services \(In\-Database\):** Install this feature during [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] setup to enable secure execution of R scripts on the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] computer.  
  
     When you select this feature, extensions  are installed in the database engine to support execution of R scripts, and a new service is created, the [!INCLUDE[rsql_launchpad](../../Token\Other/rsql_launchpad_md.md)], to manage communications between the R runtime and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance.  
  
+   **Microsoft R Client:** A free tool that lets data scientists develop R solutions from their workstations while working with production data that resides on the SQL Server. If your solution uses the **ScaleR** functions, you can specify that computations run on the SQL Server computer for greater scalability. [Microsoft R Client](http://go.microsoft.com/fwlink/?LinkId=799768)  is available as a separate, free installer.  
  
+ **Microsoft R:** When you install either the in-database server or the client, you get not just the basic R libraries, but enhanced connectivity and performance libraries, such as **ScaleR**. You can use the same code on your laptop and on the server, but get far greater performance and scalability if you run computations on the SQL Server computer.  
  
## Additional Resources  
  
 [Getting Started with SQL Server R Services](../../Topics\TopicNameNotContainA/Getting-Started-with-SQL-Server-R-Services.md)   
 Describes common scenarios for uses of R with SQL Server.  
  
[Set Up SQL Server R Services In-Database](Set%20up%20SQL%20Server%20R%20Services%20\(In-Database\).md)  
Install R and associated database components as part of SQL Server setup.  
  
[SQL Server R Services Tutorials](SQL%20Server%20R%20Services%20Tutorials.md)  
Learn how to create SQL Server data sources in your R code, and how to use remote compute contexts. Other tutorials aimed at SQL developers demonstrate how to train and deploy an R model in SQL Server.  
  
## See Also  
  
 [Getting Started with Microsoft R Server &#40;Standalone&#41;](../Topic/Getting%20Started%20with%20Microsoft%20R%20Server%20\(Standalone\).md)  
  
  