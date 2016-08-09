---
title: "Managing and Monitoring R Solutions"
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
ms.assetid: d455f22a-190f-4a28-9088-98a843cd5db2
caps.latest.revision: 15
caps.handback.revision: 0
manager: paulettm
---
# Managing and Monitoring R Solutions
Database administrators must integrate competing projects and priorities into a single point of contact: the database server. They must provide data access not just to data scientists but to a variety of report developers, business analysts, and business data consumers, while maintaining the health of operational and reporting data stores. In the enterprise, the DBA is a critical part of building and deploying an effective infrastructure for data science. [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] provides many benefits to the database administrator who supports the data science role.  
  
-   **Security.** The architecture of [!INCLUDE[rsql_productname](../../Topics/TopicNameContainA/tokens/rsql_productname_md.md)] keeps your databases secure and isolates the execution of R sessions from the operation of the database instance .  
  
     You can specify who has permission to execute the R scripts and ensure that the data used in R jobs is managed using the same security roles that are defined in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)].  
  
-   **Reliability.** R sessions are executed in a separate process to ensure that your server continues to run as usual even if the R session encounters issues.  
  
-   **Resource governance.** You can control the amount of resources allocated to the R runtime, to prevent massive computations from jeopardizing the overall server performance.  
  
> [!NOTE]  
>  This section is under construction.  
  
## In This Section  
 [Determine Which Packages are Installed on SQL Server](../../Topics/TopicNameNotContainA/Determine-Which-Packages-are-Installed-on-SQL-Server.md)  
  
 [Install Additional R Packages on SQL Server](../../Topics/TopicNameNotContainA/Install-Additional-R-Packages-on-SQL-Server.md)  
  
 [Configure and Manage Advanced Analytics Extensions](../../Topics/TopicNameNotContainA/Configure-and-Manage-Advanced-Analytics-Extensions.md)  
  
 [Security Considerations for the R Runtime in SQL Server](../../Topics/TopicNameNotContainA/Security-Considerations-for-the-R-Runtime-in-SQL-Server.md)  
  
 [Modify the User Account Pool for SQL Server R Services](../../Topics/TopicNameNotContainA/Modify-the-User-Account-Pool-for-SQL-Server-R-Services.md)  
  
## See Also  
 [SQL Server R Services Features and Tasks](../../Topics/TopicNameNotContainA/SQL-Server-R-Services-Features-and-Tasks.md)