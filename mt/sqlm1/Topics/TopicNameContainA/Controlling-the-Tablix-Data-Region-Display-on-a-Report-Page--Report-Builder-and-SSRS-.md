---
title: Controlling the Tablix Data Region Display on a Report Page (Report Builder and SSRS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f81c48cc-f038-4f57-988d-e9a3cbb46424
---
# Controlling the Tablix Data Region Display on a Report Page (Report Builder and SSRS)
  This topic describes properties for a tablix data region that you can modify to change the way a tablix data region appears when you view it in a report.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../Token\Other/ssRBRDDup_md.md)]  
  
## Controlling the Appearance of Data  
 The following features help control the appearance of a tablix data region:  
  
-   **Formatting data.** To format data in a table, matrix, or list, set the format properties of the text box in the cell. You can set properties for multiple cells at the same time. To format data in a chart, set formatting properties on the series. For more information, see [Formatting Report Items &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20Report%20Items%20\(Report%20Builder%20and%20SSRS\).md) and [Formatting a Chart &#40;Report Builder and SSRS&#41;](../Topic/Formatting%20a%20Chart%20\(Report%20Builder%20and%20SSRS\).md).  
  
-   **Writing expressions**. For more information, see [Expression Uses in Reports &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Uses%20in%20Reports%20\(Report%20Builder%20and%20SSRS\).md), and [Expression Examples &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Examples%20\(Report%20Builder%20and%20SSRS\).md).  
  
-   **Controlling sort order**. To control the sort order, you must define sort expressions on the data region. To control sort order for rows and columns that are associated with a group, you must define sort expressions on the group, including the details groups. You can also add interactive sort buttons to enable the user to sort a tablix data region or its groups. For more information, see [Sort Data in a Data Region &#40;Report Builder and SSRS&#41;](../Topic/Sort%20Data%20in%20a%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md).  
  
-   **Displaying a message when there is no data**. When no data exists for a report dataset at run time, you can write your own message to display in place of the data region. For more information, see [Set a No Data Message for a Data Region &#40;Report Builder and SSRS&#41;](../Topic/Set%20a%20No%20Data%20Message%20for%20a%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md).  
  
-   **Conditionally hiding data**. To conditionally control whether to show or hide a data region or parts of a data region, you can set the Hidden property to **True** or to an expression. Expressions can include references to report parameters. You can also specify a toggle item, so that user can decide to display detail data. For more information, see [Drilldown Action &#40;Report Builder and SSRS&#41;](../Topic/Drilldown%20Action%20\(Report%20Builder%20and%20SSRS\).md).  
  
-   **Merging cells.** Multiple contiguous cells within a table can be combined into a single cell. This is known as a column span or a cell merge. Cells can only be combined horizontally or vertically. When you merge cells, only the data in the first cell is preserved. Data in other cells is removed. Merged cells can be split into their original columns. For more information, see [Merge Cells in a Data Region &#40;Report Builder and SSRS&#41;](../Topic/Merge%20Cells%20in%20a%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md).  
  
## Controlling Tablix Data Region Position and Expansion on a Page  
 The following features help control the way a tablix data region displays in a rendered report:  
  
-   **Controlling the position of a tablix data region in relation to other report items**. A tablix data region can be positioned above, next to, or below other report items on the report design surface. At run time, [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] expands the tablix data region as needed for the data retrieved for the linked dataset, moving peer report items aside as needed. To anchor a tablix next to another report item, you must make the report items peers and adjust their relative positions. For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../Topic/Rendering%20Behaviors%20\(Report%20Builder%20%20and%20SSRS\).md).  
  
-   **Changing the Expansion Direction**. To control whether a tablix data region expands across the page from left\-to\-right \(LTR\) or from right\-to\-left \(RTL\), use the Direction property, which can be accessed through the Properties window. For more information, see [Rendering Data Regions &#40;Report Builder and SSRS&#41;](../Topic/Rendering%20Data%20Regions%20\(Report%20Builder%20and%20SSRS\).md).  
  
## Controlling How a Tablix Data Region Renders on a Page  
 The following list describes ways that you can help control how a tablix data region appears in a report:  
  
-   **Controlling paging**. To control the amount of data that displays on each report page, you can set page breaks on data regions. You can also set page breaks on groups. Page breaks can affect the on\-demand rendering performance by reducing the amount of data that needs to be processed on each page. For more information, see [Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](../Topic/Pagination%20in%20Reporting%20Services%20\(Report%20Builder%20%20and%20SSRS\).md) and [Add a Page Break &#40;Report Builder and SSRS&#41;](../Topic/Add%20a%20Page%20Break%20\(Report%20Builder%20and%20SSRS\).md).  
  
-   **Displaying data on either side of row headers**. You are not limited to displaying row headers on the side of a tablix data region. You can move the row headers between columns, so that columns of data appear before the row headers. To do this, modify the GroupsBeforeRowHeaders property for the matrix. You can access this property through the Properties window. The value for this property is an integer; for example, a value of 2 will display two groups instances of data region column data before displaying the column containing the row headers.  
  
## Controlling How Tablix Row and Column Groups Render  
 To control how a tablix data region groups render depends on the group structure. A tablix data region can have four areas, as shown in the following figure:  
  
 ![Tablix data region areas](../../Images\Image\ImageNotContaina/rs_TablixAreas.gif "rs_TablixAreas")  
  
 The row group area and column group area contain group headers. When a tablix data region has group headers, you control how rows and columns repeat by setting properties on the **General** page of the **Tablix Properties** dialog Box.  
  
 If a tablix data region has only a tablix body area, there are no group headers. There are only static and dynamic tablix members. A static member displays once in relation to a tablix row or column group. A dynamic member repeats once for every unique group value. For example, in a tablix data region that displays a sales order, the column names in the sales order can be displayed on a static row member. Each line in the sales order is displayed on a dynamic row member.  
  
 You can help control how a tablix member renders by setting properties in the Properties pane. For more information, see "Advanced mode" in [Grouping Pane &#40;Report Builder&#41;](../Topic/Grouping%20Pane%20\(Report%20Builder\).md).  
  
 The following list describes ways that you can help control how a tablix data region appears in a report:  
  
-   **Repeating row and column headers on multiple pages**.You can display row and column headers on each page that a tablix data region spans. For more information, see [Display Row and Column Headers on Multiple Pages &#40;Report Builder and SSRS&#41;](../Topic/Display%20Row%20and%20Column%20Headers%20on%20Multiple%20Pages%20\(Report%20Builder%20and%20SSRS\).md).  
  
-   **Keeping row and column headers in view when scrolling**. You can control whether to keep the row and column headers in view when you scroll a report using a browser. For more information, see [Keep Headers Visible When Scrolling Through a Report &#40;Report Builder and SSRS&#41;](../Topic/Keep%20Headers%20Visible%20When%20Scrolling%20Through%20a%20Report%20\(Report%20Builder%20and%20SSRS\).md).  
  
 For more information about how exporting a report to different formats affects the way a tablix data region renders on a page, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](../Topic/Rendering%20Behaviors%20\(Report%20Builder%20%20and%20SSRS\).md).  
  
## See Also  
 [Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](../Topic/Linking%20Multiple%20Data%20Regions%20to%20the%20Same%20Dataset%20\(Report%20Builder%20and%20SSRS\).md)   
 [Nested Data Regions &#40;Report Builder and SSRS&#41;](../Topic/Nested%20Data%20Regions%20\(Report%20Builder%20and%20SSRS\).md)   
 [Expression Scope for Totals, Aggregates, and Built-in Collections &#40;Report Builder and SSRS&#41;](../Topic/Expression%20Scope%20for%20Totals,%20Aggregates,%20and%20Built-in%20Collections%20\(Report%20Builder%20and%20SSRS\).md)   
 [Controlling Page Breaks, Headings, Columns, and Rows &#40;Report Builder and SSRS&#41;](../Topic/Controlling%20Page%20Breaks,%20Headings,%20Columns,%20and%20Rows%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tablix Data Region &#40;Report Builder and SSRS&#41;](../Topic/Tablix%20Data%20Region%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tables &#40;Report Builder  and SSRS&#41;](../Topic/Tables%20\(Report%20Builder%20%20and%20SSRS\).md)   
 [Matrices &#40;Report Builder and SSRS&#41;](../Topic/Matrices%20\(Report%20Builder%20and%20SSRS\).md)   
 [Lists &#40;Report Builder and SSRS&#41;](../Topic/Lists%20\(Report%20Builder%20and%20SSRS\).md)   
 [Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../Topic/Tables,%20Matrices,%20and%20Lists%20\(Report%20Builder%20and%20SSRS\).md)  
  
  