---
title: Some availability replicas are not synchronizing data
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3db6a569-e942-4321-a0dd-c4ab002087c8
---
# Some availability replicas are not synchronizing data
    
## Introduction  
  
|||  
|-|-|  
|**Policy Name**|Availability Replicas Data Synchronization State|  
|**Issue**|Some availability replicas are not synchronizing data.|  
|**Category**|**Warning**|  
|**Facet**|Availability group|  
  
## Description  
 This policy rolls up the data synchronization state of all availability replicas in the availability group and checks if the synchronization of any availability replica is not operational. The policy is in an unhealthy state if any of the data synchronization states of the availability replica is NOT SYNCRONIZING.  
  
 This policy is in a healthy state if none of the data synchronization states of the availability replica is NOT SYNCHRONIZING.  
  
> [!NOTE]  
>  For this release of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], information about possible causes and solutions is located at [Some availability replicas are not synchronizing data](http://go.microsoft.com/fwlink/p/?LinkId=220852) on the TechNet Wiki.  
  
## Possible Causes  
 In this availability group, at least one secondary replica has a NOT SYNCHRONIZING synchronization state and is not receiving data from the primary replica.  
  
## Possible Solution  
 Use the availability replica policy state to find the availability replica with a NOT SYNCHROINIZING state, and then resolve the issue at the availability replica.  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Use the Always On Dashboard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always%20On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)  
  
  