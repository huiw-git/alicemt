---
title: Classified Columns (Data Mining)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68bf3b78-dc12-497c-898f-b43a45646123
---
# Classified Columns (Data Mining)
  When you define a classified column, you create a relationship between the current column and another column in the mining structure. The data in the mining structure column that you designate as the classified column contains categorical information that describes the values in another column in the mining structure.  
  
 For example, suppose you have two columns with numerical data: one column, \[Yearly Purchases\], contains the total yearly purchases per customer for a specific calendar year, and the other column, \[Standard Deviations\], contains the standard deviations for those values. In this case you could designate the \[Yearly Purchases\] column as the classified column, and the model would be able to use this relationship in analysis.  
  
> [!NOTE]  
>  The algorithms provided in [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] do not support the use of classified columns; this feature is provided for use in creating custom algorithms.  
  
## Defining a Classified Column  
 The data type of a classified column must be either **Long** or **Double**.  
  
 The following list describes the content types that [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] supports for classified columns.  
  
 **PROBABILITY**  
 The value in the column is the probability of the associated value, and is a number between 0 and 1.  
  
 **VARIANCE**  
 The value in the column is the variance of the associated value.  
  
 **STDEV**  
 The value in the column is the standard deviation of the associated value.  
  
 **PROBABILITY\_VARIANCE**  
 The value in the column is the variance of the probability for the associated value.  
  
 **PROBABILITY\_STDEV**  
 The value in the column is the standard deviation of the probability for the associated value.  
  
 **SUPPORT**  
 The value in the column is the weight, or case replication factor, of the associated value.  
  
## See Also  
 [Content Types &#40;Data Mining&#41;](../Topic/Content%20Types%20\(Data%20Mining\).md)   
 [Mining Structures &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Structures%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Data Types &#40;Data Mining&#41;](../Topic/Data%20Types%20\(Data%20Mining\).md)  
  
  