---
title: Customize Mining Models and Structure
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
ms.assetid: 32c17b4f-e090-45f9-b3aa-ffa7084e928e
---
# Customize Mining Models and Structure
  After you have selected an algorithm that meets your business needs, you can customize the mining model in the following ways to potentially improve results.  
  
-   Use different columns of data in the model, or change the usage, content type, or discretization method for the columns.  
  
-   Create filters on the mining model to restrict the data used in training the model.  
  
-   Change the algorithm that was used to analyze data.  
  
-   Set algorithm parameters to control thresholds, tree splits, and other important conditions.  
  
 This topic describes these options.  
  
## Changing Data Used by the Model  
 The decisions that you make about which columns of data to use in the model, and how to use and process that data, greatly affect the results of analysis. The following topics provide information to help you understand these choices.  
  
### Using Feature Selection  
 Most data mining algorithms in [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/includes/ssASnoversion_md.md)] use a process called *feature selection* to select only the most useful attributes for addition to a model. Reducing the number of columns and attributes can improve performance and the quality of the model. The feature selection methods that are available differ depending on the algorithm that you choose.  
  
 [Feature Selection &#40;Data Mining&#41;](../../Topics/TopicNameNotContainA/Feature-Selection--Data-Mining-.md).  
  
### Changing Usage  
 You can change which columns are included in a mining model and how each column is used. If you do not get the results you expect, you should example the columns you used as input, and ask yourself whether the columns are a good choice, and whether there is anything you can do to improve the handling of data, including:  
  
-   Identifying categorical variables that have mistakenly labeled as numbers.  
  
-   Adding categories to collapse the number of attributes and make it easier t find correlations.  
  
-   Changing the way that numbers are binned, or discretized.  
  
-   Removing columns that have a lot of unique values, or columns that are really reference data and not useful for analysis, such as addresses or middle names.  
  
 You don’t need to physically remove columns from the mining structure; you can just flag the column as **Ignore**. The column is removed from the mining model, but can still be used by other mining models in the structure, ore referenced in a drillthrough query.  
  
### Creating Aliases for Model Columns  
 When [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/includes/ssASnoversion_md.md)] creates the mining model, it uses the same column names that are in the mining structure. You can add an alias to any column in the mining model. This might make it easier to understand the column contents or usage, or make the name shorter for convenience in creating queries. Aliases are also helpful when you want to create a copy of a column and name it something descriptive.  
  
 You create an alias by editing the **Name** property of the mining model column. [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/includes/ssASnoversion_md.md)] continues to use the original name as the ID of the column, and the new value that you type for **Name** becomes the column alias, and appears in the grid in parentheses next to the column usage.  
  
 ![aliases on mining model columns](../../Topics/TopicNameNotContainA/media/ModelColumnAlias-Income.gif "ModelColumnAlias-Income")  
  
 The graphic shows related models that have multiple copies of a mining structure column, all related to Income. Each copy of the structure column has been discretized in a different way. The models in the diagram each use a different column from the mining structure; however, for convenience in comparing the columns across the models, the column in each model has been renamed to [**Income**].  
  
### Adding Filters  
 You can add a filter to a mining model. A filter is a set of WHERE conditions that restrict the data in the model cases to some subset. The filter is used when training the model, and can optionally be used when you test the model or create accuracy charts.  
  
 By adding filters, you can reuse mining structures but create models based on very different subsets of the data. Or, you can simply use filters to eliminate certain rows and improve the quality of analysis.  
  
 For more information, see [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](../../Topics/TopicNameNotContainA/Filters-for-Mining-Models--Analysis-Services---Data-Mining-.md).  
  
## Changing the Algorithm  
 Although new models that you add to a mining structure share the same data set, you can get different results by using a different algorithm (if the data supports it), or by changing the parameters for the algorithm. You can also set modeling flags.  
  
 The choice of algorithm determines what kind of results you will get. For general information about how a specific algorithm works, or the business scenarios where you would benefit from using a particular algorithm, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../../Topics/TopicNameNotContainA/Data-Mining-Algorithms--Analysis-Services---Data-Mining-.md).  
  
 See the technical reference topic for each algorithm for a description of the requirements and restrictions, as well as detailed information about the customizations that each algorithm supports.  
  
