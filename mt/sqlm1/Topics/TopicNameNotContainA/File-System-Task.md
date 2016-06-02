---
title: File System Task
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7dd79a6a-e066-4028-a385-1d40f31056f8
---
# File System Task
  The File System task performs operations on files and directories in the file system. For example, by using the File System task, a package can create, move, or delete directories and files. You can also use the File System task to set attributes on files and directories. For example, the File System task can make files hidden or read\-only.  
  
 All File System task operations use a source, which can be a file or a directory. For example, the file that the task copies or the directory it deletes is a source. The source can be specified by using a File connection manager that points to the directory or file or by providing the name of a variable that contains the source path. For more information, see [File Connection Manager](../../Topics\TopicNameNotContainA/File-Connection-Manager.md) and [Integration Services &#40;SSIS&#41; Variables](../Topic/Integration%20Services%20\(SSIS\)%20Variables.md).  
  
 The operations that copy and move file and directories and rename files use a destination and a source. The destination is specified by using a File connection manager or a variable. File system task operations can be configured to permit overwriting of destination files and directories. The operation that creates a new directory can be configured to use an existing directory that has the specified name instead of failing when the directory already exists.  
  
## Predefined File System Operations  
 The File System task includes a predefined set of operations. The following table describes these operations.  
  
|Operation|Description|  
|---------------|-----------------|  
|Copy directory|Copies a folder from one location to another.|  
|Copy file|Copies a file from one location to another.|  
|Create directory|Creates a folder in a specified location.|  
|Delete directory|Deletes a folder in a specified location.|  
|Delete directory content|Deletes all files and folders in a folder.|  
|Delete file|Deletes a file in a specified location.|  
|Move directory|Moves a folder from one location to another.|  
|Move file|Moves a file from one location to another.|  
|Rename file|Renames a file in a specified location.|  
|Set attributes|Sets attributes on files and folders. Attributes include Archive, Hidden, Normal, ReadOnly, and System. Normal is the lack of attributes, and it cannot be combined with other attributes. All other attributes can be used in combination.|  
  
 The File System task operates on a single file or directory. Therefore, this task does not support the use of wildcard characters to perform the same operation on multiple files. To have the File System task repeat an operation on multiple files or directories, put the File System task in a Foreach Loop container, as described in the following steps:  
  
-   **Configure the Foreach Loop container** On the **Collection** page of the Foreach Loop Editor, set the enumerator to **Foreach File Enumerator** and enter the wildcard expression as the enumerator configuration for **Files**. On the **Variable Mappings** page of the Foreach Loop Editor, map a variable that you want to use to pass the file names one at a time to the File System task.  
  
-   **Add and configure a File System task** Add a File System task to the Foreach Loop container. On the **General** page of the File System Task Editor, set the **SourceVariable** or **DestinationVariable** property to the variable that you defined in the Foreach Loop container.  
  
## Custom Log Entries Available on the File System Task  
 The following table describes the custom log entry for the File System task. For more information, see [Integration Services &#40;SSIS&#41; Logging](../Topic/Integration%20Services%20\(SSIS\)%20Logging.md) and [Custom Messages for Logging](../../Topics\TopicNameNotContainA/Custom-Messages-for-Logging.md).  
  
|Log entry|Description|  
|---------------|-----------------|  
|**FileSystemOperation**|Reports the operation that the task performs. The log entry is written when the file system operation starts and includes information about the source and destination.|  
  
## Configuring the File System Task  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, see the following topics:  
  
-   [File System Task Editor &#40;General Page&#41;](../Topic/File%20System%20Task%20Editor%20\(General%20Page\).md)  
  
-   [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)  
  
 For more information about how to set these properties in [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer, see the following topic:  
  
-   [Set the Properties of a Task or Container](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Task-or-Container.md)  
  
 For more information about how to set these properties programmatically, see the following topic:  
  
-   [FileSystemTask](assetId:///T:Microsoft.SqlServer.Dts.Tasks.FileSystemTask.FileSystemTask)  
  
## Related Tasks  
 [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes a task that downloads and uploads data files and manages directories on servers. For more information, see [FTP Task](../../Topics\TopicNameNotContainA/FTP-Task.md).  
  
## See Also  
 [Integration Services Tasks](../../Topics\TopicNameNotContainA/Integration-Services-Tasks.md)   
 [Control Flow](../../Topics\TopicNameNotContainA/Control-Flow.md)  
  
  