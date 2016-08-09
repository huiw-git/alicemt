---
title: "Add a Details Group (Report Builder and SSRS)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5ef8efba-6d48-4aeb-a3b9-a02ba5a44614
caps.latest.revision: 8
caps.handback.revision: 0
manager: mblythe
---
# Add a Details Group (Report Builder and SSRS)
The detail data from a report dataset is specified as a group with no group expression. Add a detail group to an existing tablix data region when you want to display the detail data for a matrix, add back detail data that you have deleted from a table or list, or to add additional detail groups. For more information about groups, see [Understanding Groups (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Understanding-Groups--Report-Builder-and-SSRS-.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Topics/TopicNameContainA/tokens/ssRBRDDup_md.md)]  
  
### To add a details group to a tablix data region  
  
1.  On the design surface, click anywhere in a tablix data region to select it. The Grouping pane displays the row and column groups for the selected data region.  
  
2.  In the Grouping pane, right-click a group that is an innermost child group. Click **Add Group**, and then click **Child Group**. The **Tablix Group** dialog box opens.  
  
3.  In **Group expression**, leave the expression blank. A details group has no expression.  
  
4.  Select **Show detail data**.  
  
5.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/tokens/clickOK_md.md)]  
  
     A new details group is added as a child group in the Grouping pane, and the row handle for the group you selected in step 1 displays the details group icon. For more information about handles, see [Tablix Data Region Cells, Rows, and Columns (Report Builder) and SSRS](../../Topics/TopicNameNotContainA/Tablix-Data-Region-Cells--Rows--and-Columns--Report-Builder--and-SSRS.md).  
  
## See Also  
 [Add or Delete a Group in a Data Region (Report Builder and SSRS)](../../Topics/TopicNameContainA/Add-or-Delete-a-Group-in-a-Data-Region--Report-Builder-and-SSRS-.md)   
 [Understanding Groups (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Understanding-Groups--Report-Builder-and-SSRS-.md)   
 [Tablix Data Region (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Tablix-Data-Region--Report-Builder-and-SSRS-.md)   
 [Tables (Report Builder  and SSRS)](../../Topics/TopicNameNotContainA/Tables--Report-Builder--and-SSRS-.md)   
 [Create a Matrix (Report Builder and SSRS)](../../Topics/TopicNameContainA/Create-a-Matrix--Report-Builder-and-SSRS-.md)   
 [Create Invoices and Forms with Lists (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Create-Invoices-and-Forms-with-Lists--Report-Builder-and-SSRS-.md)   
 [Tables, Matrices, and Lists (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Tables--Matrices--and-Lists--Report-Builder-and-SSRS-.md)