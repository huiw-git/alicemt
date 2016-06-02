---
title: Measure Group Bindings Dialog Box (Analysis Services - Multidimensional Data)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed642780-5350-438e-af73-b9ceab3f876d
---
# Measure Group Bindings Dialog Box (Analysis Services - Multidimensional Data)
  Use the **Measure Group Bindings** dialog box to create and modify direct relationships between non\-granularity attributes in a cube dimension and columns in a measure group for a regular dimension relationship, as well as to specify null processing options for any attribute in a cube dimension, from the **Define Relationship** dialog box.  
  
## Options  
 **Measure group table**  
 Displays the name of the fact table for the selected measure group.  
  
 **Attributes**  
 Displays a grid of attributes and dimension tables. Select an attribute to create or modify properties in **Relationship** for the selected attribute. The grid contains the following columns:  
  
|Option|Definition|  
|------------|----------------|  
|**Attribute Name**|Displays the name of the attribute.|  
|**Dimension Table**|Displays the name of the dimension table on which the attribute is based.|  
  
 **Relationship**  
 Displays a grid of relationships between dimension table columns for the selected attribute and fact table columns for the selected measure group as well as the null processing option for the relationship. The grid contains the following columns:  
  
|Option|Definition|  
|------------|----------------|  
|**Dimension Columns**|Displays the columns from the dimension table on which the attribute selected in **Attributes** is based.|  
|**Measure Group Columns**|Select either **Inherited from dimension** to use the measure group relationship inherited from the dimension, or select a column from the fact table on which the measure group is based to explicitly define a relationship.|  
|**Null Processing**|Select a null processing option for the attribute. For more information about null processing options, see [NullProcessing Element &#40;ASSL&#41;](../Topic/NullProcessing%20Element%20\(ASSL\).md).|  
  
## See Also  
 [Define Relationship Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Define%20Relationship%20Dialog%20Box%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](../Topic/Analysis%20Services%20Designers%20and%20Dialog%20Boxes%20\(Multidimensional%20Data\).md)  
  
  