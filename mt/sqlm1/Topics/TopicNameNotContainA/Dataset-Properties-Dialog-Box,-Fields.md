---
title: Dataset Properties Dialog Box, Fields
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e1367556-736e-4a6b-b9e7-10432a3e50b5
robots: noindex,nofollow
---
# Dataset Properties Dialog Box, Fields
  Select **Fields** on the **Dataset Properties** dialog box to change the field collection for the report dataset. The fields list is automatically populated, but you can use **Fields** to add, edit, and delete query and calculated fields.  
  
## Options  
 **Add**  
 Add a new query field or calculated field to the dataset.  
  
 **Delete**  
 Delete the selected field from the dataset.  
  
 **Field Name**  
 Type a name for the field. The field must be unique within the dataset. For each existing field in the dataset query, the name is pre\-populated.  
  
 **Field Source**  
 Enter a value for the field.  
  
 For a calculated field, the field source must be the name of an existing field retrieved by the dataset query, or an expression that you create. For example, to create a field that represents 10 times the value in the query field Sales, use the expression `=10 * Fields!Sales.Value`.  
  
 For a query field, the field source must be the name of an existing field retrieved by the dataset query.  
  
 **Expression \(fx\)**  
 Add or change an expression for the calculated field. This button only appears when you click **Add** and select **Calculated Field**.  
  
## See Also  
 [Dataset Fields Collection &#40;Report Builder and SSRS&#41;](../Topic/Dataset%20Fields%20Collection%20\(Report%20Builder%20and%20SSRS\).md)   
 [Report Datasets &#40;SSRS&#41;](../Topic/Report%20Datasets%20\(SSRS\).md)   
 [Expressions &#40;Report Builder and SSRS&#41;](../Topic/Expressions%20\(Report%20Builder%20and%20SSRS\).md)  
  
  