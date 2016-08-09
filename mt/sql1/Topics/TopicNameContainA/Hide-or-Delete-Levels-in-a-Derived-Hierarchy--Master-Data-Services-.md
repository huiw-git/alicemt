---
title: "Hide or Delete Levels in a Derived Hierarchy (Master Data Services)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
caps.latest.revision: 7
caps.handback.revision: 0
manager: jhubbard
---
# Hide or Delete Levels in a Derived Hierarchy (Master Data Services)
In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)], hide a level in a derived hierarchy when you require the level for grouping but you do not need to show the level. Delete a level when you do not want to use it for grouping.  
  
## Prerequisites  
 To perform this procedure:  
  
-   You must have permission to access the **System Administration** functional area.  
  
-   You must be a model administrator. For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
### To hide or delete levels in a derived hierarchy  
  
1.  In [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)], click **System Administration**.  
  
2.  From the menu bar, point to **Manage** and click **Derived Hierarchies**.  
  
3.  On the **Derived Hierarchy Maintenance** page, from the **Model** list, select a model.  
  
4.  Select the row for the derived hierarchy you want to edit.  
  
5.  Click **Edit**.  
  
6.  In the **Current Levels** pane:  
  
    -   To hide a level, click a level other than the top or bottom. From the **Visible** list, select **No**. Then click **Save selected hierarchy item**.  
  
    -   To delete the top level, click **Delete selected hierarchy item**. In the confirmation dialog box, click **OK**. You can delete the top level only.  
  
## See Also  
 [How to: Move Members in a Hierarchy (Master Data Services)](assetId:///049c9a15-89c1-478c-8438-028fffc9e187)   
 [Derived Hierarchies (Master Data Services)](../../Topics/TopicNameNotContainA/Derived-Hierarchies--Master-Data-Services-.md)