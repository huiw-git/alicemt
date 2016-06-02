---
title: Transfer Database Task Editor (Databases Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ccdb74d0-4bea-420c-a726-2e0eb8957e0a
---
# Transfer Database Task Editor (Databases Page)
  Use the **Databases** page of the **Transfer Database Task Editor** dialog box to specify properties for the source and destination databases involved in the Transfer Database task. The Transfer Database task copies or moves a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database between two instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. This task can also be used to copy a database within the same server. For more information about this task, see [Transfer Database Task](../../Topics\TopicNameNotContainA/Transfer-Database-Task.md).  
  
## Options  
 **SourceConnection**  
 Select a SMO connection manager in the list, or click **\<New connection...\>** to create a new connection to the source server.  
  
 **DestinationConnection**  
 Select a SMO connection manager in the list, or click **\<New connection...\>** to create a new connection to the destination server.  
  
 **DestinationDatabaseName**  
 Specify the name of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database on the destination server.  
  
 To automatically populate this field with the source database name, specify the **SourceConnection** and **SourceDatabaseName** first.  
  
 To rename the database on the destination server, type the new name in this field.  
  
 **DestinationDatabaseFiles**  
 Specifies the names and locations of the database files on the destination server.  
  
 To automatically populate this field with the source database file names and locations, specify the **SourceConnection**, **SourceDatabaseName**, and **SourceDatabaseFiles** first.  
  
 To rename the database files or to specify the new locations on the destination server, populate this field with the source database information, and then click the browse button. In the **Destination database files** dialog box, edit the **Destination File**, **Destination Folder**, or **Network File Share**.  
  
> [!NOTE]  
>  If you locate the database files by using the browse button, the file location is entered using the local drive notation: for example, c:\\. You must replace this with the network share notation, including the computer name and share name. If the default administrative share is used, you must use the $ notation, and have administrative access to the share.  
  
 **DestinationOverwrite**  
 Specify whether the database on the destination server can be overwritten.  
  
 This property has the options listed in the following table:  
  
|Value|Description|  
|-----------|-----------------|  
|**True**|Overwrite destination server database.|  
|**False**|Do not overwrite destination server database.|  
  
> [!CAUTION]  
>  The data in the destination server database will be overwritten if you specify **True** for **DestinationOverwrite**, which may result in data loss. To avoid this, back up the destination server database to another location before executing the Transfer Database task.  
  
 **Action**  
 Specify whether the task will **Copy** or **Move** the database to the destination server.  
  
 **Method**  
 Specify whether the task will be executed while the database on the source server is in online or offline mode.  
  
 To transfer a database using offline mode, the user that runs the package must be a member of the **sysadmin** fixed server role.  
  
 To transfer a database using the online mode, the user that runs the package must be a member of the **sysadmin** fixed server role, or the database owner \(**dbo**\) of the selected database.  
  
 **SourceDatabaseName**  
 Select the name of the database to be copied or moved.  
  
 **SourceDatabaseFiles**  
 Click the browse button to select the database files.  
  
 **ReattachSourceDatabase**  
 Specify whether the task will attempt to reattach the source database if a failure occurs.  
  
 This property has the options listed in the following table:  
  
|Value|Description|  
|-----------|-----------------|  
|**True**|Reattach source database.|  
|**False**|Do not reattach source database.|  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Integration Services Tasks](../../Topics\TopicNameNotContainA/Integration-Services-Tasks.md)   
 [Transfer Database Task Editor &#40;General Page&#41;](../Topic/Transfer%20Database%20Task%20Editor%20\(General%20Page\).md)   
 [Expressions Page](../../Topics\TopicNameNotContainA/Expressions-Page.md)   
 [SMO Connection Manager](../../Topics\TopicNameNotContainA/SMO-Connection-Manager.md)  
  
  