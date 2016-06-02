---
title: Multicast Transformation
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 32194784-1684-40cd-9f91-1aba4d8360d3
---
# Multicast Transformation
  The Multicast transformation distributes its input to one or more outputs. This transformation is similar to the Conditional Split transformation. Both transformations direct an input to multiple outputs. The difference between the two is that the Multicast transformation directs every row to every output, and the Conditional Split directs a row to a single output. For more information, see [Conditional Split Transformation](../../Topics\TopicNameNotContainA/Conditional-Split-Transformation.md).  
  
 You configure the Multicast transformation by adding outputs.  
  
 Using the Multicast transformation, a package can create logical copies of data. This capability is useful when the package needs to apply multiple sets of transformations to the same data. For example, one copy of the data is aggregated and only the summary information is loaded into its destination, while another copy of the data is extended with lookup values and derived columns before it is loaded into its destination.  
  
 This transformation has one input and multiple outputs. It does not support an error output.  
  
## Configuration of the Multicast Transformation  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For information about the properties that you can set in the **Multicast Transformation Editor** dialog box, see [Multicast Transformation Editor](../../Topics\TopicNameNotContainA/Multicast-Transformation-Editor.md).  
  
 For information about the properties that you can set programmatically, see [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md).  
  
## Related Tasks  
 For information about how to set properties of this component, see [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md).  
  
## See Also  
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)   
 [Integration Services Transformations](../../Topics\TopicNameNotContainA/Integration-Services-Transformations.md)  
  
  