---
title: File Connection Manager
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 019078bc-44ee-4975-9169-0f9a89e3f3be
---
# File Connection Manager
  A File connection manager enables a package to reference an existing file or folder, or to create a file or folder at run time. For example, you can reference an Excel file. Certain components in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] use information in files to perform their work. For example, an Execute SQL task can reference a file that contains the SQL statements that the task executes. Other components perform operations on files. For example, the File System task can reference a file to copy it to a new location.  
  
## Usage Types of the File Connection Manager  
 The **FileUsageType** property of the File connection manager specifies how the file connection is used. The File connection manager can create a file, create a folder, use an existing file, or use an existing folder.  
  
 The following table lists the values of **FileUsageType**.  
  
|Value|Description|  
|-----------|-----------------|  
|**0**|File connection manager uses an existing file.|  
|**1**|File connection manager creates a file.|  
|**2**|File connection manager uses an existing folder.|  
|**3**|File connection manager creates a folder.|  
  
## Multiple File or Folder Connections  
 The File connection manager can reference only one file or folder. To reference multiple files or folders, use a Multiple Files connection manager instead of a File connection manager. For more information, see [Multiple Files Connection Manager](../../Topics\TopicNameNotContainA/Multiple-Files-Connection-Manager.md).  
  
## Configuration of the File Connection Manager  
 When you add a File connection manager to a package, [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] creates a connection manager that will resolve to a File connection at run time, sets the File connection properties, and adds the File connection to the **Connections** collection of the package.  
  
 The **ConnectionManagerType** property of the connection manager is set to **FILE**.  
  
 You can configure a File connection manager in the following ways:  
  
-   Specify the usage type.  
  
-   Specify a file or folder.  
  
 You can set the ConnectionString property for the File connection manager by specifying an expression in the Properties window of [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. However, to avoid a validation error when you use an expression to specify the file or folder, in the **File Connection Manager Editor**, for **File\/Folder**, add a file or folder path.  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, see [File Connection Manager Editor](../../Topics\TopicNameNotContainA/File-Connection-Manager-Editor.md).  
  
 For information about configuring a connection manager programmatically, see [ConnectionManager](assetId:///T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager) and [Adding Connections Programmatically](../Topic/Adding%20Connections%20Programmatically.md).  
  
  