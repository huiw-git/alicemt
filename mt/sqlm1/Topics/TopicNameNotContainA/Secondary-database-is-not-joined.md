---
title: Secondary database is not joined
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 10817e5e-75fa-42dd-baa2-359bea3ad051
---
# Secondary database is not joined
    
## Introduction  
  
|||  
|-|-|  
|**Policy Name**|Availability Database Join State|  
|**Issue**|Secondary database is not joined.|  
|**Category**|**Warning**|  
|**Facet**|Availability database|  
  
## Description  
 This policy checks the join state of the secondary database \(also known as a "secondary database replica"\). The policy is in an unhealthy state when the dataset replica is not joined. The policy is otherwise in a healthy state.  
  
> [!NOTE]  
>  For this release of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], information about possible causes and solutions is located at [Secondary database is not joined](http://go.microsoft.com/fwlink/p/?LinkId=220862) on the TechNet Wiki.  
  
## Possible Causes  
 This secondary database is not joined to the availability group. The configuration of this secondary database is incomplete.  
  
## Possible Solution  
 Use Transact\-SQL, PowerShell, or SQL Server Management Studio to join the secondary replica to the availability group. For more information about joining secondary replicas to availability groups, see [Joining a Secondary Replica to an Availability Group \(SQL Server\)](http://msdn.microsoft.com/library/ff878473\(SQL.110\).aspx).  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Use the Always On Dashboard &#40;SQL Server Management Studio&#41;](../Topic/Use%20the%20Always%20On%20Dashboard%20\(SQL%20Server%20Management%20Studio\).md)  
  
  