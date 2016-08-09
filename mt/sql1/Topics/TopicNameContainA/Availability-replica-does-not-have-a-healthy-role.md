---
title: "Availability replica does not have a healthy role"
ms.custom: na
ms.date: 2016-05-17
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ebb2c9f4-2097-4688-b4fb-8f0571047317
caps.latest.revision: 14
caps.handback.revision: 0
manager: jhubbard
---
# Availability replica does not have a healthy role
## Introduction  
  
|||  
|-|-|  
|**Policy Name**|Availability Replica Role State|  
|**Issue**|Availability replica does not have a healthy role.|  
|**Category**|**Critical**|  
|**Facet**|Availability replica|  
  
## Description  
 This policy checks the state of the role of the availability replica. The policy is in an unhealthy state when the role of the availability replica is neither primary nor secondary. The policy is otherwise in a healthy state.  
  
> [!NOTE]  
>  For this release of [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)], information about possible causes and solutions is located at [Availability replica does not have a healthy role](http://go.microsoft.com/fwlink/p/?LinkId=220856) on the TechNet Wiki.  
  
## Possible Causes  
 The role of this availability replica is unhealthy. The replica does not have either the primary or secondary role.  
  
## Possible Solution: Information_still_to_come  
  
## See Also  
 [Overview of Always On Availability Groups (SQL Server)](../../Topics/TopicNameNotContainA/Overview-of-Always-On-Availability-Groups--SQL-Server-.md)   
 [Use the Always On Dashboard (SQL Server Management Studio)](../../Topics/TopicNameNotContainA/Use-the-Always-On-Dashboard--SQL-Server-Management-Studio-.md)