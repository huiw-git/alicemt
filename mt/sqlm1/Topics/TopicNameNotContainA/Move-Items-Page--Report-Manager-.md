---
title: Move Items Page (Report Manager)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc83b8d2-bc79-4b56-8970-34a1cbbcc176
robots: noindex,nofollow
---
# Move Items Page (Report Manager)
  Use the Move Items page to move a report, folder, or other item to a new location on the report server. You can type the path of the new location or use a tree view to browse to a new location in the report server namespace. You can only move items that you have permission to move and that are stored on the current report server.  
  
 When you move an item that is referenced by another item \(for example, a shared data source or model that is referenced by many reports\), the path information for that item is updated automatically. Moving a shared data source does not disrupt a data source connection to the reports and models that use it. If you move a shared data source or model to a folder for which users do not have permission, they will still be able to run any report that references the data source or model, however the item will not be visible to them in the folder hierarchy.  
  
 For **Location**, specify the full path to folder, beginning with the root folder name. You can type the path name or use the tree view to navigate to the folder you want.  
  
> [!NOTE]  
>  Not all items are movable. You cannot move reserved folders such as Home, My Reports, or Users Folders. You cannot move report history or snapshots to different locations. History and snapshots are always located with, and accessed through, the report on which they are based.  
  
## Navigation  
 Use the following procedures to navigate to this location in the user interface \(UI\).  
  
###### To open the Move Items page from the Contents page in Details View  
  
1.  Open Report Manager, and navigate to the folder that contains an item you want to move. You can also move items from the Report Manager Home page.  
  
2.  In the toolbar, click **Details View**.  
  
    > [!NOTE]  
    >  If you see only **Tiles View**, you are already in **Details View**.  
  
3.  Select the box next to an item, and then click **Move** in the toolbar. You can select more than one box if you want to move multiple items to the same new location.  
  
###### To open the Move Items page from the Contents page in Tiles View  
  
1.  Open Report Manager, and navigate to the folder that contains an item you want to move. You can also move items from the Report Manager Home page.  
  
2.  In the toolbar, click **Tiles View**.  
  
    > [!NOTE]  
    >  If you see only **Details View**, you are already in **Tiles View**.  
  
3.  Hover over an item, and click the drop\-down arrow.  
  
4.  In the drop\-down menu, click **Move**.  
  
###### To open the Move Items page from the General Properties page of an item  
  
1.  Open Report Manager, and navigate to the folder that contains an item you want to move. You can also move items from the Report Manager Home page.  
  
2.  Hover over an item, and click the drop\-down arrow.  
  
3.  In the drop\-down menu, click **Manage**. This opens the General properties page for an item.  
  
4.  In the item toolbar, click **Move**.  
  
## See Also  
 [Report Manager  &#40;SSRS Native Mode&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)   
 [General Properties Page, Folders &#40;Report Manager&#41;](../Topic/General%20Properties%20Page,%20Folders%20\(Report%20Manager\).md)   
 [General Properties Page, Reports &#40;Report Manager&#41;](../Topic/General%20Properties%20Page,%20Reports%20\(Report%20Manager\).md)   
 [General Properties Page, Resources &#40;Report Manager&#41;](../Topic/General%20Properties%20Page,%20Resources%20\(Report%20Manager\).md)   
 [General Properties Page, Shared Data Sources &#40;Report Manager&#41;](../Topic/General%20Properties%20Page,%20Shared%20Data%20Sources%20\(Report%20Manager\).md)   
 [Report Manager F1 Help](../../Topics\TopicNameNotContainA/Report-Manager-F1-Help.md)  
  
  