---
title: Full-Text Index Properties (Columns Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-search
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75e52edb-0d07-4393-9345-8b5af4561e35
---
# Full-Text Index Properties (Columns Page)
  **To view or change the properties of a full\-text index**  
  
-   [Manage Full-Text Indexes](../../Topics\TopicNameNotContainA/Manage-Full-Text-Indexes.md)  
  
## UIElement List  
 **Unique index**  
 Select an index from the drop down list. The index must be a single\-key\-column, unique, non\-nullable index.  
  
 **Select the eligible columns that will be full\-text indexed**  
 The grid displays the table columns that are available for this full\-text index. Columns that are currently full\-text indexed are checked. Optionally, you can check additional columns that you want to be full\-text indexed.  
  
> [!IMPORTANT]  
>  Ensure that at least one column is checked before you click OK.  
  
|||  
|-|-|  
|**Available Columns**|The column name.|  
|**Language for Word Breaker**|The language whose word breakers and stemmers perform linguistic analysis on all full\-text indexed data.<br /><br /> For more information, see [Configure and Manage Word Breakers and Stemmers for Search](../../Topics\TopicNameNotContainA/Configure-and-Manage-Word-Breakers-and-Stemmers-for-Search.md) and [Choose a Language When Creating a Full-Text Index](../../Topics\TopicNameContainA/Choose-a-Language-When-Creating-a-Full-Text-Index.md).|  
|**Type**|The name of the table column that holds the document type of the selected column. This is a read\-only property.|  
|**Statistical Semantics**|Select whether to enable semantic indexing for the selected column. For more information, see [Semantic Search &#40;SQL Server&#41;](../Topic/Semantic%20Search%20\(SQL%20Server\).md).<br /><br /> If you select a **Language** prior to selecting **Statistical Semantics**, and the selected language does not have an associated Semantic Language Model, then the **Statistical Semantics** checkbox is disabled. If you select **Statistical Semantics** prior to selecting a **Language**, the languages available in the drop\-down combo box will be restricted to those for which there is Semantic Language Model support.|  
  
## See Also  
 [Populate Full-Text Indexes](../../Topics\TopicNameNotContainA/Populate-Full-Text-Indexes.md)  
  
  