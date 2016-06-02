---
title: Copy Column Transformation
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1c72a313-9026-46bc-a57f-c6b3f47346f8
---
# Copy Column Transformation
  The Copy Column transformation creates new columns by copying input columns and adding the new columns to the transformation output. Later in the data flow, different transformations can be applied to the column copies. For example, you can use the Copy Column transformation to create a copy of a column and then convert the copied data to uppercase characters by using the Character Map transformation, or apply aggregations to the new column by using the Aggregate transformation.  
  
## Configuration of the Copy Column Transformation  
 You configure the Copy Column transformation by specifying the input columns to copy. You can create multiple copies of a column, or create copies of multiple columns in one operation.  
  
 This transformation has one input and one output. It does not support an error output.  
  
 You can set properties through the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically.  
  
 For more information about the properties that you can set in the **Copy Column Transformation Editor** dialog box, see [Copy Column Transformation Editor](../../Topics\TopicNameNotContainA/Copy-Column-Transformation-Editor.md).  
  
 The **Advanced Editor** dialog box reflects the properties that can be set programmatically. For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:  
  
-   [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md)  
  
-   [Transformation Custom Properties](../../Topics\TopicNameNotContainA/Transformation-Custom-Properties.md)  
  
 For more information about how to set properties, see [Set the Properties of a Data Flow Component](../../Topics\TopicNameContainA/Set-the-Properties-of-a-Data-Flow-Component.md).  
  
## See Also  
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)   
 [Integration Services Transformations](../../Topics\TopicNameNotContainA/Integration-Services-Transformations.md)  
  
  