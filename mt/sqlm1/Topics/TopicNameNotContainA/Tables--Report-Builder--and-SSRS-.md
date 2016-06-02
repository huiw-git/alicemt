---
title: Tables (Report Builder  and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0a95c339-c5aa-49ad-b1c8-72824b7a9c82
---
# Tables (Report Builder  and SSRS)
 In [!INCLUDE[ssRSnoversion_md](../../Token\Other/ssRSnoversion_md.md)], you can use a table to display detail data or grouped data, or a combination of both in a paginated report.   
   
 You can group data by a single field, by multiple fields, or by writing your own expression. You can create nested groups or independent, adjacent groups. To display aggregated values for grouped data, add totals to groups. Format the rows and columns to highlight the data you want to emphasize. You can initially hide detail or grouped data, and include drilldown toggles to enable a user to interactively choose how much data to show.  
  
 To quickly get started with tables, see [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../Topic/Tutorial:%20Creating%20a%20Basic%20Table%20Report%20\(Report%20Builder\).md) or [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../Topic/Create%20a%20Basic%20Table%20Report%20\(SSRS%20Tutorial\).md).  
  
> [!NOTE]  
>  You can publish tables separately from a report as report parts. Read more about [Report Parts](Report%20Parts%20\(Report%20Builder%20and%20SSRS\).md).  
  
  
##  <a name="AddingTable"></a> Adding a Table to Display Detail Data  
 Add a table to the design surface from the Insert tab on the ribbon. You can add a table by using the Table or Matrix Wizard, which includes creating a data source connection and dataset and configuring the table, or a table based on the table template, which you configure manually.  
  
> [!NOTE]  
>  The wizard is available only in Report Builder.  
  
 To describe how to configure a table from beginning to end, this topic uses the table template.  
  
 By default, a new table has a fixed number of columns with a header row for labels and a data row for detail data. The following figure shows a new table added to the design surface.  
  
 ![Table template](../../Images\Image\ImageNotContaina/rs_TableTemplateNew.gif "rs_TableTemplateNew")  
  
 When you select the table, row and column handles appear on the outside of the table and brackets appear inside cells. Row handles display graphics that help you understand the purpose of each row. Brackets indicate group membership for a selected cell. The following figure shows a selected empty cell in a default table.  
  
 ![Table template on design surface, selected](../../Images\Image\ImageNotContaina/rs_TableTemplateNewSelected.gif "rs_TableTemplateNewSelected")  
  
 The row handle for the Data row shows the details symbol \(![Row handle with 3 parallel lines for details row](../../Images\Image\ImageNotContaina/rs_IconTablix_DetailsRow.gif "rs_IconTablix_DetailsRow")\). To display data on these rows, drag fields from the Report Data pane to the table cells in either the header or the details row. Both rows are filled in simultaneously. To add additional columns, drag the field to the table until you see an insertion point. After you add dataset fields to the table, you can change the default format for dates and currency to control the way they display in the report. The following diagram shows a table data region with these fields: Date, Order, Product, Qty, and Line Total.  
  
 ![Design, Table with column headers in Bold](../../Images\Image\ImageNotContaina/rs_BasicTableDetailsFormattedDesign.gif "rs_BasicTableDetailsFormattedDesign")  
  
 Check your design by viewing the report in Preview. The table expands down the page as needed. The label row and the details row each display once for every row in the dataset query result set. Each product sold in the order is listed on a separate row, along with the quantity and the line total for the item, as shown in the following figure:  
  
 ![Preview of table with bold column headers](../../Images\Image\ImageNotContaina/rs_BasicTableDetailsFormattedPreview.png "rs_BasicTableDetailsFormattedPreview")  
  
 The table that you start with is a template based on the tablix data region. You can enhance the design of your table by adding features that are supported by the underlying tablix data region. For more information, see [Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;](../Topic/Controlling%20the%20Tablix%20Data%20Region%20Display%20on%20a%20Report%20Page%20\(Report%20Builder%20and%20SSRS\).md). You can also continue to develop your table by adding row groups, column groups, and by adding or removing detail groups. For more information, see [Exploring the Flexibility of a Tablix Data Region &#40;Report Builder and SSRS&#41;](../Topic/Exploring%20the%20Flexibility%20of%20a%20Tablix%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md).  
  
### Adding Totals for Detail Data  
 To add totals, select cells with numeric data, and then use the shortcut menu to automatically add labels and totals for detail data for numeric fields. You can also specify other labels and totals manually. The following figure shows a typical totals row that includes both automatic and manually specified totals:  
  
 ![Total row added to table](../../Images\Image\ImageNotContaina/rs_BasicTableDetailsTotalDesign.gif "rs_BasicTableDetailsTotalDesign")  
  
 In Preview, the report displays the header row and the details row once for every row in the dataset query result set, and it displays the totals row. The follow figure shows the last few rows of the table including the total row.  
  
 ![Preview with table and total row](../../Images\Image\ImageNotContaina/rs_BasicTableDetailsTotalPreview.gif "rs_BasicTableDetailsTotalPreview")  
  
 For more information, see [Add a Total to a Group or Tablix Data Region &#40;Report Builder and SSRS&#41;](../Topic/Add%20a%20Total%20to%20a%20Group%20or%20Tablix%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md).  
  
##  <a name="AddingRowGroups"></a> Adding Row Groups to a Table  
 Just as you can drag a field from the Report Data pane to a cell to display detail data, you can drag a field to the Grouping pane to add a group. For a table, drag the field to the Row Groups pane. After you add a group, the table automatically adds cells in new columns in the row group area in which to display the group values. For more information about areas, see [Tablix Data Region Areas &#40;Report Builder and SSRS&#41;](../Topic/Tablix%20Data%20Region%20Areas%20\(Report%20Builder%20and%20SSRS\).md).  
  
 The following figure shows a table with two nested row groups in Design view. The row groups were created by dragging the Order field and then the Date field to the Row Groups pane and inserting each group as a parent of the existing groups. The figure shows a parent group based on date and a child group based on order number, as well as the details group that was defined by default.  
  
 ![Table grouped by Date and Order](../../Images\Image\ImageNotContaina/rs_BasicTableGroupsDesign.gif "rs_BasicTableGroupsDesign")  
  
 In Preview, the report displays the order data grouped first by date, and then by order, as shown in the follow figure.  
  
 ![Table grouped by date and then order](../../Images\Image\ImageNotContaina/rs_BasicTableGroupsPreview.png "rs_BasicTableGroupsPreview")  
  
 An alternative way of displaying grouped data is to indent the group hierarchy to display the nested relationship of groups instead of presenting each value in its own column. This style of formatting is called a stepped report. For more information about how to format group information as a stepped report, see [Create a Stepped Report &#40;Report Builder and SSRS&#41;](../Topic/Create%20a%20Stepped%20Report%20\(Report%20Builder%20and%20SSRS\).md).  
  
### Adding Totals to Row Groups  
 To show totals for a group, you can use the context\-sensitive **Add Total** command. For a row group, the Add Total command adds a row outside the group so that it repeats only once in relation to the group. For nested groups, the total row for the child group is outside the child group but inside the parent group. In such a case, it is useful to set the background color of the total row for the child group to distinguish it from the detail rows. You can also use a different background color to distinguish the table header and footer rows. The following figure shows the table with a total row added for the group based on order numbers.  
  
 ![Design view, add total rows to group and table](../../Images\Image\ImageNotContaina/rs_BasicTableGroupsTotalsColorDesign.gif "rs_BasicTableGroupsTotalsColorDesign")  
  
 When you view the report, the row displaying the order subtotals repeats once for every order number. The table footer displays totals for all dates. In the following figure, the last few rows show the last three detail rows, the subtotal for the last order number SO71952, and the totals for all dates in the table.  
  
 ![Preview, Table with Group Totals, last rows](../../Images\Image\ImageNotContaina/rs_BasicTableGroupsTotalsColorPreviewBottom.gif "rs_BasicTableGroupsTotalsColorPreviewBottom")  
  
 For more information, see [Add a Total to a Group or Tablix Data Region &#40;Report Builder and SSRS&#41;](../Topic/Add%20a%20Total%20to%20a%20Group%20or%20Tablix%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md).  
  
##  <a name="RemovingHidingRows"></a> Removing or Hiding Detail Rows  
 After you preview a table in a report, you may decide to remove existing detail rows. Or you might decide to hide them by default and allow the user to toggle between viewing more or less detail, as in a drilldown report.  
  
 To remove detail rows from a table, use the Grouping pane. Select the detail group, and use the shortcut menu to delete the group and the rows that display the detail data. The following figure shows the design view for a table grouped by date and order number, but with no detail rows. No total rows have been added to this table.  
  
 ![Design view, table with two groups, no details](../../Images\Image\ImageNotContaina/rs_BasicTableGroupsDrilldownNoDetailsDesign.gif "rs_BasicTableGroupsDrilldownNoDetailsDesign")  
  
 After you delete the details row, values are scoped to the row groups. The detail data no longer displays.  
  
> [!NOTE]  
>  Verify that after you remove a details row, the expression in each cell specifies an aggregate expression where appropriate. If necessary, edit the expression to specify aggregate functions as needed.  
  
 The following figure shows this report in Preview.  
  
 ![Preview, table with groups but no detail rows](../../Images\Image\ImageNotContaina/rs_BasicTableGroupsNoDetailsPreview.gif "rs_BasicTableGroupsNoDetailsPreview")  
  
 To add or remove rows from the table, see [Insert or Delete a Row &#40;Report Builder and SSRS&#41;](../Topic/Insert%20or%20Delete%20a%20Row%20\(Report%20Builder%20and%20SSRS\).md).  
  
 You can also hide the detail rows when the report is initially viewed. To do so, you can create a drilldown report, in which only the parent group data is displayed. For each inner group \(including the details group\), add a visibility toggle to the grouping cell of the containing group. For example, for the details group, add a toggle to the text box that displays the order number group value. For the order number group, add a toggle to the text box that displays the date group value. The following figure shows the row for September 01, 2001, expanded to display the first few orders.  
  
 ![Preview, table with expanded drilldown node](../../Images\Image\ImageNotContaina/rs_BasicTableGroupsDrilldownPreview.gif "rs_BasicTableGroupsDrilldownPreview")  
  
 For more information, see [Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](../Topic/Add%20an%20Expand%20or%20Collapse%20Action%20to%20an%20Item%20\(Report%20Builder%20and%20SSRS\).md).  
  
## See Also  
 [Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../Topic/Filter,%20Group,%20and%20Sort%20Data%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expressions &#40;Report Builder and SSRS&#41;](../Topic/Expressions%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Examples &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Examples%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../Topic/Tables,%20Matrices,%20and%20Lists%20\(Report%20Builder%20and%20SSRS\).md)  
  
  