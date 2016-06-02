---
title: Architecture Overview (SQL Server R Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6c4a4f66-ea3e-4a73-acf2-6c8aeafc94b0
---
# Architecture Overview (SQL Server R Services)
This section provides an overview of the architecture of [!INCLUDE[rsql_productname_md](../../Token\Other/rsql_productname_md.md)], including security, new components added in the SQL Server database engine to support R  components, and interoperability of open source R scripts running in SQL Server.


## Goals


The architecture of [!INCLUDE[rsql_productname_md](../../Token\Other/rsql_productname_md.md)] is designed to support the open source R language. Current users of R should be able to port their R code and execute it in T-SQL with relatively minor modifications.

However, SQL Server R Services also provides innovations that deliver increased performance and closer database integration for the R language,  to enable faster data throughput and processing, and to lower barriers for enterprise development of R solutions. These innovations include both open source and proprietary components developed by Microsoft.


The primary goals of integration with SQL Server are to provide improved performance and scalability for R, while managing data securely. Towards this goal, SQL Server R Services provides a multi-process infrastructure that supports both integrated Windows authentication and password-based SQL logins. 

+ [!INCLUDE[rsql_productname_md](../../Token\Other/rsql_productname_md.md)] provides a base distribution of R, together with the ScaleR packages and the ability to run R tasks in parallel.
+ New components in SQL Server provide a secure, high-performance framework for running external scripts.
+ R tasks execute outside the SQL Server process, to provide security and greater manageability.
+ [!INCLUDE[rsql_launchpad_md](../../Token\Other/rsql_launchpad_md.md)] manages the security of all R processes. 

To help you optimize existing R code and take advantage of these improvements, the topics in this section describe the new architecture in detail. By understanding how data processing and analysis is handled by [!INCLUDE[rsql_productname_md](../../Token\Other/rsql_productname_md.md)], you can make appropriate choices about how to ingest data, how to most efficiently perform feature engineering, and how to consume results.
 

## In This Section
+ [R Interoperability](../../Topics\TopicNameNotContainA/R-Interoperability-in-SQL-Server-R-Services.md)
+ [New Components in SQL Server for R Services](../../Topics\TopicNameNotContainA/New-Components-in-SQL-Server-to-Support-R-Services.md)
+ [Security Overview](Security%20Overview%20\(SQL%20Server%20R%20Services\).md)

## See Also
[R Services Tutorials](SQL%20Server%20R%20Services%20Tutorials.md)
