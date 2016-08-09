---
title: "Adding Data to a Tablix Data Region (Report Builder and SSRS)"
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
ms.assetid: 8f1d0a76-afed-480f-98fb-89e2d4eb09b1
caps.latest.revision: 7
caps.handback.revision: 0
manager: mblythe
---
# Adding Data to a Tablix Data Region (Report Builder and SSRS)
To display data from a report dataset in a table or matrix, in each data cell, specify the name of a dataset field to display. You can display detail data or grouped data. If you add groups to a table or matrix, rows and columns for group values and group data are added automatically. You can then add subtotals and totals for your data.  
  
 All data in a data region belongs to at least one group. Detail data is a member of the details group. For more information about detail and grouped data, see [Understanding Groups (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Understanding-Groups--Report-Builder-and-SSRS-.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Topics/TopicNameContainA/tokens/ssRBRDDup_md.md)]  
  
## Adding Detail Data  
 Detail data is all the data from a report dataset after filters are applied to the dataset, data region, and details group. All detail data displayed in a single tablix data region must come from the same report dataset.  
  
 To add detail data from a report dataset to a tablix data region, drag a dataset field from the Report Data pane to each cell in the detail row. For existing cells in a tablix data region, you can add or edit a dataset field expression by using the field selector in each cell or by dragging a field from the Report Data pane to the cell. To create additional columns, you can drag the field from the Report Data pane and insert it into an existing tablix data region.  
  
 By default, at run-time, a cell in the details row displays detail data and a cell in a group row displays an aggregate value. For more information about tablix rows and columns, see [Tablix Data Region Cells, Rows, and Columns (Report Builder) and SSRS](../../Topics/TopicNameNotContainA/Tablix-Data-Region-Cells--Rows--and-Columns--Report-Builder--and-SSRS.md).  
  
 A table template and a list template provide a details row. A matrix template has no details row. If your tablix data region has no details row, you can add one by defining a details group. For more information, see [Add a Details Group (Report Builder and SSRS)](../../Topics/TopicNameContainA/Add-a-Details-Group--Report-Builder-and-SSRS-.md).  
  
## Adding Grouped Data  
 Grouped data is all the detail data specified by a group expression after filters are applied to the dataset, data region, and the group. To organize detail data in groups, drag fields from the Report Data pane to the Grouping pane. When you add a group, [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] automatically adds related rows or columns to the tablix data region on which to display grouped data. Cells in these rows or columns are associated with grouped data. For more information, see [Add or Delete a Group in a Data Region (Report Builder and SSRS)](../../Topics/TopicNameContainA/Add-or-Delete-a-Group-in-a-Data-Region--Report-Builder-and-SSRS-.md).  
  
 By default, when you add a dataset field that represents numeric data to a cell in a group row or column, the value of the cell is the sum of the grouped data scoped to the innermost row and column group memberships for the cell. You can change the default aggregate function **Sum** to any other aggregate function, such as **Avg** or **Count**. You can also change the default scope for an aggregate calculation, for example, to calculate the percentage a value contributes to a row group. For more information, see [Expression Scope for Totals, Aggregates, and Built-in Collections (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expression-Scope-for-Totals--Aggregates--and-Built-in-Collections--Report-Builder-and-SSRS-.md).  
  
 By default, all grouped data comes from the same report dataset. In a tablix data region, you can include aggregate values from another dataset by specifying the dataset name as a scope. You can specify multiple aggregate values from multiple datasets within a single tablix data region. For more information, see [Aggregate Functions Reference (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Aggregate-Functions-Reference--Report-Builder-and-SSRS-.md).  
  
## Adding Subtotals and Totals  
 To add subtotals for a group and grand totals for the data region, use the Add Total feature on the shortcut menu in a cell or in the Grouping pane. The rows and columns on which to display the totals are automatically added for you. Subtotal and total expressions default to using the [Sum](../../Topics/TopicNameNotContainA/Sum-Function--Report-Builder-and-SSRS-.md) aggregate function. After you add the expression, you can change the default function. For more information, see [Add a Total to a Group or Tablix Data Region (Report Builder and SSRS)](../../Topics/TopicNameContainA/Add-a-Total-to-a-Group-or-Tablix-Data-Region--Report-Builder-and-SSRS-.md) and [Expression Scope for Totals, Aggregates, and Built-in Collections (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expression-Scope-for-Totals--Aggregates--and-Built-in-Collections--Report-Builder-and-SSRS-.md).  
  
## Adding Labels  
 To add labels for a group or for the data region, add a row or column outside the group that you want to label. Label rows and columns are similar to rows and columns that you add to display totals. For more information, see [Insert or Delete a Row (Report Builder and SSRS)](../../Topics/TopicNameContainA/Insert-or-Delete-a-Row--Report-Builder-and-SSRS-.md) or [Insert or Delete a Column (Report Builder and SSRS)](../../Topics/TopicNameContainA/Insert-or-Delete-a-Column--Report-Builder-and-SSRS-.md).  
  
## Adding an Existing Tablix Data Region from Another Report  
 You can copy a data region from another report and paste it into-a new or existing report. After you paste the data region, you must ensure that the dataset the data region uses is defined, and that the dataset fields have identical names and data types as in the original report. You cannot copy datasets from one report to another, but if your reports use shared data sources, you can quickly duplicate the dataset in the another report. Also you can import the query text for the queries that retrieve the data for the dataset, which makes it simple to duplicate the queries in reports. For more information, see [Report Embedded Datasets and Shared Datasets (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Report-Embedded-Datasets-and-Shared-Datasets--Report-Builder-and-SSRS-.md).  
  
## See Also  
 [Expressions (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expressions--Report-Builder-and-SSRS-.md)   
 [Report Parameters (Report Builder and Report Designer)](../../Topics/TopicNameNotContainA/Report-Parameters--Report-Builder-and-Report-Designer-.md)   
 [Interactive Sort, Document Maps, and Links (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Interactive-Sort--Document-Maps--and-Links--Report-Builder-and-SSRS-.md)   
 [Add Dataset Filters, Data Region Filters, and Group Filters (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Add-Dataset-Filters--Data-Region-Filters--and-Group-Filters--Report-Builder-and-SSRS-.md)   
 [Add, Edit, Refresh Fields in the Report Data Pane (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Add--Edit--Refresh-Fields-in-the-Report-Data-Pane--Report-Builder-and-SSRS-.md)   
 [Add an Expression (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Add-an-Expression--Report-Builder-and-SSRS-.md)