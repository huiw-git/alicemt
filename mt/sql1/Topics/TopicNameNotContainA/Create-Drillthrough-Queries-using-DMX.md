---
title: "Create Drillthrough Queries using DMX"
ms.custom: na
ms.date: 08/09/2016
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
caps.latest.revision: 6
caps.handback.revision: 0
manager: paulettm
---
# Create Drillthrough Queries using DMX
For all models that support drillthrough, you can retrieve case data and structure data by creating a DMX query in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)] or any other client that supports DMX.  
  
> [!WARNING]  
>  To view the data, drillthrough must have been enabled, and you must have the necessary permissions.  
  
## Specifying Drillthrough Options  
 The general syntax is for retrieving model cases and structure cases is as follows:  
  
```  
SELECT <model column list>, StructureColumn('<structure column name') FROM <modelname>.CASES  
```  
  
 For additional information about using DMX queries to return case data, see [SELECT FROM <model\>.CASES (DMX)](assetId:///d58acb47-aaa6-40b7-b8c4-6a6700fbc1dd) and [SELECT FROM <structure\>.CASES](assetId:///36f50213-14dc-42da-b899-20240b781e1a).  
  
## Examples  
 The following DMX query returns the case data for a specific product series, from a time series model. The query also returns the column **Amount**, which was not used in the model but is available in the mining structure.  
  
```  
SELECT [DateSeries], [Model Region], Quantity, StructureColumn('Amount') AS [M200 Pacific Amount]  
FROM Forecasting.CASES  
WHERE [Model Region] = 'M200 Pacific'  
```  
  
 Note that in this example, an alias has been used to rename the structure column. If you do not assign an alias to the structure column, the column is returned with the name 'Expression'. This is the default behavior for all unnamed columns.  
  
## See Also  
 [Drillthrough Queries (Data Mining)](../../Topics/TopicNameNotContainA/Drillthrough-Queries--Data-Mining-.md)   
 [Drillthrough on Mining Structures](../../Topics/TopicNameNotContainA/Drillthrough-on-Mining-Structures.md)