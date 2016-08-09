---
title: "Dataset Properties Dialog Box, Fields (Report Builder)"
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
ms.assetid: 75c7e54a-3d20-4c9a-88da-ab36dce2ce42
caps.latest.revision: 15
caps.handback.revision: 0
manager: mblythe
---
# Dataset Properties Dialog Box, Fields (Report Builder)
Select **Fields** on the **Dataset Properties** dialog box to change the field collection for the report dataset. The fields list is automatically populated, but you can use **Fields** to add, edit, and delete query and calculated fields.  
  
 Calculated fields are supported only on embedded datasets. For more information, see [Report Embedded Datasets and Shared Datasets (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Report-Embedded-Datasets-and-Shared-Datasets--Report-Builder-and-SSRS-.md).  
  
## Options  
 **Add**  
 Add a new query or calculated field to the dataset.  
  
 **Delete**  
 Delete the selected field from the dataset.  
  
 **Field Name**  
 Type a name for the field. The field must be unique within the dataset. For each existing field in the dataset, the name is pre-populated.  
  
 **Field Source**  
 Enter a value for the field.  
  
 For a calculated field, the field source must be the name of an existing field retrieved by the dataset query, or an expression that you create. For example, to create a field that represents 10 times the value in the query field Sales, use the expression `=10 * Fields!Sales.Value`.  
  
 For a query field, the field source must be the name of an existing field retrieved by the dataset query.  
  
 **Expression (fx)**  
 Add or change an expression for the new calculated field. This button only appears when you click **Add** and select **Calculated Field**.  
  
## See Also  
 [Dataset Fields Collection (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Dataset-Fields-Collection--Report-Builder-and-SSRS-.md)   
 [Create a Shared Dataset or Embedded Dataset (Report Builder and SSRS)](../../Topics/TopicNameContainA/Create-a-Shared-Dataset-or-Embedded-Dataset--Report-Builder-and-SSRS-.md)   
 [Report Builder Help for Dialog Boxes, Panes, and Wizards](assetId:///2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [Dataset Properties Dialog Box, Options (Report Builder)](../../Topics/TopicNameNotContainA/Dataset-Properties-Dialog-Box--Options--Report-Builder-.md)   
 [Dataset Properties Dialog Box, Filters (Report Builder)](../../Topics/TopicNameNotContainA/Dataset-Properties-Dialog-Box--Filters--Report-Builder-.md)   
 [Dataset Properties Dialog Box, Parameters (Report Builder)](../../Topics/TopicNameNotContainA/Dataset-Properties-Dialog-Box--Parameters--Report-Builder-.md)   
 [Dataset Properties Dialog Box, Query (Report Builder)](../../Topics/TopicNameNotContainA/Dataset-Properties-Dialog-Box--Query--Report-Builder-.md)   
 [Expressions (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expressions--Report-Builder-and-SSRS-.md)   
 [Data Connections, Data Sources, and Connection Strings in Report Builder](../../Topics/TopicNameNotContainA/Data-Connections--Data-Sources--and-Connection-Strings-in-Report-Builder.md)