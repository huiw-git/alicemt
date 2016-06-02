---
title: Data Conversion Transformation
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fd515bbc-6f49-4d0c-ae7f-6ea3c3f24a1c
---
# Data Conversion Transformation
  The Data Conversion transformation converts the data in an input column to a different data type and then copies it to a new output column. For example, a package can extract data from multiple sources, and then use this transformation to convert columns to the data type required by the destination data store. You can apply multiple conversions to a single input column.  
  
 Using this transformation, a package can perform the following types of data conversions:  
  
-   Change the data type. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
    > [!NOTE]  
    >  If you are converting data to a date or a datetime data type, the date in the output column is in the ISO format, although the locale preference may specify a different format.  
  
-   Set the column length of string data and the precision and scale on numeric data. For more information, see [Precision, Scale, and Length &#40;Transact-SQL&#41;](../Topic/Precision,%20Scale,%20and%20Length%20\(Transact-SQL\).md).  
  
-   Specify a code page. For more information, see [Comparing String Data](../../Topics\TopicNameNotContainA/Comparing-String-Data.md).  
  
    > [!NOTE]  
    >  When copying between columns with a string data type, the two columns must use the same code page.  
  
 If the length of an output column of string data is shorter than the length of its corresponding input column, the output data is truncated. For more information, see [Error Handling in Data](../../Topics\TopicNameNotContainA/Error-Handling-in-Data.md).  
  
 This transformation has one input, one output, and one error output.  
  
## Related Tasks  
 You can set properties through the [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] Designer or programmatically. For information about using the Data Conversion Transformation in the SSIS Designer, see [Convert Data to a Different Data Type by Using the Data Conversion Transformation](../../Topics\TopicNameContainA/Convert-Data-to-a-Different-Data-Type-by-Using-the-Data-Conversion-Transformation.md) and [Data Conversion Transformation Editor](../../Topics\TopicNameNotContainA/Data-Conversion-Transformation-Editor.md). For information about setting properties of this transformation programmatically, see [Common Properties](../../Topics\TopicNameNotContainA/Common-Properties.md) and [Transformation Custom Properties](../../Topics\TopicNameNotContainA/Transformation-Custom-Properties.md).  
  
## Related Content  
 Blog entry, [Performance Comparison between Data Type Conversion Techniques in SSIS 2008](http://go.microsoft.com/fwlink/?LinkId=220823), on blogs.msdn.com.  
  
## See Also  
 [Fast Parse](../../Topics\TopicNameNotContainA/Fast-Parse.md)   
 [Data Flow](../../Topics\TopicNameNotContainA/Data-Flow.md)   
 [Integration Services Transformations](../../Topics\TopicNameNotContainA/Integration-Services-Transformations.md)  
  
  