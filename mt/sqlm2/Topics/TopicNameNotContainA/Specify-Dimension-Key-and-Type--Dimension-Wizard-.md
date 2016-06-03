---
title: Specify Dimension Key and Type (Dimension Wizard)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d7d5db55-36c3-45f6-ade3-29aa516589c1
---
# Specify Dimension Key and Type (Dimension Wizard)
  Use the **Specify Dimension Key and Type** page to define the key attribute of the dimension and to indicate whether the dimension is a slowly changing dimension \(SCD\).  
  
> [!NOTE]  
>  This page is displayed only if you selected **Build the dimension without using a data source** on the **Select Build Method** page and if you selected **Standard dimension** on the **Select the Dimension Type** page.  
  
## Options  
 **Key attribute**  
 Select the attribute that will be the key attribute for the dimension.  
  
> [!NOTE]  
>  If no attributes have been defined for the dimension, the only value available for this option is **Create key attribute automatically.** This value is not available if any attributes are defined for the dimension.  
  
 **This is a changing dimension**  
 Select to indicate that the dimension is a slowly changing dimension. Selecting this option will create additional columns and attributes that can be used to track the movement of members within the hierarchies of the dimension over time.  
  
## See Also  
 [Dimension Wizard F1 Help](../../Topics\TopicNameNotContainA/Dimension-Wizard-F1-Help.md)   
 [Dimensions &#40;Analysis Services - Multidimensional Data&#41;](../Topic/Dimensions%20\(Analysis%20Services%20-%20Multidimensional%20Data\).md)   
 [Dimensions in Multidimensional Models](../../Topics\TopicNameNotContainA/Dimensions-in-Multidimensional-Models.md)  
  
  