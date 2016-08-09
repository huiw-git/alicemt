---
title: "Restore Options"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75c73802-f321-4671-afc7-54505d62c013
caps.latest.revision: 24
caps.handback.revision: 0
manager: mblythe
---
# Restore Options
There are many ways to restore your [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] databases, all of which require that you have administrator permissions for both the server computer and the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database. To restore an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database, you can open the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], select the appropriate options configuration and then run the restore from the dialog box. Or, you can create a script using the settings already specified in the file; the script can then be saved and run as often as needed. In this way, the restore is completed by using XMLA, as described in the next section.  
  
## Restoring Databases Using XMLA  
 The XMLA Restore command is a way to automate the restore process by running a restore based on an .abf file. The Restore command has a number of properties that can be set to specify security definitions, where remote partitions should be stored, and the relocation of relational OLAP (ROLAP) objects. For more information, see [Backing Up, Restoring, and Synchronizing Databases (XMLA)](assetId:///bb5a0c92-3927-4fa4-975b-6e4d79e0a912).  
  
> [!IMPORTANT]  
>  For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file. To restore an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] instance. To overwrite an [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] instance, or a member of a database role with Full Control (Administrator) permissions on the database to be restored.  
  
> [!NOTE]  
>  After restoring an existing database, the user who restored the database might lose access to the restored database. This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control (Administrator) permissions.  
  
## See Also  
 [Restore Database Dialog Box (Analysis Services - Multidimensional Data)](../../Topics/TopicNameNotContainA/Restore-Database-Dialog-Box--Analysis-Services---Multidimensional-Data-.md)   
 [Backup and Restore of Analysis Services Databases](../../Topics/TopicNameNotContainA/Backup-and-Restore-of-Analysis-Services-Databases.md)   
 [Restore Element (XMLA)](assetId:///bb5a0c92-3927-4fa4-975b-6e4d79e0a912)   
 [Backing Up, Restoring, and Synchronizing Databases (XMLA)](assetId:///6c021b2e-6ad0-444e-b23f-4b5f72ce084b)