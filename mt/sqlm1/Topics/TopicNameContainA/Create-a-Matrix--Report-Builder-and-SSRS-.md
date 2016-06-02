---
title: Create a Matrix (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 493e63b9-ecd0-4054-97ec-92d84e9b8182
---
# Create a Matrix (Report Builder and SSRS)
  Use a matrix to display grouped data and summary information. You can group data by multiple fields or expressions in row and column groups. Matrices provide functionality similar to crosstabs and pivot tables. At run time, as the report data and data regions are combined, a matrix grows horizontally and vertically on the page. Values in matrix cells display aggregate values scoped to the intersection of the row and column groups to which the cell belongs. You can format the rows and columns to highlight the data you want to emphasize. You can also include drilldown toggles that initially hide detail data; the user can then click the toggles to display more or less detail as needed.  
  
 After your initial design, you can continue to develop a matrix to improve the viewing experience for the user. For more information, see [Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;](../Topic/Controlling%20the%20Tablix%20Data%20Region%20Display%20on%20a%20Report%20Page%20\(Report%20Builder%20and%20SSRS\).md).  
  
 To quickly get started with matrices, see [Tutorial: Creating a Matrix Report &#40;Report Builder&#41;](../Topic/Tutorial:%20Creating%20a%20Matrix%20Report%20\(Report%20Builder\).md).  
  
> [!NOTE]  
>  You can publish lists separately from a report as report parts. Read more about [Report Parts (Report Builder and SSRS)](Report%20Parts%20\(Report%20Builder%20and%20SSRS\).md).  
  
##  <a name="AddingMatrix"></a> Adding a Matrix to Your Report  
 Add a matrix to the design surface from the Insert tab on the ribbon. You have the option to add a matrix by using the Table or Matrix Wizard, which includes creating a data source connection and dataset, and configuring the matrix or adding a matrix based on the matrix template.  
  
> [!NOTE]  
>  The wizard is available only in [!INCLUDE[ssRBDenali](../../Token\Other/ssRBDenali_md.md)].  
  
 To describe how to configure a table from beginning to end, this topic uses the matrix template.  The matrix initially has a row group, a column group, a corner cell, and a data cell, as shown in the following figure.  
  
 ![Blank Matrix with 1 row and 1 column group](../../Images\Image\ImageNotContaina/rs_MatrixTemplateNew.gif "rs_MatrixTemplateNew")  
  
 When you select a matrix on the design surface, row and column handles appear, as shown in the following figure.  
  
 ![New Matrix added from Toolbox, selected](../../Images\Image\ImageNotContaina/rs_MatrixTemplateNewSelected.gif "rs_MatrixTemplateNewSelected")  
  
 Add groups by dragging dataset fields to the Row Groups and Column Groups areas of the Grouping pane. The first field that you drag to the row groups or column groups pane replaces the initial empty default group. You can then apply formatting for each cell, depending on the data.  
  
 ![Matrix, Category row and Geography column group](../../Images\Image\ImageNotContaina/rs_BasicMatrixDesign.gif "rs_BasicMatrixDesign")  
  
 In Preview, the matrix expands to show the row group and column group values. The cells display summary values, as shown in the following figure.  
  
 ![Preview for rendered matrix with expanded groups](../../Images\Image\ImageNotContaina/rs_BasicMatrixPreview.gif "rs_BasicMatrixPreview")  
  
 The matrix you start with is a template based on the tablix data region. You can continue to develop your matrix design by adding nested or adjacent row groups or column groups, or even adding detail rows. For more information, see [Exploring the Flexibility of a Tablix Data Region &#40;Report Builder and SSRS&#41;](../Topic/Exploring%20the%20Flexibility%20of%20a%20Tablix%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="AddingParentGroupChild"></a> Adding a Parent Group or Child Group to a Matrix  
 To add a group based on a single dataset field, drag the field from the Report Data pane to the appropriate Row Groups or Column Groups area of the Grouping pane. Drop the field in the group hierarchy to set its relationship to existing groups. Drop it above an existing group to create a parent group, or drop it below an existing group to create a child group.  
  
 Several things happen when you drop a field in the **Grouping** pane:  
  
-   A new group with a unique name based on the field name is automatically created. The group expression is set to the simple field name reference, for example `[Category]`.  
  
-   A new row or column appears in the corresponding row group or column group area.  
  
-   In the new column, a row group cell appears for the default data rows from the report dataset. Cells in the tablix body for this row are now members of the row group. If there are any column groups defined, cells that are in the columns are members of those column groups. Group indicators provide visual cues for the group membership of each cell.  
  
 To customize the group after it is created, use the **Tablix Group** dialog box. You can change the group name, and edit or add additional expressions to the group definition. To add or remove rows from the table, see [Insert or Delete a Row &#40;Report Builder and SSRS&#41;](../Topic/Insert%20or%20Delete%20a%20Row%20\(Report%20Builder%20and%20SSRS\).md).  
  
 When the report runs, dynamic column headers expand right \(or left, if the Direction property of the matrix is set to RTL\) for as many columns as there are unique group values. Dynamic rows expand down the page. The data that appears in the tablix body cells are aggregates based on the intersections of row and column groups, as shown in the following figure.  
  
 ![Matrix, nested row and column groups with totals](../../Images\Image\ImageNotContaina/rs_BasicMatrixNestedGroupsTotalsDesign.gif "rs_BasicMatrixNestedGroupsTotalsDesign")  
  
 In preview, the report displays as in the following figure.  
  
 ![Nested Groups in Preview](../../Images\Image\ImageNotContaina/rs_BasicMatrixNestedGroupsTotalsPreview.gif "rs_BasicMatrixNestedGroupsTotalsPreview")  
  
 To write expressions that specify a scope other than the default scope, you must specify the name of a dataset, data region, or group in the aggregate function all. To calculate the percentage each subcategory contributes to the Clothing category group values, add a column inside the Category group next to the Total column, format the text box to show percentage, and add an expression that uses the default scope in the numerator, and the Category group scope in the denominator, as shown in the following example.  
  
 `=SUM(Fields!Linetotal.Value)/SUM(Fields! Linetotal.Value,"Category")`  
  
 For more information, see [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Scope%20for%20Totals,%20Aggregates,%20and%20Built-in%20Collections%20\(Report%20Builder%20and%20SSRS\).md).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
##  <a name="AddingAdjacentGroup"></a> Adding an Adjacent Group to a Matrix  
 To add an adjacent group based on a single dataset field, use the shortcut menu in the Grouping pane. For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](../Topic/Add%20or%20Delete%20a%20Group%20in%20a%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md). The following figure shows a group based on geography and an adjacent group based on year.  
  
 ![Adjacent Column Groups for Geography and Year](../../Images\Image\ImageNotContaina/rs_BasicMatrixAdjacentGroupsDesign.gif "rs_BasicMatrixAdjacentGroupsDesign")  
  
 In this example, the query has filtered data values to only include those values for Europe and for the years 2003 and 2004. However, you can set filters on each group independently. In preview, the report displays as in the following figure.  
  
 ![Preview of adjacent column groups](../../Images\Image\ImageNotContaina/rs_BasicMatrixAdjacentGroupsPreview.gif "rs_BasicMatrixAdjacentGroupsPreview")  
  
 To add a total column for an adjacent column group, click in the column group definition cell and use the **Add Total** command. A new static column is added next to the column group, with a default aggregate sum for every numeric field in the existing rows. To change the expression, manually edit the default aggregate, for example, `Avg([Sales])`. For more information, see [Add a Total to a Group or Tablix Data Region &#40;Report Builder and SSRS&#41;](../Topic/Add%20a%20Total%20to%20a%20Group%20or%20Tablix%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md).  
  
 ![Arrow icon used with Back to Top link](../../Images\Image\ImageNotContaina/UpArrow16x16.gif "UpArrow16x16") [Back to Top](#BackToTop)  
  
## See Also  
 [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](../Topic/Aggregate%20Functions%20Reference%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Examples &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Examples%20\(Report%20Builder%20and%20SSRS\).md)  
  
  