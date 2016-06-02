---
title: General Properties Page, Report Parts (Report Manager)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 93ddce72-31f1-42f7-abd5-8191acbb00c5
robots: noindex,nofollow
---
# General Properties Page, Report Parts (Report Manager)
  Use the Properties page to view and manage the general properties for a report part.  
  
 From Report Manager, you cannot view or change the appearance and functionality of the report part. To change the design, you must use an authoring tool to open and modify the design and publish it back to the server.  
  
## Navigation  
 Use the following procedure to navigate to this location in the user interface \(UI\).  
  
###### To open the properties page for a report part  
  
1.  Open Report Manager, and locate the report part for which you want to configure properties.  
  
2.  Hover over the report part, and click the drop\-down arrow.  
  
3.  In the drop\-down list, click **Manage**. The General properties page opens.  
  
## Options  
 **Modified Date**  
 The date and time the report part properties were last modified on the server or a new version of the report part was published to the server. Read\-only.  
  
 **Modified By**  
 The name of the user who last modified the report part. Read\-only.  
  
 **Creation Date**  
 The date and time the report part was originally published to the server. Read\-only.  
  
 **Created By**  
 The name of the user who originally created the report part. Read\-only.  
  
 **Size**  
 The file size of the report part. Read\-only.  
  
 **Name**  
 Type a name to identify the report part.  
  
 **Description**  
 Provide information about the report part. The description appears on the Contents page of Report Manager. The description text can be searched when a user is searching for report parts from a report authoring tool.  
  
 **Hide in list view**  
 Select to hide the report part from users who are using list view mode in Report Manager. List view mode is the default view format when you browse the report server folder hierarchy. Although you can hide an item in list view, you cannot hide an item in details view. If you want to restrict access to an item, you must create a role assignment.  
  
 **Type**  
 The type of report part. Read\-only.  
  
 **Apply**  
 Save your changes.  
  
 **Delete**  
 Remove the report part from the report server database. Deleting a report part from the server will not prevent the rendering of existing reports which the report part was added to.  
  
 **Move**  
 Click to open the Move Items page to move a report part within the report server folder hierarchy. For more information, see [Move Items Page &#40;Report Manager&#41;](../Topic/Move%20Items%20Page%20\(Report%20Manager\).md).  
  
 **Download**  
 Extract a copy of the report part definition to be saved as a .rsc file. The .rsc file can be uploaded to a report server folder or used to replace an existing report part in a report server folder.  
  
 **Replace**  
 Replace the report part definition with a different one from an .rsc file.  
  
## See Also  
 [Managing Report Parts](../../Topics\TopicNameNotContainA/Managing-Report-Parts.md)   
 [Report Manager  &#40;SSRS Native Mode&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)   
 [Contents Page &#40;Report Manager&#41;](../Topic/Contents%20Page%20\(Report%20Manager\).md)   
 [Report Parts &#40;Report Builder and SSRS&#41;](../Topic/Report%20Parts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Report Manager F1 Help](../../Topics\TopicNameNotContainA/Report-Manager-F1-Help.md)   
 [Report Parts and Datasets in Report Builder](../../Topics\TopicNameNotContainA/Report-Parts-and-Datasets-in-Report-Builder.md)  
  
  