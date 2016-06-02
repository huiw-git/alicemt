---
title: Create Drillthrough Queries using DMX
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
ms.assetid: 42c896ee-e5ee-4017-b66e-31d1fe66d369
---
# Create Drillthrough Queries using DMX
  For all models that support drillthrough, you can retrieve case data and structure data by creating a DMX query in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or any other client that supports DMX.  
  
> [!WARNING]  
>  To view the data, drillthrough must have been enabled, and you must have the necessary permissions.  
  
## Specifying Drillthrough Options  
 The general syntax is for retrieving model cases and structure cases is as follows:  
  
```  
SELECT <model column list>, StructureColumn('<structure column name') FROM <modelname>.CASES  
```  
  
 For additional information about using DMX queries to return case data, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](../Topic/SELECT%20FROM%20%3Cmodel%3E.CASES%20\(DMX\).md) and [SELECT FROM &#60;structure&#62;.CASES](../Topic/SELECT%20FROM%20%3Cstructure%3E.CASES.md).  
  
## Examples  
 The following DMX query returns the case data for a specific product series, from a time series model. The query also returns the column **Amount**, which was not used in the model but is available in the mining structure.  
  
```  
SELECT [DateSeries], [Model Region], Quantity, StructureColumn('Amount') AS [M200 Pacific Amount]  
FROM Forecasting.CASES  
WHERE [Model Region] = 'M200 Pacific'  
```  
  
 Note that in this example, an alias has been used to rename the structure column. If you do not assign an alias to the structure column, the column is returned with the name 'Expression'. This is the default behavior for all unnamed columns.  
  
## See Also  
 [Drillthrough Queries &#40;Data Mining&#41;](../Topic/Drillthrough%20Queries%20\(Data%20Mining\).md)   
 [Drillthrough on Mining Structures](../../Topics\TopicNameNotContainA/Drillthrough-on-Mining-Structures.md)  
  
  