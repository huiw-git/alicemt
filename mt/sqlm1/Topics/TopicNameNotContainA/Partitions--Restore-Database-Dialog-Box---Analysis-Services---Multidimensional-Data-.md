---
title: Partitions (Restore Database Dialog Box) (Analysis Services - Multidimensional Data)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1ad4dde5-4651-4069-875c-7ab73cd8b4f4
---
# Partitions (Restore Database Dialog Box) (Analysis Services - Multidimensional Data)
  Use the **Partitions** page of the **Restore Database** dialog box in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] to specify the location to restore local partitions, and to specify whether to restore remote partitions and the remote backup files to use when restoring remote partitions.  
  
> [!IMPORTANT]  
>  For each backup file, the user who runs the restore command must have permission to read from the backup location specified for each file. To restore an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database that is not installed on the server, the user must also be a member of the server role for that [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance. To overwrite an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database, the user must have one of the following roles: a member of the server role for the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance, or a member of a database role with Full Control \(Administrator\) permissions on the database to be restored.  
  
> [!NOTE]  
>  After restoring an existing database, the user who restored the database might lose access to the restored database. This loss of access can occur if, at the time that the backup was performed, the user was not a member of the server role or was not a member of the database role with Full Control \(Administrator\) permissions.  
  
 **To display the Paritions page in the Restore Database dialog box**  
  
-   In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], right\-click either the **Databases** folder of an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance or a database in **Object Explorer**, click **Restore**, and then under **Select a page**, click **Partitions**.  
  
## Options  
 **Script**  
 Creates a restore script that is based on the options selected in the dialog box. The restore script is written in the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] Scripting Language \(ASSL\).  
  
 Clicking the **Script** icon sends the restore script into a new query window, by default.  
  
 Clicking the **Script** arrow displays a menu that allows you to choose where to send the restore script:  
  
-   To a new query window \(default\).  
  
-   To a file.  
  
-   To the clipboard.  
  
-   To a job.  
  
 **Restore to original locations**  
 Select to restore local partitions contained in the backup file to their original locations.  
  
 **Select different locations**  
 Select to specify different locations in which to restore local partitions.  
  
> [!NOTE]  
>  You can only change the restoration folder of a local partition if a location other than the default location was specified for that partition in the cube.  
  
 The following grid, enabled when this option is selected, is used to specify a restoration folder for each local partition:  
  
|Column|Description|  
|------------|-----------------|  
|**Cube**|Displays the name of the cube that contains the local partition.|  
|**MeasureGroup**|Displays the name of the measure group that contains the local partition.|  
|**Partition**|Displays the name of the local partition.|  
|**Size \(MB\)**|Displays the size, in megabytes, of the local partition.|  
|**Original Folder**|Displays the name of the original folder in which the local partition was stored.|  
|**Restoration Folder**|Type the name of the restoration folder for the local partition, or click the ellipsis button \(**...**\) to display the **Browse for Remote Folder** dialog box and select the path of the folder to use. For more information about the **Browse for Remote Folder** dialog box, see [Browse for Remote Folder Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Browse%20for%20Remote%20Folder%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md).|  
  
 **Restore remote partitions**  
 Select to restore remote partitions stored in remote backup files.  
  
> [!NOTE]  
>  This option is enabled only if the backup file contains references to remote partitions.  
  
 The following grid, enabled when this option is selected, is used to specify a restoration folder for each local partition:  
  
|Column|Description|  
|------------|-----------------|  
|**Server**|Displays the name of the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance that manages the remote partition.|  
|**Data Source**|Displays the name of the data source in the backup file that represents the database that contains the remote partition.|  
|**Backup File**|Type the full path and file name of the remote backup file to use, or click the ellipsis button \(**...**\) to display the **Locate Database Files** dialog box and select the path and file name of the remote backup file to use. For more information about the **Locate Database Files** dialog box, see [Locate Database Files Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Locate%20Database%20Files%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md).|  
|**...**|Click to display the **Remote Partitions \- Advanced Settings** dialog box and modify advanced options, such as the connection string for the data source, for restoring the remote partition. For more information about the **Remote Partitions \- Advanced Settings** dialog box, see [Remote Partitions - Advanced Settings Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Remote%20Partitions%20-%20Advanced%20Settings%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md).|  
  
## See Also  
 [Restore Database Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Restore%20Database%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [General &#40;Restore Database Dialog Box&#41; &#40;Analysis Services - Multidimensional Data&#41;](../Topic/General%20\(Restore%20Database%20Dialog%20Box\)%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Backup and Restore of Analysis Services Databases](../../Topics\TopicNameNotContainA/Backup-and-Restore-of-Analysis-Services-Databases.md)  
  
  