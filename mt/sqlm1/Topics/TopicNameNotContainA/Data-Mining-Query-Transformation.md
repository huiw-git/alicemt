---
title: Data Mining Query Transformation
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7960133b-a3e1-48af-ba43-55ed78c38e71
---
# Data Mining Query Transformation
  The Data Mining Query transformation performs prediction queries against data mining models. This transformation contains a query builder for creating Data Mining Extensions \(DMX\) queries. The query builder lets you create custom statements for evaluating the transformation input data against an existing mining model using the DMX language. For more information, see [Data Mining Extensions &#40;DMX&#41; Reference](../Topic/Data%20Mining%20Extensions%20\(DMX\)%20Reference.md).  
  
 One transformation can execute multiple prediction queries if the models are built on the same data mining structure. For more information, see [Data Mining Query Tools](../../Topics\TopicNameNotContainA/Data-Mining-Query-Tools.md).  
  
## Configuration of the Data Mining Query Transformation  
 The Data Mining Query transformation uses an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] connection manager to connect to the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] project or the instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] that contains the mining structure and mining models. For more information, see [Analysis Services Connection Manager](../../Topics\TopicNameNotContainA/Analysis-Services-Connection-Manager.md).  
  
 This transformation has one input and one output. It does not support an error output.  
  
 You can set properties through [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in the **Data Mining Query Transformation Editor** dialog box, click one of the following topics:  
  
-   [Data Mining Query Transformation Editor &#40;Mining Model Tab&#41;](../Topic/Data%20Mining%20Query%20Transformation%20Editor%20\(Mining%20Model%20Tab\).md)  
  
-   [Data Mining Query Transformation Editor &#40;Mining Model Tab&#41;](../Topic/Data%20Mining%20Query%20Transformation%20Editor%20\(Mining%20Model%20Tab\).md)  
  
 The **Advanced Editor** dialog box reflects the properties that can be set programmatically. For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:  
  
-   [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
-   [Transformation Custom Properties](../../Topics\TopicNameNotContainA/Transformation-Custom-Properties.md)  
  
 For more information about how to set properties, see [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md).  
  
  