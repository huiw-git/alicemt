---
title: Change Row Height or Column Width (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f061c204-5cd5-4467-9a9c-8a12803d93ba
---
# Change Row Height or Column Width (Report Builder and SSRS)
  When you set a row height, you are specifying the maximum height for the row in the rendered report. However, by default, text boxes in the row are set to grow vertically to accommodate their data at run\-time, and this can cause a row to expand beyond the height that you specify. To set a fixed row height, you must change the text box properties so they do not automatically expand.  
  
 When you set a column width, you are specifying the maximum width for the column in the rendered report. Columns do not automatically adjust horizontally to accommodate text.  
  
 If a cell in a row or column contains a rectangle or data region, the minimum height and width of the cell is determined by the height and width of the contained item. For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../Topic/Rendering%20Behaviors%20\(Report%20Builder%20%20and%20SSRS\).md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
### To change row height by moving row handles  
  
1.  In Design view, click anywhere in the tablix data region to select it. Gray row handles appear on the outside border of the tablix data region.  
  
2.  Hover over the row handle edge that you want to expand. A double\-headed arrow appears.  
  
3.  Click to grab the edge of the row and move it higher or lower to adjust the row height.  
  
### To change row height by setting cell properties  
  
1.  In Design view, click a cell in the table row.  
  
     ![Selected Cell in a Table](../../Images\Image\ImageContaina/Table_SelectCell.png "Table_SelectCell")  
  
2.  In the **Properties** pane that displays, modify the **Height** property, and then click anywhere outside the **Properties** pane.  
  
     ![Properties Pane for selected table cell](../../Images\Image\ImageNotContaina/Cell_PropertiesPane.png "Cell_PropertiesPane")  
  
### To prevent a row from automatically expanding vertically  
  
1.  In Design view, click anywhere in the tablix data region to select it. Gray row handles appear on the outside border of the tablix data region.  
  
2.  Click the row handle to select the row.  
  
3.  In the Properties pane, set CanGrow to **False**.  
  
    > [!NOTE]  
    >  If you cannot see the Properties pane, from the **View** menu, click **Properties**.  
  
### To change column width  
  
1.  In Design view, click anywhere in the tablix data region to select it. Gray column handles appear on the outside border of the tablix data region.  
  
2.  Hover over the column handle edge that you want to expand. A double\-headed arrow appears.  
  
3.  Click to grab the edge of the column and move it left or right to adjust the column width.  
  
## See Also  
 [Tablix Data Region &#40;Report Builder and SSRS&#41;](../Topic/Tablix%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](../Topic/Tablix%20Data%20Region%20Cells,%20Rows,%20and%20Columns%20\(Report%20Builder\)%20and%20SSRS.md)   
 [Tables &#40;Report Builder  and SSRS&#41;](../Topic/Tables%20\(Report%20Builder%20%20and%20SSRS\).md)   
 [Matrices &#40;Report Builder and SSRS&#41;](../Topic/Matrices%20\(Report%20Builder%20and%20SSRS\).md)   
 [Lists &#40;Report Builder and SSRS&#41;](../Topic/Lists%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../Topic/Tables,%20Matrices,%20and%20Lists%20\(Report%20Builder%20and%20SSRS\).md)  
  
  