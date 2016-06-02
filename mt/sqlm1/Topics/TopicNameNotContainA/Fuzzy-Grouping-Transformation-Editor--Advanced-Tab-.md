---
title: Fuzzy Grouping Transformation Editor (Advanced Tab)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dd820d75-b8a7-4515-aea4-3553ba5b442e
---
# Fuzzy Grouping Transformation Editor (Advanced Tab)
  Use the **Advanced** tab of the **Fuzzy Grouping Transformation Editor** dialog box to specify input and output columns, set similarity thresholds, and define delimiters.  
  
> [!NOTE]  
>  The **Exhaustive** and the **MaxMemoryUsage** properties of the Fuzzy Grouping transformation are not available in the **Fuzzy Grouping Transformation Editor**, but can be set by using the **Advanced Editor**. For more information on these properties, see the Fuzzy Grouping Transformation section of [Transformation Custom Properties](../../Topics\TopicNameNotContainA/Transformation-Custom-Properties.md).  
  
 To learn more about the Fuzzy Grouping transformation, see [Fuzzy Grouping Transformation](../../Topics\TopicNameNotContainA/Fuzzy-Grouping-Transformation.md).  
  
## Options  
 **Input key column name**  
 Specify the name of an output column that contains the unique identifier for each input row. The **\_key\_in** column has a value that uniquely identifies each row.  
  
 **Output key column name**  
 Specify the name of an output column that contains the unique identifier for the canonical row of a group of duplicate rows. The **\_key\_out** column corresponds to the **\_key\_in** value of the canonical data row.  
  
 **Similarity score column name**  
 Specify a name for the column that contains the similarity score. The similarity score is a value between 0 and 1 that indicates the similarity of the input row to the canonical row. The closer the score is to 1, the more closely the row matches the canonical row.  
  
 **Similarity threshold**  
 Set the similarity threshold by using the slider. The closer the threshold is to 1, the more the rows must resemble each other to qualify as duplicates. Increasing the threshold can improve the speed of matching because fewer candidate records have to be considered.  
  
 **Token delimiters**  
 The transformation provides a default set of delimiters for tokenizing data, but you can add or remove delimiters as needed by editing the list.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Identify Similar Data Rows by Using the Fuzzy Grouping Transformation](../../Topics\TopicNameNotContainA/Identify-Similar-Data-Rows-by-Using-the-Fuzzy-Grouping-Transformation.md)  
  
  