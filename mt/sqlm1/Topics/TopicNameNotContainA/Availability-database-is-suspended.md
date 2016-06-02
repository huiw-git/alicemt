---
title: Availability database is suspended
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6baee70f-848c-4e86-b20d-78875c0f82cb
---
# Availability database is suspended
    
## Introduction  
  
|||  
|-|-|  
|**Policy Name**|Availability Database Suspension State|  
|**Issue**|Availability database is suspended.|  
|**Category**|**Warning**|  
|**Facet**|Availability database|  
  
## Description  
 This policy checks the state of data movement of the secondary database \(also known as a "secondary database replica"\). The policy is in an unhealthy state when the data movement is suspended. The policy is otherwise in a healthy state.  
  
> [!NOTE]  
>  For this release of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], information about possible causes and solutions is located at [Availability database is suspended](http://go.microsoft.com/fwlink/p/?LinkId=220860) on the TechNet Wiki.  
  
## Possible Causes  
 Data synchronization on this availability database might have been suspended because of the following:  
  
-   Due to an error, the system might have suspended data synchronization.  
  
-   The database administrator might have suspended data synchronization for maintenance purposes.  
  
## Possible Solution  
 Resume data synchronization. If the issue persists, check the availability group in the Event log, and then diagnose why the system suspended data movement.  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Use the Always On Dashboard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always%20On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)  
  
  