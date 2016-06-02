---
title: Save Data Mining Query Result Dialog Box (Mining Model Prediction View)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 112fb527-7466-4fd4-9cf1-75596135648f
---
# Save Data Mining Query Result Dialog Box (Mining Model Prediction View)
  Use the **Save Data Mining Query Result** dialog box to save the results of a data mining query to a new table.  
  
 The new table will be created in the database defined by the data source.  
  
## Options  
 **Data Source**  
 Select a data source from the current project. If the correct data source does not exist, click **New** to create a new data source.  
  
 **New**  
 Opens the **Data Source Wizard**.  
  
 **Table Name**  
 Type a name for the new table.  
  
 **Overwrite if exists**  
 Select this option if you want to overwrite an existing table with the same name.  
  
 Overwriting the existing table is required if any of the following is true:  
  
-   You added columns to the prediction query.  
  
-   You changed the names or data types of any columns in the prediction query.  
  
-   You ran an ALTER statement on the destination table.  
  
 If multiple columns have the same name \(for example, several derived columns might have the default column name **Expression**\), you must create an alias for each column with a duplicate name. If the columns do not have unique names, an error will be raised when the designer tries to save the results to SQL Server, because columns in a table must have unique names.  
  
 **Add to DSV**  
 \(Optional\) Select a data source view contained in the project if you want to add the table to an existing data source.  
  
 This option is useful if you want to keep all related tables for a model—such as training data, prediction source data, and query results—in the same data source.  
  
## See Also  
 [Prediction Query Builder &#40;Data Mining&#41;](../Topic/Prediction%20Query%20Builder%20\(Data%20Mining\).md)   
 [Data Mining Query Tools](../../Topics\TopicNameNotContainA/Data-Mining-Query-Tools.md)   
 [Data Mining Extensions &#40;DMX&#41; Statement Reference](../Topic/Data%20Mining%20Extensions%20\(DMX\)%20Statement%20Reference.md)  
  
  