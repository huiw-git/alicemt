---
title: Import and Export Packages (SSIS Service)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef18ec11-b536-47d9-abd1-794099f43486
---
# Import and Export Packages (SSIS Service)
    
> [!IMPORTANT]  
>  This topic discusses the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service, a Windows service for managing [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] packages. [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] supports the service for backward compatibility with earlier releases of [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]. Starting in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], you can manage objects such as packages on the Integration Services server.  
  
 Packages can be saved either in the sysssispackages table in the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] msdb database or in the file system.  
  
 The package store, which is the logical storage that [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service monitors and manages, can include both the msdb database and the file system folders specified in the configuration file for the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service.  
  
 You can import and export packages between the following storage types:  
  
-   File system folders anywhere in the file system.  
  
-   Folders in the SSIS Package Store. The two default folders are named File System and MSDB.  
  
-   The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] msdb database.  
  
 [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] gives you the ability to import and export packages, and by doing this change the storage format and location of packages. Using the import and export features, you can add packages to the file system, package store, or msdb database, and copy packages from one storage format to another. For example, packages saved in msdb can be copied to the file system and vice versa.  
  
 You can also copy a package to a different format using the **dtutil** command prompt utility \(dtutil.exe\). For more information, see [dtutil Utility](../../Topics\TopicNameNotContainA/dtutil-Utility.md).  
  
## To import or export a package  
  
> [!IMPORTANT]  
>  This topic discusses the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service that is part of [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]. [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] supports the [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] service for backward compatibility with [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]. For information about managing packages in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], see [Integration Services &#40;SSIS&#41; Server](../Topic/Integration%20Services%20\(SSIS\)%20Server.md).  
  
 You can import or export an [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package from or to the following locations:  
  
-   You can import a package that is stored in an instance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], in the file system, or in the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] package store. The imported package is saved to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or to a folder in the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] package store.  
  
-   You can export a package that is stored in an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], the file system, or the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Store to a different storage format and location.  
  
 However, there are some restrictions on importing and exporting a package between different versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]:  
  
-   On an instance of [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], you can import packages from an instance of [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], but you cannot export packages to an instance of [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)].  
  
-   On an instance of [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], you cannot import packages from, or export packages to, an instance of [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)].  
  
 The following procedures describe how to use [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] to import or export a package.  
  
#### To import a package by Using SQL Server Management Studio  
  
1.  Click **Start**, point to **Microsoft** [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], and then click **SQL Server Management Studio**.  
  
2.  In the **Connect to Server** dialog box set the following options:  
  
    -   In the **Server type** box, select **Integration Services**.  
  
    -   In the **Server name** box, provide a server name or click **\<Browse for more…\>** and locate the server to use.  
  
3.  If Object Explorer is not open, on the **View** menu, click **Object Explorer**.  
  
4.  In Object Explorer, expand the **Stored Packages** folder.  
  
5.  Expand the subfolders to locate the folder into which you want to import a package.  
  
6.  Right\-click the folder, click **Import Package**. and then do one of the following:  
  
    -   To import from an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], select the **SQL Server** option, and then specify the server and select the authentication mode. If you select [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, provide a user name and a password.  
  
         Click the browse button **\(…\)**, select the package to import, and then click **OK.**  
  
    -   To import from the file system, select the **File system** option.  
  
         Click the browse button **\(…\)**, select the package to import, and then click **Open.**  
  
    -   To import from the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Package Store, select the **SSIS Package Store** option and specify the server.  
  
         Click the browse button **\(…\)**, select the package to import, and then click **OK.**  
  
7.  Optionally, update the package name.  
  
8.  To update the protection level of the package, click the browse button **\(…\)** and choose a different protection level by using the **Package Protection Level** dialog box. If the **Encrypt sensitive data with password** or the **Encrypt all data with password** option is selected, type and confirm a password.  
  
9. Click **OK** to complete the import.  
  
#### To export a package by Using SQL Server Management Studio  
  
1.  Click **Start**, point to **Microsoft** [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], and then click **SQL Server Management Studio**.  
  
2.  In the **Connect to Server** dialog box, set the following options:  
  
    -   In the **Server type** box, select **Integration Services**.  
  
    -   In the **Server name** box, provide a server name or click **\<Browse for more…\>** and locate the server to use.  
  
3.  If Object Explorer is not open, on the **View** menu, click **Object Explorer**.  
  
4.  In Object Explorer, expand the **Stored Packages** folder.  
  
5.  Expand the subfolders to locate the package you want to export.  
  
6.  Right\-click the package, click **Export**, and then do one of the following:  
  
    -   To export to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], select the **SQL Server** option, and then specify the server and select the authentication mode. If you select [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, provide a user name and a password.  
  
         Click the browse button **\(…\)**, and expand the **SSIS Packages** folder to locate the folder to which you want to save the package. Optionally, update the default name of the package, and then click **OK**.  
  
    -   To export to the file system, select the **File System** option.  
  
         Click the browse button **\(…\)** to locate the folder to which you want to export the package, type the name of the package file, and then click **Save.**  
  
    -   To export to the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] package store, select the **SSIS Package Store** option, and specify the server.  
  
         Click the browse button **\(…\)**, expand the **SSIS Packages** folder, and select the folder to which you want to save the package. Optionally, enter a new name for the package in the **Package Name** text box. [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
7.  To update the protection level of the package, click the browse button **\(…\)** and choose a different protection level by using the **Package Protection Level** dialog box. If the **Encrypt sensitive data with password** or the **Encrypt all data with password** option is selected, type and confirm a password.  
  
8.  Click **OK** to complete the export.  
  
## See Also  
 [Package Management &#40;SSIS Service&#41;](../Topic/Package%20Management%20\(SSIS%20Service\).md)  
  
  