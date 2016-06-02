---
title: Neural Network Model Query Examples
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
ms.assetid: 81b06183-620f-4e0c-bc10-532e6a1f0829
---
# Neural Network Model Query Examples
  When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or a prediction query, which uses the patterns in the model to make predictions for new data. For example, a content query for a neural network model might retrieve model metadata such as the number of hidden layers. Alternatively, a prediction query might suggest classifications based on an input and optionally provide probabilities for each classification.  
  
 This section explains how to create queries for models that are based on the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Neural Network algorithm.  
  
 **Content queries**  
  
 [Getting Model Metadata by Using DMX](#bkmk_Query1)  
  
 [Retrieving Model Metadata from the Schema Rowset](#bkmk_Query2)  
  
 [Retrieving the Input Attributes for the Model](#bkmk_Query3)  
  
 [Retrieving Weights from the Hidden Layer](#bkmk_Query4)  
  
 **Prediction queries**  
  
 [Creating a Singleton Prediction](#bkmk_Query5)  
  
## Finding Information about a Neural Network Model  
 All mining models expose the content learned by the algorithm according to a standardized schema, the mining model schema rowset. This information provides details about the model and includes the basic metadata, structures discovered in analysis, and parameters that are used when processing. You can create queries against the model content by using Data Mining Extension \(DMX\) statements.  
  
###  <a name="bkmk_Query1"></a> Sample Query 1: Getting Model Metadata by Using DMX  
 The following query returns some basic metadata about a model that was built by using the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Neural Network algorithm. In a neural network model, the parent node of the model contains only the name of the model, the name of the database where the model is stored, and the number of child nodes. However, the marginal statistics node \(NODE\_TYPE \= 24\) provides both this basic metadata and some derived statistics about the input columns used in the model.  
  
 The following sample query is based on the mining model that you create in the [Intermediate Data Mining Tutorial](../Topic/Lesson%205:%20Building%20Neural%20Network%20and%20Logistic%20Regression%20Models%20\(Intermediate%20Data%20Mining%20Tutorial\).md), named `Call Center Default NN`. The model uses data from a call center to explore possible correlations between staffing and the number of calls, orders, and issues. The DMX statement retrieves data from the marginal statistics node of the neural network model. The query includes the FLATTENED keyword, because the input attribute statistics of interest are stored in a nested table, NODE\_DISTRIBUTION. However, if your query provider supports hierarchical rowsets you do not need to use the FLATTENED keyword.  
  
```  
SELECT FLATTENED MODEL_CATALOG, MODEL_NAME,   
(    SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE,  
     [SUPPORT], [PROBABILITY], VALUETYPE   
     FROM NODE_DISTRIBUTION  
) AS t  
FROM [Call Center Default NN].CONTENT  
WHERE NODE_TYPE = 24  
```  
  
> [!NOTE]  
>  You must enclose the name of the nested table columns SUPPORT and PROBABILITY in brackets to distinguish them from the reserved keywords of the same name.  
  
 Example results:  
  
|MODEL\_CATALOG|MODEL\_NAME|t.ATTRIBUTE\_NAME|t.ATTRIBUTE\_VALUE|t.SUPPORT|t.PROBABILITY|t.VALUETYPE|  
|--------------------|-----------------|-----------------------|------------------------|---------------|-------------------|-----------------|  
|Adventure Works DW Multidimensional 2012|Call Center NN|Average Time Per Issue|Missing|0|0|1|  
|Adventure Works DW Multidimensional 2012|Call Center NN|Average Time Per Issue|\< 64.7094100096|11|0.407407407|5|  
  
 For a definition of what the columns in the schema rowset mean in the context of a neural network model, see [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Model%20Content%20for%20Neural%20Network%20Models%20\(Analysis%20Services%20-%20Data%20Mining\).md).  
  
###  <a name="bkmk_Query2"></a> Sample Query 2: Retrieving Model Metadata from the Schema Rowset  
 You can find the same information that is returned in a DMX content query by querying the data mining schema rowset. However, the schema rowset provides some additional columns. The following sample query returns the date that the model was created, the date it was modified, and the date that the model was last processed. The query also returns the predictable columns, which are not easily available from the model content, and the parameters that were used to build the model. This information can be useful for documenting the model.  
  
```  
SELECT MODEL_NAME, DATE_CREATED, LAST_PROCESSED, PREDICTION_ENTITY, MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'Call Center Default NN'  
```  
  
 Example results:  
  
|||  
|-|-|  
|MODEL\_NAME|Call Center Default NN|  
|DATE\_CREATED|1\/10\/2008 5:07:38 PM|  
|LAST\_PROCESSED|1\/10\/2008 5:24:02 PM|  
|PREDICTION\_ENTITY|Average Time Per Issue,<br /><br /> Grade Of Service,<br /><br /> Number Of Orders|  
|MINING\_PARAMETERS|HOLDOUT\_PERCENTAGE\=30, HOLDOUT\_SEED\=0,<br /><br /> MAXIMUM\_INPUT\_ATTRIBUTES\=255, MAXIMUM\_OUTPUT\_ATTRIBUTES\=255,<br /><br /> MAXIMUM\_STATES\=100, SAMPLE\_SIZE\=10000, HIDDEN\_NODE\_RATIO\=4|  
  
###  <a name="bkmk_Query3"></a> Sample Query 3: Retrieving the Input Attributes for the Model  
 You can retrieve the input attribute\-value pairs that were used to create the model by querying the child nodes \(NODE\_TYPE \= 20\) of the input layer \(NODE\_TYPE \= 18\). The following query returns a list of input attributes from the node descriptions.  
  
```  
SELECT NODE_DESCRIPTION  
FROM [Call Center Default NN].CONTENT  
WHERE NODE_TYPE = 2  
```  
  
 Example results:  
  
|NODE\_DESCRIPTION|  
|-----------------------|  
|Average Time Per Issue\=64.7094100096 \- 77.4002099712|  
|Day Of Week\=Fri.|  
|Level 1 Operators|  
  
 Only a few representative rows from the results are shown here. However, you can see that the NODE\_DESCRIPTION provides slightly different information depending on the data type of the input attribute.  
  
-   If the attribute is a discrete or discretized value, the attribute and either its value or its discretized range are returned.  
  
-   If the attribute is a continuous numeric data type, the NODE\_DESCRIPTION contains only the attribute name. However, you can retrieve the nested NODE\_DISTRIBUTION table to obtain the mean, or return the NODE\_RULE to obtain the minimum and maximum values of the numeric range.  
  
 The following query shows how to query the nested NODE\_DISTRIBUTION table to return the attributes in one column, and their values in another column. For continuous attributes, the value of the attribute is represented by its mean.  
  
```  
SELECT FLATTENED   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE  
FROM NODE_DISTRIBUTION) as t  
FROM [Call Center Default NN -- Predict Service and Orders].CONTENT  
WHERE NODE_TYPE = 21  
```  
  
 Example results:  
  
|t.ATTRIBUTE\_NAME|t.ATTRIBUTE\_VALUE|  
|-----------------------|------------------------|  
|Average Time Per Issue|64.7094100096 \- 77.4002099712|  
|Day Of Week|Fri.|  
|Level 1 Operators|3.2962962962963|  
  
 The minimum and maximum range values are stored in the NODE\_RULE column, and are represented as an XML fragment, as shown in the following example:  
  
```  
<NormContinuous field="Level 1 Operators">    
  <LinearNorm orig="2.83967303681711" norm="-1" />    
  <LinearNorm orig="3.75291955577548" norm="1" />    
</NormContinuous>    
```  
  
###  <a name="bkmk_Query4"></a> Sample Query 4: Retrieving Weights from the Hidden Layer  
 The model content of a neural network model is structured in a way that makes it easy to retrieve details about any node in the network. Moreover, the ID numbers of the nodes provide information that helps you identify relationships among the node types.  
  
 The following query demonstrates how to retrieve the coefficients that are stored under a particular node of the hidden layer. The hidden layer consists of an organizer node \(NODE\_TYPE \= 19\), which contains only metadata, and multiple child nodes \(NODE\_TYPE \= 22\), which contain the coefficients for the various combinations of attributes and values. This query returns only the coefficient nodes.  
  
```  
SELECT FLATTENED TOP 1 NODE_UNIQUE_NAME,   
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, VALUETYPE  
FROM NODE_DISTRIBUTION) as t  
FROM  [Call Center Default NN -- Predict Service and Orders].CONTENT  
WHERE NODE_TYPE = 22  
AND [PARENT_UNIQUE_NAME] = '40000000200000000' FROM [Call Center Default NN].CONTENT  
```  
  
 Example results:  
  
|NODE\_UNIQUE\_NAME|t.ATTRIBUTE\_NAME|t.ATTRIBUTE\_VALUE|t.VALUETYPE|  
|------------------------|-----------------------|------------------------|-----------------|  
|70000000200000000|6000000000000000a|\-0.178616518|7|  
|70000000200000000|6000000000000000b|\-0.267561918|7|  
|70000000200000000|6000000000000000c|0.11069497|7|  
|70000000200000000|6000000000000000d|0.123757712|7|  
|70000000200000000|6000000000000000e|0.294565343|7|  
|70000000200000000|6000000000000000f|0.22245318|7|  
|70000000200000000||0.188805045|7|  
  
 The partial results shown here demonstrate how the neural network model content relates the hidden node to the input nodes.  
  
-   The unique names of nodes in the hidden layer always begin with 70000000.  
  
-   The unique names of nodes in the input layer always begin with 60000000.  
  
 Thus, these results tell you that the node denoted by the ID 70000000200000000 had six different coefficients \(VALUETYPE \= 7\) passed to it. The values of the coefficients are in the ATTRIBUTE\_VALUE column. You can determine exactly which input attribute the coefficient is for by using the node ID in the ATTRIBUTE\_NAME column. For example, the node ID 6000000000000000a refers to input attribute and value, `Day of Week = 'Tue.'` You can use the node ID to create a query, or you can browse to the node by using the [Microsoft Generic Content Tree Viewer](../Topic/Microsoft%20Generic%20Content%20Tree%20Viewer%20\(Data%20Mining\).md).  
  
 Similarly, if you query the NODE\_DISTRIBUTION table of the nodes in the output layer \(NODE\_TYPE \= 23\), you can see the coefficients for each output value. However, in the output layer, the pointers refer back to the nodes of the hidden layer. For more information, see [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Model%20Content%20for%20Neural%20Network%20Models%20\(Analysis%20Services%20-%20Data%20Mining\).md).  
  
## Using a Neural Network Model to Make Predictions  
 The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Neural Network algorithm supports both classification and regression. You can use prediction functions with these models to provide new data and create either singleton or batch predictions.  
  
###  <a name="bkmk_Query5"></a> Sample Query 5: Creating a Singleton Prediction  
 The easiest way to build a prediction query on a neural network model is to use the Prediction Query Builder, available on the **Mining Prediction** tab of Data Mining Designer in both [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] and [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. You can browse the model in the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Neural Network Viewer to filter attributes of interest and view trends, and then switch to the **Mining Prediction** tab to create a query and predict new values for those trends.  
  
 For example, you can browse the call center model to view correlations between the order volumes and other attributes. To do this, open the model in the viewer, and for **Input**, select **\<All\>**.  Next, for **Output**, select **Number of Orders**. For **Value 1**, select the range that represents the most orders, and for **Value 2**, select the range that represents the fewest orders. You can then see at a glance all the attributes that the model correlates with order volume.  
  
 By browsing the results in the viewer, you find that certain days of the week have low order volumes, and that an increase in the number of operators seems to be correlated with higher sales. You could then use a prediction query on the model to test a "what if" hypothesis and ask if increasing the number of level 2 operators on a low\-volume day would increase orders. To do this, create a query such as the following:  
  
```  
SELECT Predict([Call Center Default NN].[Number of Orders]) AS [Predicted Orders],  
PredictProbability([Call Center Default NN].[Number of Orders]) AS [Probability]  
FROM [Call Center Default NN]  
NATURAL PREDICTION JOIN   
(SELECT 'Tue.' AS [Day of Week],  
13 AS [Level 2 Operators]) AS t  
```  
  
 Example results:  
  
|Predicted Orders|Probability|  
|----------------------|-----------------|  
|364|0.9532…|  
  
 The predicted sales volume is higher than the current range of sales for Tuesday, and the probability of the prediction is very high. However, you might want to create multiple predictions by using a batch process to test a variety of hypotheses on the model.  
  
> [!NOTE]  
>  The Data Mining Add\-Ins for Excel 2007 provide logistic regression wizards that make it easy to answer complex questions, such as how many Level Two Operators would be needed to improve service grade to a target level for a specific shift. The data mining add\-ins are a free download, and include wizards that are based on the neural network and\/or logistic regression algorithms. For more information, see the [Data Mining Add\-ins for Office 2007](http://go.microsoft.com/fwlink/?LinkID=117790) Web site.  
  
## List of Prediction Functions  
 All [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] algorithms support a common set of functions. There are no prediction functions that are specific to the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Neural Network algorithm; however, the algorithm supports the functions that are listed in the following table.  
  
|||  
|-|-|  
|Prediction Function|Usage|  
|[IsDescendant &#40;DMX&#41;](../Topic/IsDescendant%20\(DMX\).md)|Determines whether one node is a child of another node in the neural network graph.|  
|[PredictAdjustedProbability &#40;DMX&#41;](../Topic/PredictAdjustedProbability%20\(DMX\).md)|Returns the weighted probability.|  
|[PredictHistogram &#40;DMX&#41;](../Topic/PredictHistogram%20\(DMX\).md)|Returns a table of values related to the current predicted value.|  
|[PredictVariance &#40;DMX&#41;](../Topic/PredictVariance%20\(DMX\).md)|Returns variance for the predicted value.|  
|[PredictProbability &#40;DMX&#41;](../Topic/PredictProbability%20\(DMX\).md)|Returns probability  for the predicted value.|  
|[PredictStdev &#40;DMX&#41;](../Topic/PredictStdev%20\(DMX\).md)|Returns the standard deviance for the predicted value.|  
|[PredictSupport &#40;DMX&#41;](../Topic/PredictSupport%20\(DMX\).md)|For neural network and logistic regression models, returns a single value that represents the size of the training set for the entire model.|  
  
 For a list of the functions that are common to all [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] algorithms, see [Algorithm Reference \(Analysis Services \- Data Mining\)](https://technet.microsoft.com/library/bb895228\(v=sql.105\).aspx). For the syntax of specific functions, see [Data Mining Extensions &#40;DMX&#41; Function Reference](../Topic/Data%20Mining%20Extensions%20\(DMX\)%20Function%20Reference.md).  
  
## See Also  
 [Microsoft Neural Network Algorithm](../../Topics\TopicNameNotContainA/Microsoft-Neural-Network-Algorithm.md)   
 [Microsoft Neural Network Algorithm Technical Reference](../../Topics\TopicNameNotContainA/Microsoft-Neural-Network-Algorithm-Technical-Reference.md)   
 [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Model%20Content%20for%20Neural%20Network%20Models%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;](../Topic/Lesson%205:%20Building%20Neural%20Network%20and%20Logistic%20Regression%20Models%20\(Intermediate%20Data%20Mining%20Tutorial\).md)  
  
  