---
title: "Data synchronization state of availability database is not healthy"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4fd003e7-808e-4b0e-b28a-47d9f2616f06
caps.latest.revision: 16
caps.handback.revision: 0
manager: mblythe
---
# Data synchronization state of availability database is not healthy
## Introduction  
  
|||  
|-|-|  
|**Policy Name**|Availability Database Data Synchronization State|  
|**Issue**|Data synchronization state of availability database is not healthy.|  
|**Category**|**Warning**|  
|**Facet**|Availability database|  
  
## Description  
 This policy rolls up the data synchronization state of all availability databases (also known as "database replicas") in the availability replica. The policy is in an unhealthy sate when any database replica is not in the expected data synchronization state. The policy is otherwise in a healthy state.  
  
> [!NOTE]  
>  For this release of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)], information about possible causes and solutions is located at [Data synchronization state of some availability database is not healthy](http://go.microsoft.com/fwlink/p/?LinkId=220858) on the TechNet Wiki.  
  
## Possible Causes  
 The data synchronization state of this availability database is unhealthy. On an asynchronous-commit availability replica, every availability database should be in the SYNCHRONIZING state. On a synchronous-commit replica, every availability database must be in the SYNCHRONIZED state.  
  
## Possible Solution  
 Use the database replica policy to find the database replica with an unhealthy data synchronization state, and then resolve the issue at the database replica.  
  
## See Also  
 [Overview of Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md)   
 [Use the Always On Dashboard (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Use-the-Always-On-Dashboard--SQL-Server-Management-Studio-.md)