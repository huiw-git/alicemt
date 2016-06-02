---
title: Package Management (SSIS Service)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0261ed9e-3b01-4e37-a9d4-d039c41029b6
---
# Package Management (SSIS Service)
  Management of packages involves tasks including the following tasks:  
  
-   Monitoring running packages  
  
-   Managing package storage  
  
-   Importing and exporting packages  
  
> [!IMPORTANT]  
>  This topic discusses the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages. [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]. Starting in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], you can manage objects such as packages on the Integration Services server.  
  
## Package Store  
 [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] provides two top\-level folders for accessing [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages: **Running Packages** and **Stored Packages**. The **Running Packages** folder lists the packages that are currently running on the server. The **Stored Packages** folder lists the packages that are saved in the package store. These are the only packages that the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service manages. The package store can consist of either or both the msdb database and file system folders listed in the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service configuration file. The configuration file specifies the msdb and file system folders to manage. You might also have packages stored elsewhere in the file system that are not managed by the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service.  
  
 Packages that you save to msdb are stored in a table named sysssispackages. When you save packages to msdb, you can also group them in logical folders. The use of logical folders can help you organize packages by purpose, or filter packages in the sysssispackages table. You can create new logical folders by using [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]. By default, any logical folders that you add to msdb are automatically included in the package store.  
  
 The logical folders that you create for grouping packages in msdb are represented as rows in the sysssispackagefolders table in msdb. The folderid and parentfolderid columns in sysssispackagefolders define the folder hierarchy. The root logical folders in msdb are the rows in sysssispackagefolders that have null values in the parentfolderid column. For more information, see [sysssispackages &#40;Transact-SQL&#41;](../Topic/sysssispackages%20\(Transact-SQL\).md) and [sysssispackagefolders &#40;Transact-SQL&#41;](../Topic/sysssispackagefolders%20\(Transact-SQL\).md).  
  
 When you open [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and connect to [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)], you will see the msdb folders that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service manages listed within the Stored Packages folder. If the configuration file specifies root file system folders, the Stored Packages folder also lists packages saved to the file system in those folders and in all subfolders.  
  
 You can store packages in any file system folder, but they will not be listed in subfolders of the **Stored Packages** folder unless you add the folder to the list of folders in the configuration file for the package store. For more information about the configuration file, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](../Topic/Configuring%20the%20Integration%20Services%20Service%20\(SSIS%20Service\).md).  
  
 The **Running Packages** folder contains no subfolders and it is not extensible.  
  
 By default, the **Stored Packages** folder contains two folders: **File System** and **MSDB**. The **File System** folder lists the packages that are saved to the file system. The location of these files is specified in the configuration file for the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service. The default folder is the Packages folder, located in %Program Files%\\Microsoft SQL Server\\100\\DTS. The **MSDB** folder lists the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages that have been saved to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] msdb database on the server. The sysssispackages table contains the packages saved to msdb.  
  
 To view the list of packages in the package store, you must open [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and connect to [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]. For more information, see [View Integration Services Packages in SQL Server Management Studio &#40;SSIS Service&#41;](../Topic/View%20Integration%20Services%20Packages%20in%20SQL%20Server%20Management%20Studio%20\(SSIS%20Service\).md).  
  
## Monitoring Running Packages  
 The **Running Packages** folder lists the packages that are currently running. To view information about current packages on the **Summary** page of [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], click the **Running Packages** folder. Information such as the execution duration of running packages is listed on the **Summary** page. Optionally, refresh the folder to display the most current information.  
  
 To view information about a single running package on the **Summary** page, click the package. The **Summary** page displays information such as the version and description of the package.  
  
 You can stop a running package from the **Running Packages** folder by right\-clicking the package and then clicking **Stop**.  
  
## Managing Package Storage  
 To organize packages, you can add custom folders to the root package store folders that the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service lists in its configuration file. By default, the root folders are the **File System** and **MSDB** folders. For example, you might want to add to the **File System** folder a **Data Cleaning** folder that contains all the packages used for cleaning data. You can add custom folders to custom folders, creating a nested folder hierarchy to suit your needs. The custom folders can be deleted and renamed; however, you cannot rename or delete the root folders that the configuration file specifies. To update the root folders that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] lists, you must update the configuration file.  
  
 For more information, see [Configuring the Integration Services Service &#40;SSIS Service&#41;](../Topic/Configuring%20the%20Integration%20Services%20Service%20\(SSIS%20Service\).md).  
  
## Importing and Exporting Packages  
 [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages can be saved to either to the msdb database or to the file system. You can copy a package from one storage type to the other by using the import or export feature that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] provides. You can also import a package to the same storage type and give the package a different name, to create a copy of a package. The **dtutil** command prompt utility \(dtutil.exe\) can also be used to import and export packages.  
  
 For more information, see [dtutil Utility](../../Topics\TopicNameNotContainA/dtutil-Utility.md).  
  
## Related Tasks  
  
-   [Import and Export Packages &#40;SSIS Service&#41;](../Topic/Import%20and%20Export%20Packages%20\(SSIS%20Service\).md)  
  
-   [View Integration Services Packages in SQL Server Management Studio &#40;SSIS Service&#41;](../Topic/View%20Integration%20Services%20Packages%20in%20SQL%20Server%20Management%20Studio%20\(SSIS%20Service\).md)  
  
## See Also  
 [Integration Services Service &#40;SSIS Service&#41;](../Topic/Integration%20Services%20Service%20\(SSIS%20Service\).md)  
  
  