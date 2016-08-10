---
title: "SQL Server Browser Properties (Advanced Tab)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ba79137a-cb72-4bf3-a650-e11d02cfce10
caps.latest.revision: 20
caps.handback.revision: 0
manager: jhubbard
---
# SQL Server Browser Properties (Advanced Tab)
The [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Browser program runs as a service on the server. [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Browser listens for incoming requests for [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] resources and provides information about [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instances installed on the computer.  
  
## Options  
 **Clustered**  
 Indicates if this service is installed as a resource of a clustered server.  
  
 **Customer Feedback Reporting**  
 Indicates whether Service Quality Monitoring has been enabled on this service. For more information on Customer Feedback Reporting, search Books Online for the topic, "Error and Usage Report Settings."  
  
 **Dump Directory**  
 The location where memory dumps are placed in case of an error.  
  
 **Error Reporting**  
 When set to **Yes**, the Dr. Watson program forwards information to either [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] or your error server if a serious failure occurs. For more information on Error Reporting, search Books Online for the topic, "Error and Usage Report Settings."  
  
 **Instance ID**  
 Indicates the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance that used this [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent instance. The default instance is **MSSQL10_50.MSSQLSERVER**.  
  
## See Also  
 [SQL Server Browser Service](../../Topics/TopicNameNotContainA/SQL-Server-Browser-Service.md)