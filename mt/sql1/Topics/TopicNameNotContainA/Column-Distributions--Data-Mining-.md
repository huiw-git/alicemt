---
title: "Column Distributions (Data Mining)"
ms.custom: na
ms.date: 07/04/2016
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
caps.latest.revision: 33
caps.handback.revision: 0
manager: paulettm
---
# Column Distributions (Data Mining)
In [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)], you can define column distributions in a mining structure, to affect how algorithms process the data in those columns when you create mining models. For some algorithms, it is useful to define the distribution of any continuous columns before you process the model, if the columns are known to contain common distributions of values. If you do not define the distributions, the resulting mining models may produce less accurate predictions than if the distributions were defined, because the algorithms will have less information from which to interpret the data.  
  
 The algorithms that are available in [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] support the following distribution types:  
  
 **Normal**  
 The values for the continuous column form a histogram with a normal distribution.  
  
 ![Histogram with normal distribution](../../Topics/TopicNameNotContainA/images/Normal_Distribution.gif "Normal_Distribution")  
  
 **Log Normal**  
 The values for the continuous column form a histogram, where the curve is elongated at the upper end and is skewed toward the lower end.  
  
 ![Histogram with log normal distribution](../../Topics/TopicNameNotContainA/images/Log_Normal_Distribution.gif "Log_Normal_Distribution")  
  
 **Uniform**  
 The values for the continuous column form a flat curve, in which all values are equally likely.  
  
 ![Histogram with uniform distribution](../../Topics/TopicNameNotContainA/images/Uniform_Distribution.gif "Uniform_Distribution")  
  
 For more information about the algorithms that [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] provides, see [Data Mining Algorithms (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Data-Mining-Algorithms--Analysis-Services---Data-Mining-.md).  
  
## See Also  
 [Content Types (Data Mining)](../../Topics/TopicNameNotContainA/Content-Types--Data-Mining-.md)   
 [Mining Structures (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Mining-Structures--Analysis-Services---Data-Mining-.md)   
 [Discretization Methods (Data Mining)](../../Topics/TopicNameNotContainA/Discretization-Methods--Data-Mining-.md)   
 [Distributions (DMX)](assetId:///cfbb9f38-ae71-401e-867f-15c6a2b6fb97)   
 [Mining Structure Columns](../../Topics/TopicNameNotContainA/Mining-Structure-Columns.md)