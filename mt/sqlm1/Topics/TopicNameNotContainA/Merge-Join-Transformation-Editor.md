---
title: Merge Join Transformation Editor
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ac06f419-30b3-42aa-8b34-42000bec4285
---
# Merge Join Transformation Editor
  Use the **Merge Join Transformation Editor** dialog box to specify the join type, the join columns, and the output columns for merging two inputs combined by a join.  
  
> [!IMPORTANT]  
>  The Merge Join Transformation requires sorted data for its inputs. For more information about this important requirement, see [Sort Data for the Merge and Merge Join Transformations](../../Topics\TopicNameNotContainA/Sort-Data-for-the-Merge-and-Merge-Join-Transformations.md).  
  
 To learn more about the Merge Join transformation, see [Merge Join Transformation](../../Topics\TopicNameNotContainA/Merge-Join-Transformation.md).  
  
## Options  
 **Join type**  
 Specify whether you want to use an inner join, left outer join, or full join.  
  
 **Swap Inputs**  
 Switch the order between inputs by using the **Swap Inputs** button. This selection may be useful with the Left outer join option.  
  
 **Input**  
 For each column that you want in the merged output, first select from the list of available inputs.  
  
 Inputs are displayed in two separate tables. Select columns to include in the output. Drag columns to create a join between the tables. To delete a join, select it and then press the DELETE key.  
  
 **Input Column**  
 Select a column to include in the merged output from the list of available columns on the selected input.  
  
 **Output Alias**  
 Type an alias for each output column. The default is the name of the input column; however, you can choose any unique, descriptive name.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Sort Data for the Merge and Merge Join Transformations](../../Topics\TopicNameNotContainA/Sort-Data-for-the-Merge-and-Merge-Join-Transformations.md)   
 [Extend a Dataset by Using the Merge Join Transformation](../../Topics\TopicNameContainA/Extend-a-Dataset-by-Using-the-Merge-Join-Transformation.md)   
 [Merge Transformation](../../Topics\TopicNameNotContainA/Merge-Transformation.md)   
 [Union All Transformation](../../Topics\TopicNameNotContainA/Union-All-Transformation.md)  
  
  