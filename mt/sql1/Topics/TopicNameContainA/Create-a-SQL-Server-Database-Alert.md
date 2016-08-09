---
title: "Create a SQL Server Database Alert"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0511136a-1b6b-4095-aa45-39e77b67aba2
caps.latest.revision: 23
manager: jhubbard
---
# Create a SQL Server Database Alert
You can use System Monitor to create an alert that is raised when a threshold value for a System Monitor counter has been reached. In response to the alert, System Monitor launches an application, such as a custom application written to handle the alert condition. For example, you could create an alert that is raised when the number of deadlocks exceeds a specific value.  
  
 Alerts also can be defined by using [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] and [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Agent. For more information, see [sys.sysperfinfo (Transact-SQL)](assetId:///3f57d0f0-4781-46ec-82cd-b751dc5affef).  
  
 For more information about using System Monitor to set up a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database alert, see [Set Up a SQL Server Database Alert (Windows)](../../Topics/TopicNameContainA/Set-Up-a-SQL-Server-Database-Alert--Windows-.md) .  
  
## See Also  
 [sp_add_alert](assetId:///d9b41853-e22d-4813-a79f-57efb4511f09)   
 [sysperfinfo](assetId:///e22a81cd-27de-4690-9443-6aad6393bd3c)