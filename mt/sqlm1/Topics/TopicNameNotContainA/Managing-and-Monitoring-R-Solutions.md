---
title: Managing and Monitoring R Solutions
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - r-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d455f22a-190f-4a28-9088-98a843cd5db2
---
# Managing and Monitoring R Solutions
  Database administrators must integrate competing projects and priorities into a single point of contact: the database server. They must provide data access not just to data scientists but to a variety of report developers, business analysts, and business data consumers, while maintaining the health of operational and reporting data stores. In the enterprise, the DBA is a critical part of building and deploying an effective infrastructure for data science. [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] provides many benefits to the database administrator who supports the data science role.  
  
-   **Security.** The architecture of [!INCLUDE[rsql_productname](../../Token\Other/rsql_productname_md.md)] keeps your databases secure and isolates the execution of R sessions from the operation of the database instance .  
  
     You can specify who has permission to execute the R scripts and ensure that the data used in R jobs is managed using the same security roles that are defined in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
-   **Reliability.** R sessions are executed in a separate process to ensure that your server continues to run as usual even if the R session encounters issues.  
  
-   **Resource governance.** You can control the amount of resources allocated to the R runtime, to prevent massive computations from jeopardizing the overall server performance.  
  
> [!NOTE]  
>  This section is under construction.  
  
## In This Section  
 [Monitoring R Services](../../Topics\TopicNameNotContainA/Monitoring-R-Services.md)
 
 [Resource Governance for R Services](../../Topics\TopicNameNotContainA/Resource-Governance-for-R-Services.md)
 
[Installing and Managing R Packages](../../Topics\TopicNameNotContainA/Installing-and-Managing-R-Packages.md)
  
[Configuration](Configuration%20\(SQL%20Server%20R%20Services\).md) 

+ [Configure and Manage Advanced Analytics Extensions](../../Topics\TopicNameNotContainA/Configure-and-Manage-Advanced-Analytics-Extensions.md)  
  
+  [Modify the User Account Pool for SQL Server R Services](../../Topics\TopicNameNotContainA/Modify-the-User-Account-Pool-for-SQL-Server-R-Services.md)  

 [Security Considerations for the R Runtime in SQL Server](../../Topics\TopicNameNotContainA/Security-Considerations-for-the-R-Runtime-in-SQL-Server.md)  
  
 
  
## See Also  
 [SQL Server R Services Features and Tasks](../../Topics\TopicNameNotContainA/SQL-Server-R-Services-Features-and-Tasks.md)  
  
  