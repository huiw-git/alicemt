---
title: Row Sampling Transformation
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b6caafd3-30b2-4368-82af-a44611d4cd39
---
# Row Sampling Transformation
  The Row Sampling transformation is used to obtain a randomly selected subset of an input dataset. You can specify the exact size of the output sample, and specify a seed for the random number generator.  
  
 There are many applications for random sampling. For example, a company that wanted to randomly select 50 employees to receive prizes in a lottery could use the Row Sampling transformation on the employee database to generate the exact number of winners.  
  
 The Row Sampling transformation is also useful during package development for creating a small but representative dataset. You can test package execution and data transformation with richly representative data, but more quickly because a random sample is used instead of the full dataset. Because the sample dataset used by the test package is always the same size, using the sample subset also makes it easier to identify performance problems in the package.  
  
 This transformation is similar to the Percentage Sampling transformation, which creates a sample dataset by selecting a percentage of the input rows. See [Percentage Sampling Transformation](../../Topics\TopicNameNotContainA/Percentage-Sampling-Transformation.md).  
  
## Configuring the Row Sampling Transformation  
 The Row Sampling transformation creates a sample dataset by selecting a specified number of the transformation input rows. Because the selection of rows from the transformation input is random, the resultant sample is representative of the input. You can also specify the seed that is used by the random number generator, to affect how the transformation selects rows.  
  
 Using the same random seed on the same transformation input always creates the same sample output. If no seed is specified, the transformation uses the tick count of the operating system to create the random number. Therefore, you could use the same seed during testing, to verify the transformation results during the development and testing of the package, and then change to a random seed when the package is moved into production.  
  
 The Row Sampling transformation includes the **SamplingValue** custom property. This property can be updated by a property expression when the package is loaded. For more information, see [Integration Services &#40;SSIS&#41; Expressions](../Topic/Integration%20Services%20\(SSIS\)%20Expressions.md), [Use Property Expressions in Packages](../../Topics\TopicNameNotContainA/Use-Property-Expressions-in-Packages.md), and [Transformation Custom Properties](../../Topics\TopicNameNotContainA/Transformation-Custom-Properties.md).  
  
 This transformation has one input and two outputs. It has no error output.  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in the **Row Sampling Transformation Editor** dialog box, see [Row Sampling Transformation Editor &#40;Sampling Page&#41;](../Topic/Row%20Sampling%20Transformation%20Editor%20\(Sampling%20Page\).md).  
  
 The **Advanced Editor** dialog box reflects the properties that can be set programmatically. For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:  
  
-   [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
-   [Transformation Custom Properties](../../Topics\TopicNameNotContainA/Transformation-Custom-Properties.md)  
  
 For more information about how to set properties, see.  
  
## Related Tasks  
 [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md)  
  
  