---
title: "Change Row Height or Column Width (Report Builder and SSRS)"
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
ms.assetid: f061c204-5cd5-4467-9a9c-8a12803d93ba
caps.latest.revision: 9
caps.handback.revision: 0
manager: mblythe
---
# Change Row Height or Column Width (Report Builder and SSRS)
When you set a row height, you are specifying the maximum height for the row in the rendered report. However, by default, text boxes in the row are set to grow vertically to accommodate their data at run-time, and this can cause a row to expand beyond the height that you specify. To set a fixed row height, you must change the text box properties so they do not automatically expand.  
  
 When you set a column width, you are specifying the maximum width for the column in the rendered report. Columns do not automatically adjust horizontally to accommodate text.  
  
 If a cell in a row or column contains a rectangle or data region, the minimum height and width of the cell is determined by the height and width of the contained item. For more information, see [Rendering Behaviors (Report Builder  and SSRS)](../../Topics/TopicNameNotContainA/Rendering-Behaviors--Report-Builder--and-SSRS-.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Topics/TopicNameContainA/tokens/ssRBRDDup_md.md)]  
  
### To change row height by moving row handles  
  
1.  In Design view, click anywhere in the tablix data region to select it. Gray row handles appear on the outside border of the tablix data region.  
  
2.  Hover over the row handle edge that you want to expand. A double-headed arrow appears.  
  
3.  Click to grab the edge of the row and move it higher or lower to adjust the row height.  
  
### To change row height by setting cell properties  
  
1.  In Design view, click a cell in the table row.  
  
     ![Selected Cell in a Table](../../Topics/TopicNameNotContainA/images/Table_SelectCell.png "Table_SelectCell")  
  
2.  In the **Properties** pane that displays, modify the **Height** property, and then click anywhere outside the **Properties** pane.  
  
     ![Properties Pane for selected table cell](../../Topics/TopicNameNotContainA/images/Cell_PropertiesPane.png "Cell_PropertiesPane")  
  
### To prevent a row from automatically expanding vertically  
  
1.  In Design view, click anywhere in the tablix data region to select it. Gray row handles appear on the outside border of the tablix data region.  
  
2.  Click the row handle to select the row.  
  
3.  In the Properties pane, set **CanGrow** to **False**.  
  
    > [!NOTE]  
    >  If you cannot see the Properties pane, from the **View** menu, click **Properties**.  
  
### To change column width  
  
1.  In Design view, click anywhere in the tablix data region to select it. Gray column handles appear on the outside border of the tablix data region.  
  
2.  Hover over the column handle edge that you want to expand. A double-headed arrow appears.  
  
3.  Click to grab the edge of the column and move it left or right to adjust the column width.  
  
## See Also  
 [Tablix Data Region (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Tablix-Data-Region--Report-Builder-and-SSRS-.md)   
 [Tablix Data Region Cells, Rows, and Columns (Report Builder) and SSRS](../../Topics/TopicNameNotContainA/Tablix-Data-Region-Cells--Rows--and-Columns--Report-Builder--and-SSRS.md)   
 [Tables (Report Builder  and SSRS)](../../Topics/TopicNameNotContainA/Tables--Report-Builder--and-SSRS-.md)   
 [Create a Matrix (Report Builder and SSRS)](../../Topics/TopicNameContainA/Create-a-Matrix--Report-Builder-and-SSRS-.md)   
 [Create Invoices and Forms with Lists (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Create-Invoices-and-Forms-with-Lists--Report-Builder-and-SSRS-.md)   
 [Tables, Matrices, and Lists (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Tables--Matrices--and-Lists--Report-Builder-and-SSRS-.md)