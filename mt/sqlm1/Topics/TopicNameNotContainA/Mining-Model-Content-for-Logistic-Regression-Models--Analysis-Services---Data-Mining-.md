---
title: Mining Model Content for Logistic Regression Models (Analysis Services - Data Mining)
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
ms.assetid: 69cc0b86-e8bc-4d6c-903e-85724f5c0396
---
# Mining Model Content for Logistic Regression Models (Analysis Services - Data Mining)
  This topic describes mining model content that is specific to models that use the Microsoft Logistic Regression algorithm. For an explanation of how to interpret statistics and structure shared by all model types, and general definitions of terms related to mining model content, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Model%20Content%20\(Analysis%20Services%20-%20Data%20Mining\).md).  
  
## Understanding the Structure of a Logistic Regression Model  
 A logistic regression model is created by using the Microsoft Neural Network algorithm with parameters that constrain the model to eliminate the hidden node. Therefore, the overall structure of a logistic regression model is almost identical to that of a neural network: each model has a single parent node that represents the model and its metadata, and a special marginal statistics node \(NODE\_TYPE \= 24\) that provides descriptive statistics about the inputs used in the model.  
  
 Additionally, the model contains a subnetwork \(NODE\_TYPE \= 17\) for each predictable attribute. Just like in a neural network model, each subnetwork always contains two branches: one for the input layer, and another branch that contains the hidden layer \(NODE\_TYPE \= 19\) and the output layer \(NODE\_TYPE \= 20\) for the network. The same subnetwork may be used for multiple attributes if they are specified as predict\-only. Predictable attributes that are also inputs may not appear in the same subnetwork.  
  
 However, in a logistic regression model, the node that represents the hidden layer is empty, and has no children. Therefore the model contains nodes that represent individual outputs \(NODE\_TYPE \= 23\) and individual inputs \(NODE\_TYPE \= 21\) but no individual hidden nodes.  
  
 ![structure of content for logisitc regression model](../../Images\Image\ImageNotContaina/skt_ModelContentStructure_LogRegc.gif "skt_ModelContentStructure_LogRegc")  
  
 By default, a logistic regression model is displayed in the **Microsoft Neural Network Viewer**. With this custom viewer, you can filter on input attributes and their values, and graphically see how they affect the outputs. The tooltips in the viewer show you the probability and lift associated with each pair of inputs and output values. For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](../../Topics\TopicNameContainA/Browse-a-Model-Using-the-Microsoft-Neural-Network-Viewer.md).  
  
 To explore the structure of the inputs and subnetworks, and to see detailed statistics, you can use the Microsoft Generic Content Tree viewer. You can click on any node to expand it and see the child nodes, or view the weights and other statistics contained in the node.  
  
## Model Content for a Logistic Regression Model  
 This section provides detail and examples only for those columns in the mining model content that have particular relevance for logistic regression. The model content is almost identical to that of a neural network model, but descriptions that apply to neural network models may be repeated in this table for convenience.  
  
 For information about general\-purpose columns in the schema rowset, such as MODEL\_CATALOG and MODEL\_NAME, that are not described here, or for explanations of mining model terminology, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Model%20Content%20\(Analysis%20Services%20-%20Data%20Mining\).md).  
  
 MODEL\_CATALOG  
 Name of the database where the model is stored.  
  
 MODEL\_NAME  
 Name of the model.  
  
 ATTRIBUTE\_NAME  
 The names of the attribute that corresponds to this node.  
  