|||  
|-|-|  
|[Microsoft Decision Trees Algorithm](../../Topics/TopicNameNotContainA/Microsoft-Decision-Trees-Algorithm.md)|[Microsoft Time Series Algorithm](../../Topics/TopicNameNotContainA/Microsoft-Time-Series-Algorithm.md)|  
|[Microsoft Clustering Algorithm](../../Topics/TopicNameNotContainA/Microsoft-Clustering-Algorithm.md)|[Microsoft Neural Network Algorithm](../../Topics/TopicNameNotContainA/Microsoft-Neural-Network-Algorithm.md)|  
|[Microsoft Naive Bayes Algorithm](../../Topics/TopicNameNotContainA/Microsoft-Naive-Bayes-Algorithm.md)|[Microsoft Logistic Regression Algorithm](../../Topics/TopicNameNotContainA/Microsoft-Logistic-Regression-Algorithm.md)|  
|[Microsoft Association Algorithm](../../Topics/TopicNameNotContainA/Microsoft-Association-Algorithm.md)|[Microsoft Linear Regression Algorithm](../../Topics/TopicNameNotContainA/Microsoft-Linear-Regression-Algorithm.md)|  
|[Microsoft Sequence Clustering Algorithm](../../Topics/TopicNameNotContainA/Microsoft-Sequence-Clustering-Algorithm.md)||  
  
## Customizing Algorithm Parameters  
 Each algorithm supports parameters that you can use to customize the behavior of the algorithm and fine-tune the results of your model. For a description of how to use each parameter, see the following topics:  
  
 The topic for each algorithm type also lists the prediction functions that can be used with models based on that algorithm.  
  
