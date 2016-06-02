---
title: Restore Database Dialog Box (Analysis Services - Multidimensional Data)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a3990d47-55e2-424e-8eac-87edc937e806
---
# Restore Database Dialog Box (Analysis Services - Multidimensional Data)
  Use the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] to restore an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database from a backup file using the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Backup File \(.abf\) format.  
  
> [!IMPORTANT]  
>  For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file. To restore an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance. To overwrite an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance, or a member of a database role with Full Control \(Administrator\) permissions on the database to be restored.  
  
> [!NOTE]  
>  After restoring an existing database, the user who restored the database might lose access to the restored database. This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control \(Administrator\) permissions.  
  
 **To display the Restore Database dialog box**  
  
-   In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], right\-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance or a database in **Object Explorer**, and then click **Restore**.  
  
 The **Restore Database** dialog box contains the following pages.  
  
## Pages  
 **General**  
 Use this page to select the database to restore, the backup file from which to restore the database, as well as the general options and password to use while restoring the database. For more information about this page, see [General &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/General%20\(Restore%20Database%20Dialog%20Box\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md).  
  
 **Partitions**  
 Use this page to restore local partitions to specified locations, and to restore remote partitions from remote backup files. For more information about this page, see [Partitions &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Partitions%20\(Restore%20Database%20Dialog%20Box\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md).  
  
## See Also  
 [Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](../Topic/Analysis%20Services%20Designers%20and%20Dialog%20Boxes%20\(Multidimensional%20Data\).md)   
 [Backup and Restore of Analysis Services Databases](../../Topics\TopicNameNotContainA/Backup-and-Restore-of-Analysis-Services-Databases.md)  
  
  