|Node|Content|  
|----------|-------------|  
|Model root|Blank|  
|Marginal statistics|Blank|  
|Input layer|Blank|  
|Input node|Input attribute name|  
|Hidden layer|Blank|  
|Output layer|Blank|  
|Output node|Output attribute name|  
  
 NODE\_NAME  
 The name of the node. Currently, this column contains the same value as NODE\_UNIQUE\_NAME, though this may change in future releases.  
  
 NODE\_UNIQUE\_NAME  
 The unique name of the node.  
  
 For more information about how the names and IDs provide structural information about the model, see the section, [Using Node Names and IDs](#bkmk_NodeIDs).  
  
 NODE\_TYPE  
 A logistic regression model outputs the following node types:  
  
|Node Type ID|Description|  
|------------------|-----------------|  
|1|Model.|  
|17|Organizer node for the subnetwork.|  
|18|Organizer node for the input layer.|  
|19|Organizer node for the hidden layer. The hidden layer is empty.|  
|20|Organizer node for the output layer.|  
|21|Input attribute node.|  
|23|Output attribute node.|  
|24|Marginal statistics node.|  
  
 NODE\_CAPTION  
 A label or a caption associated with the node. In logistic regression models, always blank.  
  
 CHILDREN\_CARDINALITY  
 An estimate of the number of children that the node has.  
  
|Node|Content|  
|----------|-------------|  
|Model root|Indicates the count of child nodes, which includes at least 1 network, 1 required marginal node, and 1 required input layer. For example, if the value is 5, there are 3 subnetworks.|  
|Marginal statistics|Always 0.|  
|Input layer|Indicates the number of input attribute\-values pairs that were used by the model.|  
|Input node|Always 0.|  
|Hidden layer|In a logistic regression model, always 0.|  
|Output layer|Indicates the number of output values.|  
|Output node|Always 0.|  
  
 PARENT\_UNIQUE\_NAME  
 The unique name of the node's parent. NULL is returned for any nodes at the root level.  
  
 For more information about how the names and IDs provide structural information about the model, see the section, [Using Node Names and IDs](#bkmk_NodeIDs).  
  
 NODE\_DESCRIPTION  
 A user\-friendly description of the node.  
  
|Node|Content|  
|----------|-------------|  
|Model root|Blank|  
|Marginal statistics|Blank|  
|Input layer|Blank|  
|Input node|Input attribute name|  
|Hidden layer|Blank|  
|Output layer|Blank|  
|Output node|If the output attribute is continuous, contains the name of the output attribute.<br /><br /> If the output attribute is discrete or discretized, contains the name of the attribute and the value.|  
  
 NODE\_RULE  
 An XML description of the rule that is embedded in the node.  
  
|Node|Content|  
|----------|-------------|  
|Model root|Blank|  
|Marginal statistics|Blank|  
|Input layer|Blank|  
|Input node|An XML fragment containing the same information as the NODE\_DESCRIPTION column.|  
|Hidden layer|Blank|  
|Output layer|Blank|  
|Output node|An XML fragment containing the same information as the NODE\_DESCRIPTION column.|  
  
 MARGINAL\_RULE  
 For logistic regression models, always blank.  
  
 NODE\_PROBABILITY  
 The probability associated with this node. For logistic regression models, always 0.  
  
 MARGINAL\_PROBABILITY  
 The probability of reaching the node from the parent node. For logistic regression models, always 0.  
  
 NODE\_DISTRIBUTION  
 A nested table that contains statistical information for the node. For detailed information about the contents of this table for each node type, see the section, Understanding the NODE\_DISTRIBUTION Table, in [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Model%20Content%20for%20Neural%20Network%20Models%20\(Analysis%20Services%20-%20Data%20Mining\).md).  
  
 NODE\_SUPPORT  
 For logistic regression models, always 0.  
  
> [!NOTE]  
>  Support probabilities are always 0 because the output of this model type is not probabilistic. The only thing that is meaningful for the algorithm is the weights; therefore, the algorithm does not compute probability, support, or variance.  
  
 To get information about the support in the training cases for specific values, see the marginal statistics node.  
  
 MSOLAP\_MODEL\_COLUMN  
 |Node|Content|  
|----------|-------------|  
|Model root|Blank|  
|Marginal statistics|Blank|  
|Input layer|Blank|  
|Input node|Input attribute name.|  
|Hidden layer|Blank|  
|Output layer|Blank|  
|Output node|Input attribute name.|  
  
 MSOLAP\_NODE\_SCORE  
 In logistic regression models, always 0.  
  
 MSOLAP\_NODE\_SHORT\_CAPTION  
 In logistic regression models, always blank.  
  
##  <a name="bkmk_NodeIDs"></a> Using Node Names and IDs  
 The naming of the nodes in a logistic regression model provides additional information about the relationships between nodes in the model. The following table shows the conventions for the IDs that are assigned to nodes in each layer.  
  
|Node Type|Convention for node ID|  
|---------------|----------------------------|  
|Model root \(1\)|00000000000000000.|  
|Marginal statistics node \(24\)|10000000000000000|  
|Input layer \(18\)|30000000000000000|  
|Input node \(21\)|Starts at 60000000000000000|  
|Subnetwork \(17\)|20000000000000000|  
|Hidden layer \(19\)|40000000000000000|  
|Output layer \(20\)|50000000000000000|  
|Output node \(23\)|Starts at 80000000000000000|  
  
 You can use these IDs to determine how output attributes are related to specific input layer attributes, by viewing the NODE\_DISTRIBUTION table of the output node. Each row in that table contains an ID that points back to a specific input attribute node. The NODE\_DISTRIBUTION table also contains the coefficient for that input\-output pair.  
  
## See Also  
 [Microsoft Logistic Regression Algorithm](../../Topics\TopicNameNotContainA/Microsoft-Logistic-Regression-Algorithm.md)   
 [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Model%20Content%20for%20Neural%20Network%20Models%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Logistic Regression Model Query Examples](../../Topics\TopicNameNotContainA/Logistic-Regression-Model-Query-Examples.md)   
 [Microsoft Logistic Regression Algorithm Technical Reference](../../Topics\TopicNameNotContainA/Microsoft-Logistic-Regression-Algorithm-Technical-Reference.md)  
  
  