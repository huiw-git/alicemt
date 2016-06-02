---
title: Create Relationships
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6ebd305f-ffd2-4a1d-b24c-e28c151b94f5
---
# Create Relationships
  Use the **Create Relationships** dialog box to edit mappings between the source columns and the lookup table columns that you configured in the Fuzzy Lookup Transformation Editor, the Lookup Transformation Editor, and the Term Lookup Transformation Editor.  
  
> [!NOTE]  
>  The **Create Relationships** dialog box displays only the **Input Column** and **Lookup Column** lists when invoked from the Term Lookup Transformation Editor.  
  
 To learn more about the transformations that use the **Create Relationships** dialog box, see [Fuzzy Lookup Transformation](../../Topics\TopicNameNotContainA/Fuzzy-Lookup-Transformation.md), [Lookup Transformation](../../Topics\TopicNameNotContainA/Lookup-Transformation.md), and [Term Lookup Transformation](../../Topics\TopicNameNotContainA/Term-Lookup-Transformation.md).  
  
## Options  
 **Input Column**  
 Select from the list of available input columns.  
  
 **Lookup Column**  
 Select from the list of available lookup columns.  
  
 **Mapping Type**  
 Select fuzzy or exact matching.  
  
 When you use fuzzy matching, rows are considered duplicates if they are sufficiently similar across all columns that have a fuzzy match type. To obtain better results from fuzzy matching, you can specify that some columns should use exact matching instead of fuzzy matching. For example, if you know that a certain column contains no errors or inconsistencies, you can specify exact matching on that column, so that only rows which contain identical values in this column are considered as possible duplicates. This increases the accuracy of fuzzy matching on other columns.  
  
 **Comparison Flags**  
 For information about the string comparison options, see [Comparing String Data](../../Topics\TopicNameNotContainA/Comparing-String-Data.md).  
  
 **Minimum Similarity**  
 Set the similarity threshold at the column level by using the slider. The closer the value is to 1, the more the lookup value must resemble the source value to qualify as a match. Increasing the threshold can improve the speed of matching because fewer candidate records have to be considered.  
  
 **Similarity Output Alias**  
 Specify the name for a new output column that contains the similarity scores for the selected column. If you leave this value empty, the output column is not created.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Fuzzy Lookup Transformation Editor &#40;Columns Tab&#41;](../Topic/Fuzzy%20Lookup%20Transformation%20Editor%20\(Columns%20Tab\).md)   
 [Lookup Transformation Editor &#40;Columns Page&#41;](../Topic/Lookup%20Transformation%20Editor%20\(Columns%20Page\).md)   
 [Term Lookup Transformation Editor &#40;Term Lookup Tab&#41;](../Topic/Term%20Lookup%20Transformation%20Editor%20\(Term%20Lookup%20Tab\).md)  
  
  