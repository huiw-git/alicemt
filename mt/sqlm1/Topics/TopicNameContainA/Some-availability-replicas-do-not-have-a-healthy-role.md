---
title: Some availability replicas do not have a healthy role
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7ec5b337-7201-4a66-a541-7560f8b18784
---
# Some availability replicas do not have a healthy role
    
## Introduction  
  
|||  
|-|-|  
|**Policy Name**|Availability Replicas Role State|  
|**Issue**|Some availability replicas do not have a healthy role.|  
|**Category**|**Warning**|  
|**Facet**|Availability group|  
  
## Description  
 This policy rolls up the connection state of all availability replicas and checks if there are any availability replicas that are not in a healthy role. The policy is in an unhealthy state when any availability replica is neither primary nor secondary. The policy is otherwise in a healthy state.  
  
> [!NOTE]  
>  For this release of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], information about possible causes and solutions is located at [Some availability replicas do not have a healthy role](http://go.microsoft.com/fwlink/p/?LinkId=220854) on the TechNet Wiki.  
  
## Possible Causes  
 In this availability group, at least one availability replica does not currently have the primary or secondary role.  
  
## Possible Solution  
 Use the availability replica policy state to find the availability replica whose role is not primary or secondary, and then resolve the issue at the availability replica.  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Use the Always On Dashboard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always%20On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)  
  
  