---
title: Query the Parameters Used to Create a Mining Model
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
ms.assetid: ce7719e0-6127-4d9c-a753-0e0a3db065e1
---
# Query the Parameters Used to Create a Mining Model
  The composition of a mining model is affected not only by the training cases, but by the parameters that were set when the model was created. Therefore, you might find it useful to retrieve the parameter settings of an existing model to better understand the behavior of the model. Retrieving parameters is also useful when documenting a particular version of that model.  
  
 To find the parameters that were used when the model was created, you create a query against one of the mining model schema rowsets. In [!INCLUDE[ssASCurrent](../../Token\Other/ssASCurrent_md.md)], these schema rowsets are exposed as a set of system views that you can query easily by using Transact\-SQL syntax. This procedure describes how to create a query that returns the parameters that were used to create the specified mining model.  
  
### To open a Query window for a schema rowset query  
  
1.  In [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], open the instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] that contains the model you want to query.  
  
2.  Right\-click the instance name, select **New Query**, and then select **DMX**.  
  
    > [!NOTE]  
    >  You can also create a query against a data mining model by using the **MDX** template.  
  
3.  If the instance contains multiple databases, select the database that contains the model you want to query from the **Available Databases** list in the toolbar.  
  
### To return model parameters for an existing mining model  
  
1.  In the DMX query pane, type or paste the following text:  
  
    ```  
    SELECT MINING_PARAMETERS  
    FROM $system.DMSCHEMA_MINING_MODELS  
    WHERE MODEL_NAME = ''  
    ```  
  
2.  In Object Explorer, select the mining model you want, and then drag it into the DMX Query pane, between the single quotation marks.  
  
3.  Press F5, or click **Execute**.  
  
## Example  
 The following code returns a list of the parameters that were used to create the mining model that you build in the [Basic Data Mining Tutorial](../Topic/Basic%20Data%20Mining%20Tutorial.md). These parameters include the explicit values for any defaults used by the mining services available from providers on the server.  
  
```  
SELECT MINING_PARAMETERS   
FROM $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM Clustering'  
```  
  
 The code example returns the following parameters for the clustering model:  
  
 eExample Results:  
  
 MINING\_PARAMETERS  
  
 CLUSTER\_COUNT\=10,CLUSTER\_SEED\=0,CLUSTERING\_METHOD\=1,MAXIMUM\_INPUT\_ATTRIBUTES\=255,MAXIMUM\_STATES\=100,MINIMUM\_SUPPORT\=1,MODELLING\_CARDINALITY\=10,SAMPLE\_SIZE\=50000,STOPPING\_TOLERANCE\=10  
  
## See Also  
 [Data Mining Query Tasks and How-tos](../../Topics\TopicNameNotContainA/Data-Mining-Query-Tasks-and-How-tos.md)   
 [Data Mining Queries](../../Topics\TopicNameNotContainA/Data-Mining-Queries.md)  
  
  