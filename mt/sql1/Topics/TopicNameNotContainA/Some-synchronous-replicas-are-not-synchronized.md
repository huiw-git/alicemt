---
title: "Some synchronous replicas are not synchronized"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e58ed56e-4c30-42e6-a9fc-a8c401620e02
caps.latest.revision: 12
caps.handback.revision: 0
manager: jhubbard
---
# Some synchronous replicas are not synchronized
## Introduction  
  
|||  
|-|-|  
|**Policy Name**|Synchronous Replicas Data Synchronization State|  
|**Issue**|Some synchronous replicas are not synchronized.|  
|**Category**|**Warning**|  
|**Facet**|Availability group|  
  
## Description  
 This policy rolls up the data synchronization state of all availability replicas and checks for any availability replicas that are not in the expected synchronization state. The policy is in an unhealthy state when any asynchronous replica is not in a SYNCHRONIZING state and any synchronous replica is not in a SYNCHRONIZED state. The policy state is otherwise healthy.  
  
> [!NOTE]  
>  For this release of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)], information about possible causes and solutions is located at [Some synchronous replicas are not synchronized](http://go.microsoft.com/fwlink/p/?LinkId=220853) on the TechNet Wiki.  
  
## Possible Causes  
 In this availability group, at least one synchronous replica is not currently synchronized. The replica synchronization state could be either SYNCHONIZING or NOT SYNCHRONIZING.  
  
## Possible Solution  
 Use the availability replica policy state to find the availability replica with the incorrect synchronization state, and then resolve the issue at the availability replica.  
  
## See Also  
 [Overview of Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md)   
 [Use the Always On Dashboard (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Use-the-Always-On-Dashboard--SQL-Server-Management-Studio-.md)