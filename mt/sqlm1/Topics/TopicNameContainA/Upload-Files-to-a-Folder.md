---
title: Upload Files to a Folder
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2f99a288-d4aa-4c64-b310-e457a2aef2c5
---
# Upload Files to a Folder
  You can upload files from the file system and store them as managed items in a report server database. What happens when you upload a file depends on the file type.  
  
-   Uploading an .rdl file is equivalent to publishing a report.  
  
-   Uploading any other file adds it to the report server database as a single binary object. These files are published to a report server as a resource. Resources can be any file type. If the file extension matches a known MIME type, an icon for that MIME type is used to identify the resource type. Otherwise, a generic file icon indicates a resource.  
  
> [!NOTE]  
>  You cannot upload a report data source \(.rds\) file to create a shared data source. An .rds file is used only in Report Designer. It cannot provide the content for a shared data source item that you define and manage through Report Manager. As an alternative to uploading, you can write a script that creates a shared data source based on a .rds file.  
  
 The maximum file size for uploaded items is determined by [!INCLUDE[vstecasp](../../Token\Other/vstecasp_md.md)]. By default, the maximum size is 4 megabytes \(MB\).  
  
 Visually, files that you upload to a report server database are represented in the folder hierarchy with the following icons.  
  
 ![Report icon](../../Images\Image\ImageNotContaina/hlp_16doc.gif "hlp_16doc")  
report icon  
  
 ![Model icon](../../Images\Image\ImageNotContaina/model_icon.gif "model_icon")  
report model icon  
  
 ![generic resource icon](../../Images\Image\ImageNotContaina/hlp_16file.gif "hlp_16file")  
generic resource icon  
  
 When you upload a file, it is always placed in the folder that is currently selected. You can navigate to the folder that you want to contain the item first, or you can upload a file and then move it to a final location later.  
  
 To upload a file, use Report Manager. Whether you can upload files to a report server depends on tasks that are part of your role assignment. If you are using default security, local administrators can add items to a report server. If My Reports is enabled, any user who has a My Reports folder has permission to upload items to that folder. If you use custom role assignments, the role assignment must include tasks that support folder management.  
  
|To do this|Include these tasks|  
|----------------|-------------------------|  
|Upload an .rdl file to a folder|Manage reports|  
|Upload any file as a binary object|Manage resources|  
|View the contents of a folder|View resources, View reports|  
  
## See Also  
 [Report Manager  &#40;SSRS Native Mode&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)   
 [Granting Permissions on a Native Mode Report Server](../../Topics\TopicNameContainA/Granting-Permissions-on-a-Native-Mode-Report-Server.md)   
 [Tasks and Permissions](../../Topics\TopicNameNotContainA/Tasks-and-Permissions.md)   
 [Upload a File or Report &#40;Report Manager&#41;](../Topic/Upload%20a%20File%20or%20Report%20\(Report%20Manager\).md)  
  
  