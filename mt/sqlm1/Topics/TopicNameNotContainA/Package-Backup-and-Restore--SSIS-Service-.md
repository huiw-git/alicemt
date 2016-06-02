---
title: Package Backup and Restore (SSIS Service)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c67d3b83-a6c8-40de-920f-9236de4ac87f
---
# Package Backup and Restore (SSIS Service)
    
> [!IMPORTANT]  
>  This topic discusses the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages. [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]. Starting in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], you can manage objects such as packages on the Integration Services server.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages can be saved to the file system or msdb, a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] system database. Packages saved to msdb can be backed up and restored using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] backup and restore features.  
  
 For more information about backing up and restoring the msdb database, click one of the following topics:  
  
-   [Back Up and Restore of SQL Server Databases](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-of-SQL-Server-Databases.md)  
  
-   [Back Up and Restore of System Databases &#40;SQL Server&#41;](../Topic/Back%20Up%20and%20Restore%20of%20System%20Databases%20\(SQL%20Server\).md)  
  
 [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes the **dtutil** command\-prompt utility \(dtutil.exec\), which you can use to manage packages. For more information, see [dtutil Utility](../../Topics\TopicNameNotContainA/dtutil-Utility.md).  
  
## Configuration Files  
 Any configuration files that the packages include are stored in the file system. These files are not backed up when you back up the msdb database; therefore, you should make sure that the configuration files are backed up regularly as part of your plan for securing packages saved to msdb. To include configurations in the backup of the msdb database, you should consider using the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] configuration type instead of file\-based configurations.  
  
## Packages Stored in the File System  
 The backup of packages that are saved to the file system should be included in the plan for backing up the file system of the server. The [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service configuration file, which has the default name MsDtsSrvr.ini.xml, lists the folders on the server that the service monitors. You should make sure these folders are backed up. Additionally, packages may be stored in other folders on the server and you should make sure to include these folders in the backup.  
  
  