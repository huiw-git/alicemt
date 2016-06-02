---
title: Availability replica is disconnected
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a2162d3-54fb-4356-b349-effbdc15a5a4
---
# Availability replica is disconnected
    
## Introduction  
  
|||  
|-|-|  
|**Policy Name**|Availability Replica Connection State|  
|**Issue**|Availability replica is disconnected.|  
|**Category**|**Critical**|  
|**Facet**|Availability replica|  
  
## Description  
 This policy checks the connection state between availability replicas. The policy is in an unhealthy state when the connection state of the availability replica is DISCONNECTED. The policy is otherwise in a healthy state.  
  
> [!NOTE]  
>  For this release of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], information about possible causes and solutions is located at [Availability replica is disconnected](http://go.microsoft.com/fwlink/p/?LinkId=220857) on the TechNet Wiki.  
  
## Possible Causes  
 The secondary replica is not connected to the primary replica. The connected state is DISCONNECTED. This issue can be caused by the following:  
  
-   The connection port might be in conflict with another application.  
  
-   The encryption type or algorithm is mismatched.  
  
-   The connection endpoint has been deleted or has not been started.  
  
-   The transport is disconnected.  
  
## Possible Solutions  
 Following are possible solutions for this issue:  
  
-   Check the database mirroring endpoint configuration for the instances of the primary and secondary replica and update the mismatched configuration.  
  
-   Check if the port is conflicting, and if so, change the port number.  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Use the Always On Dashboard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always%20On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)  
  
  