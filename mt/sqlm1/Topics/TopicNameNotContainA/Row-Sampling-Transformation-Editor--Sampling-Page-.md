---
title: Row Sampling Transformation Editor (Sampling Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 544c7709-6de0-4c08-bda3-759985be9a05
---
# Row Sampling Transformation Editor (Sampling Page)
  Use the **Row Sampling Transformation Editor** dialog box to split a portion of an input into a sample using a specified number of rows. This transformation divides the input into two separate outputs.  
  
 To learn more about the Row Sampling transformation, see [Row Sampling Transformation](../../Topics\TopicNameNotContainA/Row-Sampling-Transformation.md).  
  
## Options  
 **Number of rows**  
 Specify the number of rows from the input to use as a sample.  
  
 The value of this property can be specified by using a property expression.  
  
 **Sample output name**  
 Provide a unique name for the output that will include the sampled rows. The name provided will be displayed within SSIS Designer.  
  
 **Unselected output name**  
 Provide a unique name for the output that will contain the rows excluded from the sampling. The name provided will be displayed within SSIS Designer.  
  
 **Use the following random seed**  
 Specify the sampling seed for the random number generator that the transformation uses to create a sample. This is only recommended for development and testing. The transformation uses the Microsoft Windows tick count as a seed if a random seed is not specified.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Percentage Sampling Transformation](../../Topics\TopicNameNotContainA/Percentage-Sampling-Transformation.md)  
  
  