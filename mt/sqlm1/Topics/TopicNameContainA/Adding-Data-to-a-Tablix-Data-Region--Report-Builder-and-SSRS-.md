---
title: Adding Data to a Tablix Data Region (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8f1d0a76-afed-480f-98fb-89e2d4eb09b1
---
# Adding Data to a Tablix Data Region (Report Builder and SSRS)
  To display data from a report dataset in a table or matrix, in each data cell, specify the name of a dataset field to display. You can display detail data or grouped data. If you add groups to a table or matrix, rows and columns for group values and group data are added automatically. You can then add subtotals and totals for your data.  
  
 All data in a data region belongs to at least one group. Detail data is a member of the details group. For more information about detail and grouped data, see [Understanding Groups &#40;Report Builder and SSRS&#41;](../Topic/Understanding%20Groups%20\(Report%20Builder%20and%20SSRS\).md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## Adding Detail Data  
 Detail data is all the data from a report dataset after filters are applied to the dataset, data region, and details group. All detail data displayed in a single tablix data region must come from the same report dataset.  
  
 To add detail data from a report dataset to a tablix data region, drag a dataset field from the Report Data pane to each cell in the detail row. For existing cells in a tablix data region, you can add or edit a dataset field expression by using the field selector in each cell or by dragging a field from the Report Data pane to the cell. To create additional columns, you can drag the field from the Report Data pane and insert it into an existing tablix data region.  
  
 By default, at run\-time, a cell in the details row displays detail data and a cell in a group row displays an aggregate value. For more information about tablix rows and columns, see [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](../Topic/Tablix%20Data%20Region%20Cells,%20Rows,%20and%20Columns%20\(Report%20Builder\)%20and%20SSRS.md).  
  
 A table template and a list template provide a details row. A matrix template has no details row. If your tablix data region has no details row, you can add one by defining a details group. For more information, see [Add a Details Group &#40;Report Builder and SSRS&#41;](../Topic/Add%20a%20Details%20Group%20\(Report%20Builder%20and%20SSRS\).md).  
  
## Adding Grouped Data  
 Grouped data is all the detail data specified by a group expression after filters are applied to the dataset, data region, and the group. To organize detail data in groups, drag fields from the Report Data pane to the Grouping pane. When you add a group, [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] automatically adds related rows or columns to the tablix data region on which to display grouped data. Cells in these rows or columns are associated with grouped data. For more information, see [Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;](../Topic/Add%20or%20Delete%20a%20Group%20in%20a%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md).  
  
 By default, when you add a dataset field that represents numeric data to a cell in a group row or column, the value of the cell is the sum of the grouped data scoped to the innermost row and column group memberships for the cell. You can change the default aggregate function Sum to any other aggregate function, such as Avg or Count. You can also change the default scope for an aggregate calculation, for example, to calculate the percentage a value contributes to a row group. For more information, see [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Scope%20for%20Totals,%20Aggregates,%20and%20Built-in%20Collections%20\(Report%20Builder%20and%20SSRS\).md).  
  
 By default, all grouped data comes from the same report dataset. In a tablix data region, you can include aggregate values from another dataset by specifying the dataset name as a scope. You can specify multiple aggregate values from multiple datasets within a single tablix data region. For more information, see [Aggregate Functions Reference &#40;Report Builder and SSRS&#41;](../Topic/Aggregate%20Functions%20Reference%20\(Report%20Builder%20and%20SSRS\).md).  
  
## Adding Subtotals and Totals  
 To add subtotals for a group and grand totals for the data region, use the Add Total feature on the shortcut menu in a cell or in the Grouping pane. The rows and columns on which to display the totals are automatically added for you. Subtotal and total expressions default to using the [Sum](../Topic/Sum%20Function%20\(Report%20Builder%20and%20SSRS\).md) aggregate function. After you add the expression, you can change the default function. For more information, see [Add a Total to a Group or Tablix Data Region &#40;Report Builder and SSRS&#41;](../Topic/Add%20a%20Total%20to%20a%20Group%20or%20Tablix%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md) and [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Scope%20for%20Totals,%20Aggregates,%20and%20Built-in%20Collections%20\(Report%20Builder%20and%20SSRS\).md).  
  
## Adding Labels  
 To add labels for a group or for the data region, add a row or column outside the group that you want to label. Label rows and columns are similar to rows and columns that you add to display totals. For more information, see [Insert or Delete a Row &#40;Report Builder and SSRS&#41;](../Topic/Insert%20or%20Delete%20a%20Row%20\(Report%20Builder%20and%20SSRS\).md) or [Insert or Delete a Column &#40;Report Builder and SSRS&#41;](../Topic/Insert%20or%20Delete%20a%20Column%20\(Report%20Builder%20and%20SSRS\).md).  
  
## Adding an Existing Tablix Data Region from Another Report  
 You can copy a data region from another report and paste it into\-a new or existing report. After you paste the data region, you must ensure that the dataset the data region uses is defined, and that the dataset fields have identical names and data types as in the original report. You cannot copy datasets from one report to another, but if your reports use shared data sources, you can quickly duplicate the dataset in the another report. Also you can import the query text for the queries that retrieve the data for the dataset, which makes it simple to duplicate the queries in reports. For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../Topic/Report%20Embedded%20Datasets%20and%20Shared%20Datasets%20\(Report%20Builder%20and%20SSRS\).md).  
  
## See Also  
 [Expressions &#40;Report Builder and SSRS&#41;](../Topic/Expressions%20\(Report%20Builder%20and%20SSRS\).md)   
 [Report Parameters &#40;Report Builder and Report Designer&#41;](../Topic/Report%20Parameters%20\(Report%20Builder%20and%20Report%20Designer\).md)   
 [Interactive Sort, Document Maps, and Links &#40;Report Builder and SSRS&#41;](../Topic/Interactive%20Sort,%20Document%20Maps,%20and%20Links%20\(Report%20Builder%20and%20SSRS\).md)   
 [Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](../Topic/Add%20Dataset%20Filters,%20Data%20Region%20Filters,%20and%20Group%20Filters%20\(Report%20Builder%20and%20SSRS\).md)   
 [Add, Edit, Refresh Fields in the Report Data Pane &#40;Report Builder and SSRS&#41;](../Topic/Add,%20Edit,%20Refresh%20Fields%20in%20the%20Report%20Data%20Pane%20\(Report%20Builder%20and%20SSRS\).md)   
 [Add an Expression &#40;Report Builder and SSRS&#41;](../Topic/Add%20an%20Expression%20\(Report%20Builder%20and%20SSRS\).md)  
  
  