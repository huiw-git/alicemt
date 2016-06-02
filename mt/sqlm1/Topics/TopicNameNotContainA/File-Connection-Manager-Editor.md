---
title: File Connection Manager Editor
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 051c48e5-3d86-49af-b554-ff62e3de3622
---
# File Connection Manager Editor
  Use the **File Connection Manager Editor** dialog box to specify the properties used to connect to a file or a folder.  
  
> [!NOTE]  
>  You can set the ConnectionString property for the File connection manager by specifying an expression in the Properties window of [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. However, to avoid a validation error when you use an expression to specify the file or folder, in the **File Connection Manager Editor**, for **File\/Folder**, add a file or folder path.  
  
 To learn more about the File connection manager, see [File Connection Manager](../../Topics\TopicNameNotContainA/File-Connection-Manager.md).  
  
## Options  
 **Usage Type**  
 Specify whether the **File Connection Manager** connects to an existing file or folder or creates a new file or folder.  
  
|Value|Description|  
|-----------|-----------------|  
|Create file|Create a new file at run time.|  
|Existing file|Use an existing file.|  
|Create folder|Create a new folder at run time.|  
|Existing folder|Use an existing folder.|  
  
 **File \/ Folder**  
 If **File**, specify the file to use.  
  
 If **Folder**, specify the folder to use.  
  
 **Browse**  
 Select the file or folder by using the **Select File** or **Browse for Folder** dialog box.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)  
  
  