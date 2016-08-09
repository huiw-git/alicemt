---
title: "Host a Report Server Database in a SQL Server Failover Cluster"
ms.custom: na
ms.date: 2016-03-30
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7bd5f019-2857-452f-a023-cc3b9e93aec4
caps.latest.revision: 6
caps.handback.revision: 0
manager: mblythe
---
# Host a Report Server Database in a SQL Server Failover Cluster
[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provides failover clustering support so that you can use multiple disks for one or more [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instances. Failover clustering is supported only for the report server database; you cannot run the Report Server service as part of a failover cluster.  
  
 To host a report server database on a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] failover cluster, the cluster must already be installed and configured. You can then select the failover cluster as the server name when you create the report server database in the Database Setup page of the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] Configuration tool.  
  
 Although the Report Server service cannot participate in a failover cluster, you can install [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] on a computer that has a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] failover cluster installed. The report server runs independently of the failover cluster. If you install a report server on a computer that is part of a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] failover instance, you are not required to use the failover cluster for the report server database; you can use a different [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance to host the database.  
  
## See Also  
 [Report Server Database (SSRS Native Mode)](../../Topics/TopicNameNotContainA/Report-Server-Database--SSRS-Native-Mode-.md)   
 [Create a Report Server Database  (SSRS Configuration Manager)](../../Topics/TopicNameContainA/Create-a-Report-Server-Database---SSRS-Configuration-Manager-.md)