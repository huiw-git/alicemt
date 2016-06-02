---
title: Discretization Methods (Data Mining)
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
ms.assetid: 02c0df7b-6ca5-4bd0-ba97-a5826c9da120
---
# Discretization Methods (Data Mining)
  Some algorithms that are used to create data mining models in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] require specific content types in order to function correctly. For example, the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Naive Bayes algorithm cannot use continuous columns as input and cannot predict continuous values. Additionally, some columns may contain so many values that the algorithm cannot easily identify interesting patterns in the data from which to create a model.  
  
 In these cases, you can discretize the data in the columns to enable the use of the algorithms to produce a mining model. *Discretization* is the process of putting values into buckets so that there are a limited number of possible states. The buckets themselves are treated as ordered and discrete values. You can discretize both numeric and string columns.  
  
 There are several methods that you can use to discretize data. If your data mining solution uses relational data, you can control the number of buckets to use for grouping data by setting the value of the [DiscretizationBucketCount](assetId:///P:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount) property. The default number of buckets is 5.  
  
 If your data mining solution uses data from an Online Analytical Processing \(OLAP\) cube, the data mining algorithm automatically computes the number of buckets to generate by using the following equation, where n is the number of distinct values of data in the column:  
  
 `Number of Buckets = sqrt(n)`  
  
 If you do not want [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] to calculate the number of buckets, you can use the [DiscretizationBucketCount](assetId:///P:Microsoft.AnalysisServices.DimensionAttribute.DiscretizationBucketCount) property to manually specify the number of buckets.  
  
 The following table describes the methods that you can use to discretize data in [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)].  
  
|Discretization method|Description|  
|---------------------------|-----------------|  
|**AUTOMATIC**|[!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] determines which discretization method to use.|  
|**CLUSTERS**|The algorithm divides the data into groups by sampling the training data, initializing to a number of random points, and then running several iterations of the Microsoft Clustering algorithm using the Expectation Maximization \(EM\) clustering method. The **CLUSTERS** method is useful because it works on any distribution curve. However, it requires more processing time than the other discretization methods.<br /><br /> This method can only be used with numeric columns.|  
|**EQUAL\_AREAS**|The algorithm divides the data into groups that contain an equal number of values. This method is best used for normal distribution curves, but does not work well if the distribution includes a large number of values that occur in a narrow group in the continuous data. For example, if one\-half of the items have a cost of 0, one\-half the data will occur under a single point in the curve. In such a distribution, this method breaks the data up in an effort to establish equal discretization into multiple areas. This produces an inaccurate representation of the data.|  
  
## Remarks  
  
-   You can use the **EQUAL\_AREAS** method to discretize strings.  
  
-   The **CLUSTERS** method uses a random sample of 1000 records to discretize data. Use the **EQUAL\_AREAS** method if you do not want the algorithm to sample data.  
  
  
  
## See Also  
 [Content Types &#40;Data Mining&#41;](../Topic/Content%20Types%20\(Data%20Mining\).md)   
 [Content Types &#40;DMX&#41;](../Topic/Content%20Types%20\(DMX\).md)   
 [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../Topic/Data%20Mining%20Algorithms%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Mining Structures &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Structures%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Data Types &#40;Data Mining&#41;](../Topic/Data%20Types%20\(Data%20Mining\).md)   
 [Mining Structure Columns](../../Topics\TopicNameNotContainA/Mining-Structure-Columns.md)   
 [Column Distributions &#40;Data Mining&#41;](../Topic/Column%20Distributions%20\(Data%20Mining\).md)  
  
  