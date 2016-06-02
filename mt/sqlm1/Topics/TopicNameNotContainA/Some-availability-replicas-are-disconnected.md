---
title: Some availability replicas are disconnected
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aea808be-6f0f-40c2-9aa2-a2a435ec6443
---
# Some availability replicas are disconnected
    
## Introduction  
  
|||  
|-|-|  
|**Policy Name**|Availability Replicas Connection State|  
|**Issue**|Some availability replicas are disconnected.|  
|**Category**|**Warning**|  
|**Facet**|Availability group|  
  
## Description  
 This policy rolls up the connection state of all availability replicas and checks for any availability replicas that are DISCONENCTED. The policy is in an unhealthy state when any availability replica is DISCONNECTED. The policy is otherwise in a healthy state.  
  
> [!NOTE]  
>  For this release of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], information about possible causes and solutions is located at [Some availability replicas are disconnected](http://go.microsoft.com/fwlink/p/?LinkId=220855) on the TechNet Wiki.  
  
## Possible Causes  
 In this availability group, at least one secondary replica is not connected to the primary replica. The connected state is DISCONNECTED.  
  
## Possible Solution  
 Use the availability replica policy state to find the availability replica that is DISCONNECTED, and then resolve the issue at the availability replica.  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Use the Always On Dashboard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always%20On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)  
  
  