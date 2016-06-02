---
title: Report Data Pane (Report Builder)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1492aa39-aeb1-4509-ab97-b9edd0901b7e
robots: noindex,nofollow
---
# Report Data Pane (Report Builder)
  Use the **Report Data** pane to view the currently defined parameters, data sources, datasets, field collections, and images in your report. The Report Dane displays a hierarchical view of the items that represent data in your report. The top level nodes represent built\-in fields, parameters, images, and data source references. Expand each node to view the data items. For example, when you expand a data source node, the datasets defined for that data source appear. When you expand a dataset, its field collection appears. Drag items to the report design surface or to the Grouping pane to link data with selected report items on the report page. For more information, see [Report Design View &#40;Report Builder&#41;](../Topic/Report%20Design%20View%20\(Report%20Builder\).md).  
  
## Options  
 **Built\-in Fields**  
 Represents commonly used fields in a report, such as the report name or page number. For more information, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../Topic/Built-in%20Collections%20in%20Expressions%20\(Report%20Builder%20and%20SSRS\).md).  
  
 **Parameters**  
 Represents the collection of report parameters, each of which can be single\-valued or multivalued. For more information, see [Report Parameters &#40;Report Builder and Report Designer&#41;](../Topic/Report%20Parameters%20\(Report%20Builder%20and%20Report%20Designer\).md).  
  
 **Images**  
 Represents the set of images used in the report. For more information, see [Images &#40;Report Builder and SSRS&#41;](../Topic/Images%20\(Report%20Builder%20and%20SSRS\).md).  
  
 **Data sources**  
 Represents an embedded data source or a reference to a shared data source. A data source represents a source of data for the report. A data source is the parent node for the collection of datasets that use it. For more information, see [Report Datasets &#40;SSRS&#41;](../Topic/Report%20Datasets%20\(SSRS\).md) and [Data Connections, Data Sources, and Connection Strings in Report Builder](../../Topics\TopicNameNotContainA/Data-Connections,-Data-Sources,-and-Connection-Strings-in-Report-Builder.md).  
  
 **Datasets**  
 Represents the data that is retrieved from a data source by running one command, for example, a [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] query that retrieves data from a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database. A dataset is the parent node for the collection of fields that is specified by the query, and also includes calculated fields. Report Builder supports query designers that help you specify a query. For more information, see [Report Datasets &#40;SSRS&#41;](../Topic/Report%20Datasets%20\(SSRS\).md).  
  
## See Also  
 [Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../Topic/Dataset%20Fields%20Collection%20\(Report%20Builder%20and%20SSRS\).md)   
 [Report Builder Help for Dialog Boxes, Panes, and Wizards](assetId:///2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [Grouping Pane &#40;Report Builder&#41;](../Topic/Grouping%20Pane%20\(Report%20Builder\).md)   
 [Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../Topic/Finding,%20Viewing,%20and%20Managing%20Reports%20\(Report%20Builder%20and%20SSRS%20\).md)  
  
  