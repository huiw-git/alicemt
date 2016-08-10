---
title: "Decision Trees Model Query Examples"
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
ms.assetid: ceaf1370-9dd1-4d1a-a143-7f89a723ef80
caps.latest.revision: 25
caps.handback.revision: 0
manager: paulettm
---
# Decision Trees Model Query Examples
When you create a query against a data mining model, you can create a content query, which provides details about the patterns discovered in analysis, or you can create a prediction query, which uses the patterns in the model to make predictions for new data. For example, a content query for a decision trees model might provide statistics about the number of cases at each level of the tree, or the rules that differentiate between cases. Alternatively, a prediction query maps the model to new data in order to generate recommendations, classifications, and so forth. You can also retrieve metadata about the model by using a query.  
  
 This section explains how to create queries for models that are based on the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Decision Trees algorithm.  
  
 **Content Queries**  
  
 [Retrieving Model Parameters from the Data Mining Schema Rowset](#bkmk_Query1)  
  
 [Getting Details about Trees in the Model by Using DMX](#bkmk_Query2)  
  
 [Retrieving Subtrees from the Model](#bkmk_Query3)  
  
 **Prediction Queries**  
  
 [Returning Predictions with Probabilities](#bkmk_Query4)  
  
 [Predicting Associations from a Decision Trees Model](#bkmk_Query5)  
  
 [Retrieving a Regression Formula from a Decision Trees Model](#bkmk_Query6)  
  
##  <a name="bkmk_top2"></a> Finding Information about a Decision Trees Model  
 To create meaningful queries on the content of a decision trees model, you should understand the structure of the model content, and which node types store what kind of information. For more information, see [Mining Model Content for Decision Tree Models (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Mining-Model-Content-for-Decision-Tree-Models--Analysis-Services---Data-Mining-.md).  
  
###  <a name="bkmk_Query1"></a> Sample Query 1: Retrieving Model Parameters from the Data Mining Schema Rowset  
 By querying the data mining schema rowset, you can find metadata about the model, such as when it was created, when the model was last processed, the name of the mining structure that the model is based on, and the name of the column used as the predictable attribute. You can also return the parameters that were used when the model was first created.  
  
```  
select MINING_PARAMETERS   
from $system.DMSCHEMA_MINING_MODELS  
WHERE MODEL_NAME = 'TM_Decision Tree'  
```  
  
 Sample results:  
  
 MINING_PARAMETERS  
  
 COMPLEXITY_PENALTY=0.5, MAXIMUM_INPUT_ATTRIBUTES=255,MAXIMUM_OUTPUT_ATTRIBUTES=255,MINIMUM_SUPPORT=10,SCORE_METHOD=4,SPLIT_METHOD=3,FORCE_REGRESSOR=  
  
###  <a name="bkmk_Query2"></a> Sample Query 2: Returning Details about the Model Content by Using DMX  
 The following query returns some basic information about the decision trees that were created when you built the model in the [Basic Data Mining Tutorial](assetId:///6602edb6-d160-43fb-83c8-9df5dddfeb9c). Each tree structure is stored in its own node. Because this model contains a single predictable attribute, there is only one tree node. However, if you create an association model by using the Decision Trees algorithm, there might be hundreds of trees, one for each product.  
  
 This query returns all the nodes of type 2, which are the top level nodes of a tree that represents a particular predictable attribute.  
  
> [!NOTE]  
>  The column, `CHILDREN_CARDINALITY`, must be enclosed in brackets to distinguish it from the MDX reserved keyword of the same name.  
  
```  
SELECT MODEL_NAME, NODE_NAME, NODE_CAPTION,   
NODE_SUPPORT, [CHILDREN_CARDINALITY]  
FROM TM_DecisionTrees.CONTENT  
WHERE NODE_TYPE = 2  
```  
  
 Example results:  
  
|MODEL_NAME|NODE_NAME|NODE_CAPTION|NODE_SUPPORT|CHILDREN_CARDINALITY|  
|-----------------|----------------|-------------------|-------------------|---------------------------|  
|TM_DecisionTree|000000001|All|12939|5|  
  
 What do these results tell you? In a decision trees model, the cardinality of a particular node tells you how many immediate children that node has. The cardinality for this node is 5, meaning that the model divided the target population of potential bike buyers into 5 subgroups.  
  
 The following related query returns the children for these five subgroups, together with the distribution of attributes and values in the child nodes. Because statistics such as support, probability, and variance are stored in the nested table, `NODE_DISTRIBUTION`, this example uses the `FLATTENED` keyword to output the nested table columns.  
  
> [!NOTE]  
>  The nested table column, `SUPPORT`, must be enclosed in brackets to distinguish it from the reserved keyword of the same name.  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,  
(SELECT ATTRIBUTE_NAME, ATTRIBUTE_VALUE, [SUPPORT]  
FROM NODE_DISTRIBUTION) AS t  
FROM TM_DecisionTree.CONTENT  
WHERE [PARENT_UNIQUE_NAME] = '000000001'  
```  
  
 Example results:  
  
|NODE_NAME|NODE_CAPTION|T.ATTRIBUTE_NAME|T.ATTRIBUTE_VALUE|SUPPORT|  
|----------------|-------------------|-----------------------|------------------------|-------------|  
|00000000100|Number Cars Owned = 0|Bike Buyer|Missing|0|  
|00000000100|Number Cars Owned = 0|Bike Buyer|0|1067|  
|00000000100|Number Cars Owned = 0|Bike Buyer|1|1875|  
|00000000101|Number Cars Owned = 3|Bike Buyer|Missing|0|  
|00000000101|Number Cars Owned = 3|Bike Buyer|0|678|  
|00000000101|Number Cars Owned = 3|Bike Buyer|1|473|  
  
 From these results, you can tell that of the customers who bought a bike (`[Bike Buyer]` = 1), 1067 customers had 0 cars and 473 customers had 3 cars.  
  
###  <a name="bkmk_Query3"></a> Sample Query 3: Retrieving Subtrees from the Model  
 Suppose you wanted to discover more about the customers who did buy a bike. You can view additional detail for any of the sub-trees by using the [IsDescendant (DMX)](assetId:///d9fe7446-edb5-487b-8ea6-c9efaccf6d90) function in the query, as shown in the following example. The query returns the count of bike purchasers by retrieving leaf nodes (NODE_TYPE = 4) from the tree that contains customers who are over 42 years of age. The query restricts rows from the nested table to those where Bike Buyer = 1.  
  
```  
SELECT FLATTENED NODE_NAME, NODE_CAPTION,NODE_TYPE,  
(  
SELECT [SUPPORT] FROM NODE_DISTRIBUTION WHERE ATTRIBUTE_NAME = 'Bike Buyer' AND ATTRIBUTE_VALUE = '1'  
) AS t  
FROM TM_DecisionTree.CONTENT  
WHERE ISDESCENDANT('0000000010001')  
AND NODE_TYPE = 4  
```  
  
 Example results:  
  
|NODE_NAME|NODE_CAPTION|t.SUPPORT|  
|----------------|-------------------|---------------|  
|000000001000100|Yearly Income >= 26000 and < 42000|266|  
|00000000100010100|Total Children = 3|75|  
|0000000010001010100|Number Children At Home = 1|75|  
  
## Making Predictions using a Decision Trees Model  
 Because decision trees can be used for various tasks, including classification, regression, and even association, when you create a prediction query on a decision tree model you have many options available to you. You must understand the purpose for which the model was created to understand the results of prediction. The following query samples illustrate three different scenarios:  
  
-   Returning a prediction for a classification model, together with the probability of the prediction being correct, and then filtering the results by the probability;  
  
-   Creating a singleton query to predict associations;  
  
-   Retrieving the regression formula for a part of a decision tree where the relationship between the input and output is linear.  
  
###  <a name="bkmk_Query4"></a> Sample Query 4: Returning Predictions with Probabilities  
 The following sample query uses the decision tree model that was created in the [Basic Data Mining Tutorial](assetId:///6602edb6-d160-43fb-83c8-9df5dddfeb9c). The query passes in a new set of sample data, from the table dbo.ProspectiveBuyers in [!INCLUDE[ssSampleDBnormal](../../Topics/TopicNameContainA/tokens/ssSampleDBnormal_md.md)] DW, to predict which of the customers in the new data set will purchase a bike.  
  
 The query uses the prediction function [PredictHistogram (DMX)](assetId:///85ffc542-96e7-4f58-aaa3-34d76befcedf), which returns a nested table that contains useful information about the probabilities discovered by the model. The final WHERE clause of the query filters the results to return only those customers who are predicted as likely to buy a bike, with a probability greater than 0%.  
  
```  
SELECT  
  [TM_DecisionTree].[Bike Buyer],  
  PredictHistogram([Bike Buyer]) as Results  
From  
  [TM_DecisionTree]  
PREDICTION JOIN  
  OPENQUERY([Adventure Works DW Multidimensional 2012],  
    'SELECT  
      [FirstName],  
      [LastName],  
      [MaritalStatus],  
      [Gender],  
      [YearlyIncome],  
      [TotalChildren],  
      [NumberChildrenAtHome],  
      [HouseOwnerFlag],  
      [NumberCarsOwned]  
    FROM  
      [dbo].[ProspectiveBuyer]  
    ') AS t  
ON  
  [TM_DecisionTree].[First Name] = t.[FirstName] AND  
  [TM_DecisionTree].[Last Name] = t.[LastName] AND  
  [TM_DecisionTree].[Marital Status] = t.[MaritalStatus] AND  
  [TM_DecisionTree].[Gender] = t.[Gender] AND  
  [TM_DecisionTree].[Yearly Income] = t.[YearlyIncome] AND  
  [TM_DecisionTree].[Total Children] = t.[TotalChildren] AND  
  [TM_DecisionTree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
  [TM_DecisionTree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
  [TM_DecisionTree].[Number Cars Owned] = t.[NumberCarsOwned]  
WHERE [Bike Buyer] = 1  
AND PredictProbability([Bike Buyer]) >'.05'  
```  
  
 By default, [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] returns nested tables with the column label, **Expression**. You can change this label by aliasing the column that is returned. If you do this, the alias (in this case, **Results**) is used as both the column heading and as the value in the nested table. You must expand the nested table to see the results.  
  
 Example results with **Bike Buyer** = 1:  
  
|Bike Buyer|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|$VARIANCE|$STDEV|  
|----------------|--------------|------------------|--------------------------|---------------|------------|  
|1|2540|0.634849242045644|0.013562168281562|0|0|  
|0|1460|0.364984174579377|0.00661336932550915|0|0|  
||0|0.000166583374979177|0.000166583374979177|0|0|  
  
 If your provider does not support hierarchical rowsets, such as those shown here, you can use the FLATTENED keyword in the query to return the results as a table that contains nulls in place of the repeated column values. For more information, see [Nested Tables (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Nested-Tables--Analysis-Services---Data-Mining-.md) or [Understanding the Select Statement (DMX)](assetId:///61e97285-4a06-4434-9a40-38cde5af7c3f).  
  
###  <a name="bkmk_Query5"></a> Sample Query 5: Predicting Associations from a Decision Trees Model  
 The following sample query is based on the Association mining structure. To follow along with this example, you can add a new model to this mining structure, and select Microsoft Decision Trees as the algorithm. For more information on how to create the Association mining structure, see [Lesson 4: Building the Market Basket Scenario](assetId:///651eef38-772e-4d97-af51-075b1b27fc5a).  
  
 The following sample query is a singleton query, which you can create easily in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)] by choosing fields and then selecting values for those fields from a drop-down list.  
  
```  
SELECT PredictAssociation([DT_Association].[v Assoc Seq Line Items],3)  
FROM  
  [DT_Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Patch kit' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Expected results:  
  
|Model|  
|-----------|  
|Mountain-200|  
|Mountain Tire Tube|  
|Touring Tire Tube|  
  
 The results tell you the three best products to recommend to customers who have purchased the Patch Kit product. You can also provide multiple products as input when you make recommendations, either by typing in values, or by using the **Singleton Query Input** dialog box and adding or removing values. The following sample query shows how the multiple values are provided, upon which to make a prediction. Values are connected by a UNION clause in the SELECT statement that defines the input values.  
  
```  
SELECT PredictAssociation([DT_Association].[v Assoc Seq Line Items],3)  
From  
  [DT_Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Racing Socks' AS [Model]  
  UNION SELECT 'Women''s Mountain Shorts' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 Expected results:  
  
|Model|  
|-----------|  
|Long-Sleeve Logo Jersey|  
|Mountain-400-W|  
|Classic Vest|  
  
###  <a name="bkmk_Query6"></a> Sample Query 6: Retrieving a Regression Formula from a Decision Trees Model  
 When you create a decision tree model that contains a regression on a continuous attribute, you can use the regression formula to make predictions, or you can extract information about the regression formula. For more information about queries on regression models, see [Linear Regression Model Query Examples](../../Topics/TopicNameNotContainA/Linear-Regression-Model-Query-Examples.md).  
  
 If a decision trees model contains a mixture of regression nodes and nodes that split on discrete attributes or ranges, you can create a query that returns only the regression node. The NODE_DISTRIBUTION table contains the details of the regression formula. In this example, the columns are flattened and the NODE_DISTRIBUTION table is aliased for easier viewing. However, in this model, no regressors were found to relate Income with other continuous attributes. In such cases, [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)] returns the mean value of the attribute and the total variance in the model for that attribute.  
  
```  
SELECT FLATTENED NODE_DISTRIBUTION AS t  
FROM DT_Predict. CONTENT  
WHERE NODE_TYPE = 25  
```  
  
 Example results:  
  
|t.ATTRIBUTE_NAME|t.ATTRIBUTE_VALUE|t.SUPPORT|t.PROBABILITY|t.VARIANCE|t.VALUETYPE|  
|-----------------------|------------------------|---------------|-------------------|----------------|-----------------|  
|Yearly Income|Missing|0|0.000457142857142857|0|1|  
|Yearly Income|57220.8876687257|17484|0.999542857142857|1041275619.52776|3|  
||57220.8876687257|0|0|1041216662.54387|11|  
  
 For more information about the value types and the statistics used in regression models, see [Mining Model Content for Linear Regression Models (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Mining-Model-Content-for-Linear-Regression-Models--Analysis-Services---Data-Mining-.md).  
  
## List of Prediction Functions  
 All [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] algorithms support a common set of functions. However, the [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Decision Trees algorithm supports the additional functions listed in the following table.  
  
|||  
|-|-|  
|Prediction Function|Usage|  
|[IsDescendant](assetId:///d9fe7446-edb5-487b-8ea6-c9efaccf6d90)|Determines whether one node is a child of another node in the model.|  
|[IsInNode](assetId:///47b2114f-9ad6-45cc-9498-193ad6fa5288)|Indicates whether the specified node contains the current case.|  
|[Pre dictAdjustedProbability](assetId:///9a1e2ec5-5a37-4df6-a78e-26a495cc9301)|Returns the weighted probability.|  
|[PredictAssociation](assetId:///33eb66b5-84c6-449f-aaae-316345bc4ad5)|Predicts membership in an associative dataset.|  
|[PredictHistogram](assetId:///85ffc542-96e7-4f58-aaa3-34d76befcedf)|Returns a table of values related to the current predicted value.|  
|[PredictNodeId](assetId:///fb236645-ad7e-4c54-9c4c-1af47cad7ad5)|Returns the Node_ID for each case.|  
|[PredictProbability](assetId:///7bb7e74f-e33b-4f7b-ade8-be21ace0dbd0)|Returns probability for the predicted value.|  
|[PredictStdev](assetId:///2614aad0-f3f2-4f56-9dad-9c436f11a35f)|Returns the predicted standard deviation for the specified column.|  
|[PredictSupport](assetId:///325437d6-7cb5-4ae0-8abe-edb58fe5e90d)|Returns the support value for a specified state.|  
|[PredictVariance](assetId:///3c535237-083a-4102-bdfe-9f3c929e7b2c)|Returns the variance of a specified column.|  
  
 For a list of the functions that are common to all [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] algorithms, see [Mapping Functions to Query Types (DMX)](assetId:///e128159a-0458-43c9-bfe9-129cb6cfbe1c). For the syntax of specific functions, see [DMX Function Reference](assetId:///fadd105b-9c8e-4118-a1f7-c0518b9ad970).  
  
## See Also  
 [Data Mining Queries](../../Topics/TopicNameNotContainA/Data-Mining-Queries.md)   
 [Microsoft Decision Trees Algorithm](../../Topics/TopicNameNotContainA/Microsoft-Decision-Trees-Algorithm.md)   
 [Microsoft Decision Trees Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Decision-Trees-Algorithm-Technical-Reference.md)   
 [Mining Model Content for Decision Tree Models (Analysis Services - Data Mining)](../../Topics/TopicNameNotContainA/Mining-Model-Content-for-Decision-Tree-Models--Analysis-Services---Data-Mining-.md)