---
title: Select a Nested Table Key Column Dialog Box (Mining Structure View)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f68b89a7-17df-45f8-ba7f-b458cd9b1ec3
---
# Select a Nested Table Key Column Dialog Box (Mining Structure View)
  Use the **Select a Nested Table Key Column** dialog box to designate a column that will act as the key for the new nested table. When you exit the dialog box, a new table is added to the mining structure that contains the designated key column. You can add additional columns to the nested table by right\-clicking the structure and selecting **Add a Column**. The dialog box contains different options depending on whether you are working with an OLAP mining model or a relational mining model.  
  
## Options  
 **Source table**  
 The table on which the mining model is based.  
  
 This is only used for relational mining models.  
  
 **Source column**  
 A list of all the available columns in the source table that you can use as the key of the nested table.  
  
 This is only used for relational mining models.  
  
 **Show column types**  
 A list of available column data types. Select or clear data types to filter the list of columns in **Source column**. Only columns that match the checked data types will be shown in the **Source column** list.  
  
 This is only used for relational mining models.  
  
 **Attributes**  
 A list of attributes that you can use as the key of the nested table.  
  
 This is only used for OLAP mining models.  
  
## See Also  
 [Mining Structure View &#40;Data Mining Model Designer&#41;](../Topic/Mining%20Structure%20View%20\(Data%20Mining%20Model%20Designer\).md)  
  
  