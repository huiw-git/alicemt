---
title: Select the Source Cube Dimension (Data Mining Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 556e216b-5e21-4160-967d-4c57591fbab4
---
# Select the Source Cube Dimension (Data Mining Wizard)
  Use the **Select the Source Cube Dimension** page to select the dimension from the cube that contains the cases you want to analyze. For example, if you are building a model that analyzes the purchasing behavior of customers based on demographics, you would select the Customer dimension, which typically contains a unique record for each customer and various attributes that represent demographics, such as gender, location, or income. Later in the wizard you will have the opportunity to add a table that is related to this case table: for example, you might add a nested table that shows which products the customer has purchased.  
  
> [!NOTE]  
>  This page will appear only if you have selected **From existing cube** on the **Select the Definition Method** page of the wizard.  
  
## Options  
 **Select a Source Cube Dimension**  
 Select the dimension of the cube that will provide the source data for your mining structure.  
  
## Choosing a Dimension  
 Because you can select only one dimension for use in your model, it is important that you understand the cube structure and select the dimension that provides the best information for your model. If you are not sure which dimension to use, it might be helpful to browse the cube and review the fields and the data in them by using Dimension Designer. For more information, see [Browse Dimension Data in Dimension Designer](../../Topics\TopicNameNotContainA/Browse-Dimension-Data-in-Dimension-Designer.md).  
  
 If you are unfamiliar with dimensions in general, see [Introduction to Dimensions &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Introduction%20to%20Dimensions%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md).  
  
 For more information about the type of information that is typically contained in a single dimension, including attributes and measures that might be useful for data mining, see [Dimension Relationships](../Topic/Dimension%20Relationships.md).  
  
 If the dimension that you choose does not contain all of the related attributes that you need to build the data mining model, you might need to modify the dimension. For more information, see [Define Database Dimensions](../../Topics\TopicNameNotContainA/Define-Database-Dimensions.md).  
  
## See Also  
 [Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Wizard%20F1%20Help%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Create the Data Mining Structure &#40;Data Mining Wizard&#41;](../Topic/Create%20the%20Data%20Mining%20Structure%20\(Data%20Mining%20Wizard\).md)   
 [Select the Case Key &#40;Data Mining Wizard&#41;](../Topic/Select%20the%20Case%20Key%20\(Data%20Mining%20Wizard\).md)  
  
  