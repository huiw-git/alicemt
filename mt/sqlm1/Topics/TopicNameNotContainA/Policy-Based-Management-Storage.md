---
title: Policy-Based Management Storage
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d0cbf214-fc2e-4917-8d31-1d71c9ffa61d
---
# Policy-Based Management Storage
  Policies are stored in the msdb database. After a policy or condition is changed, msdb should be backed up. For more information, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](../Topic/Back%20Up%20and%20Restore%20of%20System%20Databases%20\(SQL%20Server\).md).  
  
## Storing Policies  
 [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] includes policies that can be used to monitor an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. By default, these policies are not installed on the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]; however, they can be imported from the default installation location of C:\\Program Files\\Microsoft SQL Server\\130\\Tools\\Policies\\DatabaseEngine\\1033.  
  
 You can directly create policies by using the **File\/New** menu, and then saving them to a file. This enables you to create policies when you are not connected to an instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)].  
  
 Policy history for policies evaluated in the current instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] is maintained in msdb system tables. Policy history for policies applied to other instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] or applied to [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] or [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] is not retained.  
  
  