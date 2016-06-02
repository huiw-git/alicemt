---
title: Column Distributions (Data Mining)
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
ms.assetid: 87e700de-32be-4bc8-b01d-ba4ee1ab48de
---
# Column Distributions (Data Mining)
  In [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], you can define column distributions in a mining structure, to affect how algorithms process the data in those columns when you create mining models. For some algorithms, it is useful to define the distribution of any continuous columns before you process the model, if the columns are known to contain common distributions of values. If you do not define the distributions, the resulting mining models may produce less accurate predictions than if the distributions were defined, because the algorithms will have less information from which to interpret the data.  
  
 The algorithms that are available in [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] support the following distribution types:  
  
 **Normal**  
 The values for the continuous column form a histogram with a normal distribution.  
  
 ![Histogram with normal distribution](../../Images\Image\ImageNotContaina/Normal_Distribution.gif "Normal_Distribution")  
  
 **Log Normal**  
 The values for the continuous column form a histogram, where the curve is elongated at the upper end and is skewed toward the lower end.  
  
 ![Histogram with log normal distribution](../../Images\Image\ImageNotContaina/Log_Normal_Distribution.gif "Log_Normal_Distribution")  
  
 **Uniform**  
 The values for the continuous column form a flat curve, in which all values are equally likely.  
  
 ![Histogram with uniform distribution](../../Images\Image\ImageNotContaina/Uniform_Distribution.gif "Uniform_Distribution")  
  
 For more information about the algorithms that [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] provides, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Algorithms%20\(Analysis%20Services%20-%20Data%20Mining\).md).  
  
## See Also  
 [Content Types &#40;Data Mining&#41;](../Topic/Content%20Types%20\(Data%20Mining\).md)   
 [Mining Structures &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Structures%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Discretization Methods &#40;Data Mining&#41;](../Topic/Discretization%20Methods%20\(Data%20Mining\).md)   
 [Distributions &#40;DMX&#41;](../Topic/Distributions%20\(DMX\).md)   
 [Mining Structure Columns](../../Topics\TopicNameNotContainA/Mining-Structure-Columns.md)  
  
  