|Property name|Applies to|  
|-------------------|----------------|  
|AUTO_DETECT_PERIODICITY|[Microsoft Time Series Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Time-Series-Algorithm-Technical-Reference.md)|  
|CLUSTER_COUNT|[Microsoft Clustering Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Clustering-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Sequence Clustering Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Sequence-Clustering-Algorithm-Technical-Reference.md)|  
|CLUSTER_SEED|[Microsoft Clustering Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Clustering-Algorithm-Technical-Reference.md)|  
|CLUSTERING_METHOD|[Microsoft Clustering Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Clustering-Algorithm-Technical-Reference.md)|  
|COMPLEXITY_PENALTY|[Microsoft Decision Trees Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Decision-Trees-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Time Series Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Time-Series-Algorithm-Technical-Reference.md)|  
|FORCE_REGRESSOR|[Microsoft Decision Trees Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Decision-Trees-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Linear Regression Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Linear-Regression-Algorithm-Technical-Reference.md)<br /><br /> [Modeling Flags &#40;Data Mining&#41;](../../Topics/TopicNameNotContainA/Modeling-Flags--Data-Mining-.md)|  
|FORECAST_METHOD|[Microsoft Time Series Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Time-Series-Algorithm-Technical-Reference.md)|  
|HIDDEN_NODE_RATIO|[Microsoft Neural Network Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Neural-Network-Algorithm-Technical-Reference.md)|  
|HISTORIC_MODEL_COUNT|[Microsoft Time Series Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Time-Series-Algorithm-Technical-Reference.md)|  
|HISTORICAL_MODEL_GAP|[Microsoft Time Series Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Time-Series-Algorithm-Technical-Reference.md)|  
|HOLDOUT_PERCENTAGE|[Microsoft Logistic Regression Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Logistic-Regression-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Neural Network Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Neural-Network-Algorithm-Technical-Reference.md)<br /><br /> Note: This parameter is different from the holdout percentage value that applies to a mining structure.|  
|HOLDOUT_SEED|[Microsoft Logistic Regression Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Logistic-Regression-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Neural Network Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Neural-Network-Algorithm-Technical-Reference.md)<br /><br /> Note: This parameter is different from the holdout seed value that applies to a mining structure.|  
|INSTABILITY_SENSITIVITY|[Microsoft Time Series Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Time-Series-Algorithm-Technical-Reference.md)|  
|MAXIMUM_INPUT_ATTRIBUTES|[Microsoft Clustering Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Clustering-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Decision Trees Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Decision-Trees-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Linear Regression Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Linear-Regression-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Naive Bayes Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Naive-Bayes-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Neural Network Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Neural-Network-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Logistic Regression Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Logistic-Regression-Algorithm-Technical-Reference.md)|  
|MAXIMUM_ITEMSET_COUNT|[Microsoft Association Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Association-Algorithm-Technical-Reference.md)|  
|MAXIMUM_ITEMSET_SIZE|[Microsoft Association Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Association-Algorithm-Technical-Reference.md)|  
|MAXIMUM_OUTPUT_ATTRIBUTES|[Microsoft Decision Trees Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Decision-Trees-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Linear Regression Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Linear-Regression-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Logistic Regression Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Logistic-Regression-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Naive Bayes Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Naive-Bayes-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Neural Network Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Neural-Network-Algorithm-Technical-Reference.md)|  
|MAXIMUM_SEQUENCE_STATES|[Microsoft Sequence Clustering Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Sequence-Clustering-Algorithm-Technical-Reference.md)|  
|MAXIMUM_SERIES_VALUE|[Microsoft Time Series Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Time-Series-Algorithm-Technical-Reference.md)|  
|MAXIMUM_STATES|[Microsoft Clustering Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Clustering-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Neural Network Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Neural-Network-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Sequence Clustering Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Sequence-Clustering-Algorithm-Technical-Reference.md)|  
|MAXIMUM_SUPPORT|[Microsoft Association Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Association-Algorithm-Technical-Reference.md)|  
|MINIMUM_IMPORTANCE|[Microsoft Association Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Association-Algorithm-Technical-Reference.md)|  
|MINIMUM_ITEMSET_SIZE|[Microsoft Association Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Association-Algorithm-Technical-Reference.md)|  
|MINIMUM_DEPENDENCY_PROBABILITY|[Microsoft Naive Bayes Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Naive-Bayes-Algorithm-Technical-Reference.md)|  
|MINIMUM_PROBABILITY|[Microsoft Association Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Association-Algorithm-Technical-Reference.md)|  
|MINIMUM_SERIES_VALUE|[Microsoft Time Series Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Time-Series-Algorithm-Technical-Reference.md)|  
|MINIMUM_SUPPORT|[Microsoft Association Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Association-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Clustering Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Clustering-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Decision Trees Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Decision-Trees-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Sequence Clustering Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Sequence-Clustering-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Time Series Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Time-Series-Algorithm-Technical-Reference.md)|  
|MISSING_VALUE_SUBSTITUTION|[Microsoft Time Series Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Time-Series-Algorithm-Technical-Reference.md)|  
|MODELLING_CARDINALITY|[Microsoft Clustering Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Clustering-Algorithm-Technical-Reference.md)|  
|PERIODICITY_HINT|[Microsoft Time Series Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Time-Series-Algorithm-Technical-Reference.md)|  
|PREDICTION_SMOOTHING|[Microsoft Time Series Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Time-Series-Algorithm-Technical-Reference.md)|  
|SAMPLE_SIZE|[Microsoft Clustering Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Clustering-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Logistic Regression Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Logistic-Regression-Algorithm-Technical-Reference.md)<br /><br /> [Microsoft Neural Network Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Neural-Network-Algorithm-Technical-Reference.md)|  
|SCORE_METHOD|[Microsoft Decision Trees Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Decision-Trees-Algorithm-Technical-Reference.md)|  
|SPLIT_METHOD|[Microsoft Decision Trees Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Decision-Trees-Algorithm-Technical-Reference.md)|  
|STOPPING_TOLERANCE|[Microsoft Clustering Algorithm Technical Reference](../../Topics/TopicNameNotContainA/Microsoft-Clustering-Algorithm-Technical-Reference.md)|  
  
## See Also  
 [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](../../Topics/TopicNameNotContainA/Data-Mining-Algorithms--Analysis-Services---Data-Mining-.md)   
 [Physical Architecture &#40;Analysis Services - Data Mining&#41;](../../Topics/TopicNameNotContainA/Physical-Architecture--Analysis-Services---Data-Mining-.md)  
  
  