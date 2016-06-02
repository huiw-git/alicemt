---
title: Browse for Report Parts and Set a Default Folder (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5cf38068-65d1-4fe8-81f3-a404d8fbc663
---
# Browse for Report Parts and Set a Default Folder (Report Builder and SSRS)
  The easiest way to create a report is to add existing report parts, such as tables and charts, to your report from the Report Part Gallery. When you add a report part to your report, you are also adding everything it must have to work. For example, any report part that displays data depends on a dataset, that is, a query and a connection to a data source. After you add the report part to your report, you can modify it as much as you need.  
  
 You can set a default folder to publish report parts to the report server or SharePoint site integrated with a report server.  
  
 For more information, see [Report Parts &#40;Report Builder and SSRS&#41;](../Topic/Report%20Parts%20\(Report%20Builder%20and%20SSRS\).md).  
  
### To browse for report parts  
  
1.  On the **Insert** menu, click **Report Parts**.  
  
     If you are not already connected, click **Connect to a report server**, and enter the name.  
  
    > [!NOTE]  
    >  You must be connected to a report server to browse for report parts.  
  
2.  You can narrow your search by specifying details about the report part. Type all or part of the name and description in the **Search** box, or click **Add Criteria** and add values for any or all of these fields:  
  
    -   Created by  
  
    -   Date created  
  
    -   Date last modified  
  
    -   Last modified by  
  
    -   Server folder  
  
    -   Type  
  
     For example, to find an image, click **Add Criteria**, and then click **Type**. In the dropdown box, select the **Image** check box, press ENTER, and then click the Search magnifying glass.  
  
    > [!NOTE]  
    >  For the **Created by** and **Last modified by** values, search for the person's user name as it is represented on the report server.  
  
### To set a default folder for report parts  
  
1.  Click **Report Builder**, and then click **Options**.  
  
2.  In the **Options** dialog box, on the **Settings** tab, type a folder name in the **Publish report parts to this folder by default** textbox.  
  
 Report Builder will create this folder if you have permissions to create folders on the report server and the folder does not exist yet.  
  
 You do not need to restart Report Builder for this setting to take effect.  
  
## See Also  
 [Check for Updates or Turn Updates Off \(Report Builder and SSRS\)](assetId:///9c69792d-d7c4-453b-ae2f-6d2d071d8606)   
 [Report Parts &#40;Report Builder and SSRS&#41;](../Topic/Report%20Parts%20\(Report%20Builder%20and%20SSRS\).md)   
 [Report Parts and Datasets in Report Builder](../../Topics\TopicNameNotContainA/Report-Parts-and-Datasets-in-Report-Builder.md)   
 [Troubleshoot Report Parts \(Report Builder and SSRS\)](assetId:///d9fe1932-46e7-421b-a8a9-4c54d9576e94)   
 [Publish and Republish Report Parts &#40;Report Builder and SSRS&#41;](../Topic/Publish%20and%20Republish%20Report%20Parts%20\(Report%20Builder%20and%20SSRS\).md)  
  
  