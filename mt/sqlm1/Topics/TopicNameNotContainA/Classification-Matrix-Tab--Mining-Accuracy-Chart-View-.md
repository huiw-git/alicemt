---
title: Classification Matrix Tab (Mining Accuracy Chart View)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 85d5a047-d656-41e0-8a31-400271c2a620
---
# Classification Matrix Tab (Mining Accuracy Chart View)
  The **Classification Matrix** tab displays a classification matrix for each model selected in the models grid on the **Column Mapping** tab. The classification matrix is only available if the predictable column that is selected in the **Column Mapping** tab is not continuous. For a more detailed description of the **Classification Matrix** tab, see [Testing and Validation &#40;Data Mining&#41;](../Topic/Testing%20and%20Validation%20\(Data%20Mining\).md).  
  
## Options  
 **Copy**  
 Copies the content of each classification matrix to the clipboard.  
  
 **Counts for \<model\> on \< predictable column\>**  
 Displays a classification matrix for each mining model in the mining structure. The matrix contains the following columns:  
  
|Value|Description|  
|-----------|-----------------|  
|**Predicted**|Contains a row for each state of the predictable column.|  
|**\<states\> \(actual\)**|A column for each state in the predictable column. If the state of the row and the column correspond, the cell represents the actual number of times the state exists in the database. If they do not correspond, the cell represents the error of the prediction.|  
  
## See Also  
 [Mining Accuracy Chart Designer &#40;Data Mining&#41;](../Topic/Mining%20Accuracy%20Chart%20Designer%20\(Data%20Mining\).md)   
 [Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](../Topic/Testing%20and%20Validation%20Tasks%20and%20How-tos%20\(Data%20Mining\).md)   
 [Testing and Validation &#40;Data Mining&#41;](../Topic/Testing%20and%20Validation%20\(Data%20Mining\).md)  
  
  