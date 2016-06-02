---
title: Data Source Properties Dialog Box, General
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44b5edd3-5c11-4d3d-91b8-5871aa0572ed
---
# Data Source Properties Dialog Box, General
  Select **General** on the **Data Source Properties** dialog box to display and modify connection information for a data source in the report.  
  
## Options  
 **Name**  
 Type the name of the data source. The data source name must be unique within the report. By default, a general name, such as DataSource1 or DataSource2, is assigned to the data source.  
  
 **Embedded connection**  
 Select this option when you do not want to use a shared data source.  
  
 **Type**  
 Select a data processing extension. The list displays all registered extensions.  
  
 **Connection string**  
 Enter a connection string for the data source. Click **Edit** to build the connection string using the **Connection Properties** dialog box. Click the **Expressions** \(*fx*\) button to edit the expression.  
  
 **Use shared data source reference**  
 Select this option to link to a shared data source. Select a shared data source from the drop\-down list. To edit the selected data source, click **Edit**. If **Use shared data source reference** is selected, **Type** and **Connection string** are disabled.  
  
 **Use a single transaction when processing the queries**  
 Select this option to indicate that datasets that use this data source are run in a single transaction against the database. To include transactions for subreports that use the same data source, set **MergeTransactions** to **True** in the subreport's **Other** properties section of the **Properties** pane.  
  
## See Also  
 [Report Datasets &#40;SSRS&#41;](../Topic/Report%20Datasets%20\(SSRS\).md)   
 [Create an Embedded or Shared Data Source &#40;SSRS&#41;](../Topic/Create%20an%20Embedded%20or%20Shared%20Data%20Source%20\(SSRS\).md)   
 [Data Connections, Data Sources, and Connection Strings &#40;Report Builder and SSRS&#41;](../Topic/Data%20Connections,%20Data%20Sources,%20and%20Connection%20Strings%20\(Report%20Builder%20and%20SSRS\).md)   
 [Data Source Properties Dialog Box, Credentials](../../Topics\TopicNameNotContainA/Data-Source-Properties-Dialog-Box,-Credentials.md)  
  
  