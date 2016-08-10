---
title: "Change an Item Within a Cell (Report Builder and SSRS)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91a54778-8929-41f9-bb4c-826cec636be4
caps.latest.revision: 8
caps.handback.revision: 0
manager: mblythe
---
# Change an Item Within a Cell (Report Builder and SSRS)
Only a non-container item, such as a text box, line, or image, can be replaced by a new report item. For example, you can drag a table into a text box to replace the text box with a table.  
  
 If the cell contains a container item such as a rectangle, list, table, or matrix, the new item is added to the containing item instead of replacing it. To replace a container item with a new item, delete the container. Deleting the container item replaces it with a text box, which you can then replace with another item.  
  
 By default, all cells in a table, matrix, or list data region contain a text box.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Topics/TopicNameContainA/tokens/ssRBRDDup_md.md)]  
  
### To change an item within a cell  
  
-   On the **Insert** tab, in the **Data Regions** or **Report Items** group, click the item that you want to add to the report, and then click the report. The item is added to the report.  
  
> [!NOTE]  
>  The **Image Properties** dialog box opens when you drag an image report item to a cell, where you can set properties such as the source of the image before the image is added to the cell.  
  
## See Also  
 [Images, Text Boxes, Rectangles, and Lines (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Images--Text-Boxes--Rectangles--and-Lines--Report-Builder-and-SSRS-.md)   
 [Tables, Matrices, and Lists (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Tables--Matrices--and-Lists--Report-Builder-and-SSRS-.md)