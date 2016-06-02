---
title: Troubleshoot a Failed Add-File Operation (Always On Availability Groups)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-high-availability
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 31ceaebf-864b-4dd0-9112-0d047b0316ad
---
# Troubleshoot a Failed Add-File Operation (Always On Availability Groups)
  In some Always On availability group deployments, file paths differ between the system that hosts the primary replica and systems that host a secondary replica. If the file path of an add\-file operation does not exist on a secondary replica, the add\-file operation will succeed on the primary database. But the add\-file operation will cause the secondary database to be suspended. This, in turn, causes the secondary replica to enter the NOT SYNCHRONIZING state.  
  
> [!NOTE]  
>  We recommend that, if possible, the file path \(including the drive letter\) of a given secondary database be identical to the path of the corresponding primary database.  
  
## Problem Resolution  
 To resolve this problem the database owner must complete the following steps:  
  
1.  Remove the secondary database from the availability group. For more information, see [Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;](../Topic/Remove%20a%20Secondary%20Database%20from%20an%20Availability%20Group%20\(SQL%20Server\).md).  
  
2.  On the existing secondary database, restore a full backup of the filegroup that contains the added file to the secondary database, using WITH NORECOVERY and WITH MOVE \(specifying the file path on the server instance that hosts the secondary replica\). For more information, see [Restore a Database to a New Location &#40;SQL Server&#41;](../Topic/Restore%20a%20Database%20to%20a%20New%20Location%20\(SQL%20Server\).md).  
  
3.  Back up the transaction log that contains the add\-file operation on the primary database, and manually restore the log backup on the secondary database using WITH NORECOVERY and WITH MOVE.  
  
4.  Prepare the secondary database for re\-joining the availability group, by restoring, WITH NO RECOVERY, any other outstanding log backups from the primary database.  
  
5.  Rejoin the secondary database to the availability group. For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](../Topic/Join%20a%20Secondary%20Database%20to%20an%20Availability%20Group%20\(SQL%20Server\).md).  
  
## See Also  
 [Overview of Always On Availability Groups &#40;SQL Server&#41;](../Topic/Overview%20of%20Always%20On%20Availability%20Groups%20\(SQL%20Server\).md)   
 [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](../Topic/Manually%20Prepare%20a%20Secondary%20Database%20for%20an%20Availability%20Group%20\(SQL%20Server\).md)   
 [Troubleshoot Orphaned Users &#40;SQL Server&#41;](../Topic/Troubleshoot%20Orphaned%20Users%20\(SQL%20Server\).md)   
 [Troubleshoot Always On Availability Groups Configuration &#40;SQL Server&#41;](../Topic/Troubleshoot%20Always%20On%20Availability%20Groups%20Configuration%20\(SQL%20Server\).md)