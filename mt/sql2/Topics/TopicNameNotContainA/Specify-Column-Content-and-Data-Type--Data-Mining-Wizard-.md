---
title: Specify Column Content and Data Type (Data Mining Wizard)
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0634be64-4c38-4381-9b19-fe9a5889306c
---
# Specify Column Content and Data Type (Data Mining Wizard)
  Use the **Specify Column Content and Data Type** page to specify the usage and data type for each column that you selected on the previous page of the wizard. If you want to ignore the column, click **Back** to return to the page **Specify the Training Data**, and clear all checkboxes.  
  
 The usage of a column indicates how the data will be used in the model. A column can be used as a key to identify a series, as an input value to use in analysis, or as the value that you want to predict. Columns can be used for both prediction and input.  
  
 The data type specifies additional detail about the type of data that is contained in the column, and how the data will be used during training. Some content types require a specific data type, and vice versa. You might also need to specify a particular data type depending on the algorithm that you use when you create a mining model. For information about content types and data types in mining models and structures, see [Content Types &#40;Data Mining&#41;](../../Topics/TopicNameNotContainA/Content-Types--Data-Mining-.md).  
  
 **For More Information:** [Mining Structures &#40;Analysis Services - Data Mining&#41;](../../Topics/TopicNameNotContainA/Mining-Structures--Analysis-Services---Data-Mining-.md), [Mining Model Columns](../../Topics/TopicNameNotContainA/Mining-Model-Columns.md), [Data Mining Wizard &#40;Analysis Services - Data Mining&#41;](../../Topics/TopicNameNotContainA/Data-Mining-Wizard--Analysis-Services---Data-Mining-.md), [Create a Relational Mining Structure](../../Topics/TopicNameContainA/Create-a-Relational-Mining-Structure.md)  
  
## Options  
 **Mining model structure**  
 Displays the columns from the views and nested tables that you selected on the previous page of the wizard.  
  
 **Columns**  
 Lists the columns.  
  
 **Content type**  
 Specify the content type for the column. If you specified that the column is a key on the previous page of the wizard, the following values are available:  
  
|Option|Description|  
|------------|-----------------|  
|Key|Specify that the column contains a unique identifier for the case series.|  
|Key Sequence|Specify that the column contains a sequence identifier.|  
|Key Time|Specify that the column contains a date or other unique continuous number that is used to identify a date or time series.|  
  
 If you selected the column as a non-key column, the following values are available, depending on the data type:  
  
|Option|Description|  
|------------|-----------------|  
|Continuous|Specify that the column contains continuous numeric values.|  
|Discretized|Specify that the column contains numeric values that either have been discretized, or can be treated as discrete values.|  
|Discrete|Specify that the column contains text or other nonnumeric values.|  
  
 **Data type**  
 Specify the data type for the column.  
  
 The following values are available:  
  
-   **Boolean**  
  
-   **Date**  
  
-   **Double**  
  
-   **Long**  
  
-   **Text**  
  
 **Detect**  
 Analyze a sample of data in all numeric columns. Replaces specified **Content Type** values with a recommended content type.  
  
## See Also  
 [Data Mining Wizard F1 Help &#40;Analysis Services - Data Mining&#41;](../../Topics/TopicNameNotContainA/Data-Mining-Wizard-F1-Help--Analysis-Services---Data-Mining-.md)   
 [Suggest Related Columns &#40;Data Mining Wizard&#41;](../../Topics/TopicNameNotContainA/Suggest-Related-Columns--Data-Mining-Wizard-.md)   
 [Specify Table Types &#40;Data Mining Wizard&#41;](../../Topics/TopicNameNotContainA/Specify-Table-Types--Data-Mining-Wizard-.md)   
 [Specify the Column's Content and Data Type &#40;Data Mining Wizard&#41;](../../Topics/TopicNameNotContainA/Specify-the-Column-s-Content-and-Data-Type--Data-Mining-Wizard-.md)  
  
  