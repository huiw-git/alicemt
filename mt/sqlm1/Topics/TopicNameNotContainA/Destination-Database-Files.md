---
title: Destination Database Files
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f6f90417-86fb-4b8c-a790-0b215c344ef6
---
# Destination Database Files
  Use the **Destination Database Files** dialog box to view or change the database file names and locations on the destination server, or to specify a network file location for the Transfer Database task. For more information about this task, see [Transfer Database Task](../../Topics\TopicNameNotContainA/Transfer-Database-Task.md).  
  
 To automatically populate this dialog box with the database file names and locations on the source server, specify the **SourceConnection**, **SourceDatabaseName**, and **SourceDatabaseFiles** first in the **Databases** page of the **Transfer Database Task Editor** dialog box.  
  
## Options  
 **Destination File**  
 Names of the transferred database files on the destination server.  
  
 Enter the file name, or click the file name to edit it.  
  
 **Destination Folder**  
 Folder on the destination server where the database files will be transferred to.  
  
 Enter the folder path, click the folder path to edit it, or click browse to locate the folder where you want to transfer the database files on the destination server.  
  
 **Network File Share**  
 Network shared folder on the destination server where the database files will be transferred to. Use **Network file share** when you transfer a database in offline mode by specifying **DatabaseOffline** for **Method** in the **Databases** page of the **Transfer Database Task Editor** dialog box.  
  
 Enter the network file share location, or click browse to locate the network file share location.  
  
 When you transfer a database in offline mode, the database files are copied to the **Network file share** location before they are transferred to the **Destination folder** location.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Transfer Database Task Editor &#40;General Page&#41;](../Topic/Transfer%20Database%20Task%20Editor%20\(General%20Page\).md)   
 [Transfer Database Task Editor &#40;Databases Page&#41;](../Topic/Transfer%20Database%20Task%20Editor%20\(Databases%20Page\).md)  
  
  