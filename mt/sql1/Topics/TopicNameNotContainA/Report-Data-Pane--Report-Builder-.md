---
title: "Report Data Pane (Report Builder)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1492aa39-aeb1-4509-ab97-b9edd0901b7e
caps.latest.revision: 12
manager: mblythe
robots: noindex,nofollow
---
# Report Data Pane (Report Builder)
Use the **Report Data** pane to view the currently defined parameters, data sources, datasets, field collections, and images in your report. The Report Dane displays a hierarchical view of the items that represent data in your report. The top level nodes represent built-in fields, parameters, images, and data source references. Expand each node to view the data items. For example, when you expand a data source node, the datasets defined for that data source appear. When you expand a dataset, its field collection appears. Drag items to the report design surface or to the Grouping pane to link data with selected report items on the report page. For more information, see [Report Design View (Report Builder)](../../Topics/TopicNameNotContainA/Report-Design-View--Report-Builder-.md).  
  
## Options  
 **Built-in Fields**  
 Represents commonly used fields in a report, such as the report name or page number. For more information, see [Built-in Collections in Expressions (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Built-in-Collections-in-Expressions--Report-Builder-and-SSRS-.md).  
  
 **Parameters**  
 Represents the collection of report parameters, each of which can be single-valued or multivalued. For more information, see [Report Parameters (Report Builder and Report Designer)](../../Topics/TopicNameNotContainA/Report-Parameters--Report-Builder-and-Report-Designer-.md).  
  
 **Images**  
 Represents the set of images used in the report. For more information, see [Images (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Images--Report-Builder-and-SSRS-.md).  
  
 **Data sources**  
 Represents an embedded data source or a reference to a shared data source. A data source represents a source of data for the report. A data source is the parent node for the collection of datasets that use it. For more information, see [Report Datasets (SSRS)](../../Topics/TopicNameNotContainA/Report-Datasets--SSRS-.md) and [Data Connections, Data Sources, and Connection Strings in Report Builder](../../Topics/TopicNameNotContainA/Data-Connections--Data-Sources--and-Connection-Strings-in-Report-Builder.md).  
  
 **Datasets**  
 Represents the data that is retrieved from a data source by running one command, for example, a [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] query that retrieves data from a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] database. A dataset is the parent node for the collection of fields that is specified by the query, and also includes calculated fields. Report Builder supports query designers that help you specify a query. For more information, see [Report Datasets (SSRS)](../../Topics/TopicNameNotContainA/Report-Datasets--SSRS-.md).  
  
## See Also  
 [Dataset Fields Collection (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Dataset-Fields-Collection--Report-Builder-and-SSRS-.md)   
 [Report Builder Help for Dialog Boxes, Panes, and Wizards](assetId:///2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [Grouping Pane (Report Builder)](../../Topics/TopicNameNotContainA/Grouping-Pane--Report-Builder-.md)   
 [Finding, Viewing, and Managing Reports (Report Builder and SSRS )](../../Topics/TopicNameNotContainA/Finding--Viewing--and-Managing-Reports--Report-Builder-and-SSRS--.md)