---
title: Add a Details Group (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5ef8efba-6d48-4aeb-a3b9-a02ba5a44614
---
# Add a Details Group (Report Builder and SSRS)
  The detail data from a report dataset is specified as a group with no group expression. Add a detail group to an existing tablix data region when you want to display the detail data for a matrix, add back detail data that you have deleted from a table or list, or to add additional detail groups. For more information about groups, see [Understanding Groups &#40;Report Builder and SSRS&#41;](../Topic/Understanding%20Groups%20\(Report%20Builder%20and%20SSRS\).md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
### To add a details group to a tablix data region  
  
1.  On the design surface, click anywhere in a tablix data region to select it. The Grouping pane displays the row and column groups for the selected data region.  
  
2.  In the Grouping pane, right\-click a group that is an innermost child group. Click **Add Group**, and then click **Child Group**. The **Tablix Group** dialog box opens.  
  
3.  In **Group expression**, leave the expression blank. A details group has no expression.  
  
4.  Select **Show detail data**.  
  
5.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
     A new details group is added as a child group in the Grouping pane, and the row handle for the group you selected in step 1 displays the details group icon. For more information about handles, see [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](../Topic/Tablix%20Data%20Region%20Cells,%20Rows,%20and%20Columns%20\(Report%20Builder\)%20and%20SSRS.md).  
  
## See Also  
 [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](../Topic/Add%20or%20Delete%20a%20Group%20in%20a%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md)   
 [Understanding Groups &#40;Report Builder and SSRS&#41;](../Topic/Understanding%20Groups%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tablix Data Region &#40;Report Builder and SSRS&#41;](../Topic/Tablix%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tables &#40;Report Builder  and SSRS&#41;](../Topic/Tables%20\(Report%20Builder%20%20and%20SSRS\).md)   
 [Matrices &#40;Report Builder and SSRS&#41;](../Topic/Matrices%20\(Report%20Builder%20and%20SSRS\).md)   
 [Lists &#40;Report Builder and SSRS&#41;](../Topic/Lists%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../Topic/Tables,%20Matrices,%20and%20Lists%20\(Report%20Builder%20and%20SSRS\).md)  
  
  