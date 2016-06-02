---
title: Restore Options
ms.custom: na
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
---
# Restore Options
  There are many ways to restore your [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] databases, all of which require that you have administrator permissions for both the server computer and the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database. To restore an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database, you can open the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], select the appropriate options configuration and then run the restore from the dialog box. Or, you can create a script using the settings already specified in the file; the script can then be saved and run as often as needed. In this way, the restore is completed by using XMLA, as described in the next section.  
  
## Restoring Databases Using XMLA  
 The XMLA Restore command is a way to automate the restore process by running a restore based on an .abf file. The Restore command has a number of properties that can be set to specify security definitions, where remote partitions should be stored, and the relocation of relational OLAP \(ROLAP\) objects. For more information, see [Restore Element &#40;XMLA&#41;](../Topic/Restore%20Element%20\(XMLA\).md).  
  
> [!IMPORTANT]  
>  For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file. To restore an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance. To overwrite an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance, or a member of a database role with Full Control \(Administrator\) permissions on the database to be restored.  
  
> [!NOTE]  
>  After restoring an existing database, the user who restored the database might lose access to the restored database. This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control \(Administrator\) permissions.  
  
## See Also  
 [Restore Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Restore%20Database%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Backup and Restore of Analysis Services Databases](../../Topics\TopicNameNotContainA/Backup-and-Restore-of-Analysis-Services-Databases.md)   
 [Restore Element &#40;XMLA&#41;](../Topic/Restore%20Element%20\(XMLA\).md)   
 [Backing Up, Restoring, and Synchronizing Databases &#40;XMLA&#41;](../Topic/Backing%20Up,%20Restoring,%20and%20Synchronizing%20Databases%20\(XMLA\).md)  
  
  