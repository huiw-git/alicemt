---
title: Dataset Properties Dialog Box, Fields (Report Builder)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75c7e54a-3d20-4c9a-88da-ab36dce2ce42
---
# Dataset Properties Dialog Box, Fields (Report Builder)
  Select **Fields** on the **Dataset Properties** dialog box to change the field collection for the report dataset. The fields list is automatically populated, but you can use **Fields** to add, edit, and delete query and calculated fields.  
  
 Calculated fields are supported only on embedded datasets. For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](../Topic/Report%20Embedded%20Datasets%20and%20Shared%20Datasets%20\(Report%20Builder%20and%20SSRS\).md).  
  
## Options  
 **Add**  
 Add a new query or calculated field to the dataset.  
  
 **Delete**  
 Delete the selected field from the dataset.  
  
 **Field Name**  
 Type a name for the field. The field must be unique within the dataset. For each existing field in the dataset, the name is pre\-populated.  
  
 **Field Source**  
 Enter a value for the field.  
  
 For a calculated field, the field source must be the name of an existing field retrieved by the dataset query, or an expression that you create. For example, to create a field that represents 10 times the value in the query field Sales, use the expression `=10 * Fields!Sales.Value`.  
  
 For a query field, the field source must be the name of an existing field retrieved by the dataset query.  
  
 **Expression \(fx\)**  
 Add or change an expression for the new calculated field. This button only appears when you click **Add** and select **Calculated Field**.  
  
## See Also  
 [Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../Topic/Dataset%20Fields%20Collection%20\(Report%20Builder%20and%20SSRS\).md)   
 [Create a Shared Dataset or Embedded Dataset &#40;Report Builder and SSRS&#41;](../Topic/Create%20a%20Shared%20Dataset%20or%20Embedded%20Dataset%20\(Report%20Builder%20and%20SSRS\).md)   
 [Report Builder Help for Dialog Boxes, Panes, and Wizards](assetId:///2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [Dataset Properties Dialog Box, Options &#40;Report Builder&#41;](../Topic/Dataset%20Properties%20Dialog%20Box,%20Options%20\(Report%20Builder\).md)   
 [Dataset Properties Dialog Box, Filters &#40;Report Builder&#41;](../Topic/Dataset%20Properties%20Dialog%20Box,%20Filters%20\(Report%20Builder\).md)   
 [Dataset Properties Dialog Box, Parameters &#40;Report Builder&#41;](../Topic/Dataset%20Properties%20Dialog%20Box,%20Parameters%20\(Report%20Builder\).md)   
 [Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](../Topic/Dataset%20Properties%20Dialog%20Box,%20Query%20\(Report%20Builder\).md)   
 [Expressions &#40;Report Builder and SSRS&#41;](../Topic/Expressions%20\(Report%20Builder%20and%20SSRS\).md)   
 [Data Connections, Data Sources, and Connection Strings in Report Builder](../../Topics\TopicNameNotContainA/Data-Connections,-Data-Sources,-and-Connection-Strings-in-Report-Builder.md)  
  
  