---
title: "Dataset Properties Dialog Box, Fields"
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
ms.assetid: e1367556-736e-4a6b-b9e7-10432a3e50b5
caps.latest.revision: 36
manager: mblythe
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
 Type a name for the field. The field must be unique within the dataset. For each existing field in the dataset query, the name is pre-populated.  
  
 **Field Source**  
 Enter a value for the field.  
  
 For a calculated field, the field source must be the name of an existing field retrieved by the dataset query, or an expression that you create. For example, to create a field that represents 10 times the value in the query field Sales, use the expression `=10 * Fields!Sales.Value`.  
  
 For a query field, the field source must be the name of an existing field retrieved by the dataset query.  
  
 **Expression (fx)**  
 Add or change an expression for the calculated field. This button only appears when you click **Add** and select **Calculated Field**.  
  
## See Also  
 [Dataset Fields Collection (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Dataset-Fields-Collection--Report-Builder-and-SSRS-.md)   
 [Report Datasets (SSRS)](../../Topics/TopicNameNotContainA/Report-Datasets--SSRS-.md)   
 [Expressions (Report Builder and SSRS)](../../Topics/TopicNameNotContainA/Expressions--Report-Builder-and-SSRS-.md)