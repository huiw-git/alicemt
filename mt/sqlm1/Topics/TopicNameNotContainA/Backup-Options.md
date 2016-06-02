---
title: Backup Options
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
ms.assetid: 02d33fc9-f3f4-4b85-8b90-449b68625cf7
---
# Backup Options
  There are many ways to back up your [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] databases and they all require that you have server administrator and database administrator permissions. You can open the **Backup** dialog box in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], select the appropriate options configuration, and then run the backup from the dialog box itself. Or, you can create a script using the settings already specified in the file; the script can then be saved and run as frequently as required.  
  
## Backup and Synchronize  
 If the database is located on a remote instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], you can use the synchronization feature to back up the database to the local instance. Development builds of a database can be moved into production in this manner. You can also use the conventional, file based, backup and restore to move the development build into production, but synchronization provides additional functionality. For example, you can have security settings which are different for the development and production computers; synchronization will provide you the option to maintain those settings and synchronize all objects other than roles. Also, synchronization typically does an incremental update of those objects which are different for the source and destination computers. This kind of incremental backup is not available using the backup\/restore feature. For more information, see [Synchronize Analysis Services Databases](../../Topics\TopicNameNotContainA/Synchronize-Analysis-Services-Databases.md).  
  
> [!IMPORTANT]  
>  The Analysis Services service account must have permission to write to the backup location specified for each file. Also, the user must have one of the following roles: administrator role on the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance, or a member of a database role with Full Control \(Administrator\) permissions on the database to be backed up.  
  
## See Also  
 [Backup Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Backup%20Database%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Backup and Restore of Analysis Services Databases](../../Topics\TopicNameNotContainA/Backup-and-Restore-of-Analysis-Services-Databases.md)   
 [Backup Element &#40;XMLA&#41;](../Topic/Backup%20Element%20\(XMLA\).md)   
 [Backing Up, Restoring, and Synchronizing Databases &#40;XMLA&#41;](../Topic/Backing%20Up,%20Restoring,%20and%20Synchronizing%20Databases%20\(XMLA\).md)  
  
  