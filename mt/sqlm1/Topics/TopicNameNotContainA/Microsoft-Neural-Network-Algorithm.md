---
title: Microsoft Neural Network Algorithm
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
ms.assetid: 61eb4861-8a6a-4214-a4b8-1dd278ad7a68
---
# Microsoft Neural Network Algorithm
  The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Neural Network algorithm is an implementation of the popular and adaptable neural network architecture for machine learning.  The algorithm works by testing each possible state of the input attribute against each possible state of the predictable attribute, and calculating probabilities for each combination based on the training data. You can use these probabilities for both classification or regression tasks, to predict an outcome  based on some input attributes. A neural network can also be used for association analysis.  
  
 When you create a mining model using the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Neural Network algorithm, you can include multiple outputs, and the algorithm will create multiple networks. The number of networks contained in a single mining model contains depends on the number of states \(or attribute values\) in the input columns, as well as the number of predictable columns that the mining model uses and the number of states in those columns.  
  
## Example  
 The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Neural Network algorithm is useful for analyzing complex input data, such as from a manufacturing or commercial process, or business problems for which a significant quantity of training data is available but for which rules cannot be easily derived by using other algorithms.  
  
 Suggested scenarios for using the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Neural Network algorithm include the following:  
  
-   Marketing and promotion analysis, such as measuring the success of a direct mail promotion or a radio advertising campaign  
  
-   Predicting stock movement, currency fluctuation, or other highly fluid financial information from historical data  
  
-   Analyzing manufacturing and industrial processes  
  
-   Text mining  
  
-   Any prediction model that analyzes complex relationships between many inputs and relatively fewer outputs  
  
## How the Algorithm Works  
 The [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Neural Network algorithm creates a network that is composed of up to three layers of nodes \(sometimes called *neurons*\). These layers are the *input layer*, the *hidden layer*, and the *output layer*.  
  
 **Input layer:** Input nodes define all the input attribute values for the data mining model, and their probabilities.  
  
 **Hidden layer:** Hidden nodes receive inputs from input nodes and provide outputs to output nodes. The hidden layer is where the various probabilities of the inputs are assigned weights. A weight describes the relevance or importance of a particular input to the hidden node. The greater the weight that is assigned to an input, the more important the value of that input is. Weights can be negative, which means that the input can inhibit, rather than favor, a specific result.  
  
 **Output layer:** Output nodes represent predictable attribute values for the data mining model.  
  
 For a detailed explanation of how the input, hidden, and output layers are constructed and scored, see [Microsoft Neural Network Algorithm Technical Reference](../../Topics\TopicNameNotContainA/Microsoft-Neural-Network-Algorithm-Technical-Reference.md).  
  
## Data Required for Neural Network Models  
 A neural network model must contain a key column, one or more input columns, and one or more predictable columns.  
  
 Data mining models that use the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Neural Network algorithm are heavily influenced by the values that you specify for the parameters that are available to the algorithm. The parameters define how data is sampled, how data is distributed or expected to be distributed in each column, and when feature selection is invoked to limit the values that are used in the final model.  
  
 For more information about setting parameters to customize model behavior, see [Microsoft Neural Network Algorithm Technical Reference](../../Topics\TopicNameNotContainA/Microsoft-Neural-Network-Algorithm-Technical-Reference.md).  
  
## Viewing a Neural Network Model  
 To work with the data and see how the model correlates inputs with outputs, you can use the **Microsoft Neural Network Viewer**. With this custom viewer, you can filter on input attributes and their values, and see graphs that show how they affect the outputs. Tooltips in the viewer show the probability and lift associated with each pair of input and output values. For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](../../Topics\TopicNameContainA/Browse-a-Model-Using-the-Microsoft-Neural-Network-Viewer.md).  
  
 The easiest way to explore the structure of the model is to use the **Microsoft Generic Content Tree Viewer**. You can view the inputs, outputs, and networks created by the model, and click on any node to expand it and see statistics related to the input, output, or hidden layer nodes. For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](../../Topics\TopicNameContainA/Browse-a-Model-Using-the-Microsoft-Generic-Content-Tree-Viewer.md).  
  
## Creating Predictions  
 After the model has been processed, you can use the network and the weights stored within each node to make predictions. A neural network model supports regression, association, and classification analysis, Therefore, the meaning of each prediction might be different. You can also query the model itself, to review the correlations that were found and retrieve related statistics. For examples of how to create queries against a neural network model, see [Neural Network Model Query Examples](../../Topics\TopicNameNotContainA/Neural-Network-Model-Query-Examples.md).  
  
 For general information about how to create a query on a data mining model, see [Data Mining Queries](../../Topics\TopicNameNotContainA/Data-Mining-Queries.md).  
  
## Remarks  
  
-   Does not support drillthrough or data mining dimensions. This is because the structure of the nodes in the mining model does not necessarily correspond directly to the underlying data.  
  
-   Does not support the creation of models in Predictive Model Markup Language \(PMML\) format.  
  
-   Supports the use of OLAP mining models.  
  
-   Does not support the creation of data mining dimensions.  
  
## See Also  
 [Microsoft Neural Network Algorithm Technical Reference](../../Topics\TopicNameNotContainA/Microsoft-Neural-Network-Algorithm-Technical-Reference.md)   
 [Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;](../Topic/Mining%20Model%20Content%20for%20Neural%20Network%20Models%20\(Analysis%20Services%20-%20Data%20Mining\).md)   
 [Neural Network Model Query Examples](../../Topics\TopicNameNotContainA/Neural-Network-Model-Query-Examples.md)   
 [Microsoft Logistic Regression Algorithm](../../Topics\TopicNameNotContainA/Microsoft-Logistic-Regression-Algorithm.md)  
  
  