---
title: Derived Column Transformation Editor
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff73923e-d245-43d8-bf24-af3bdc942e51
---
# Derived Column Transformation Editor
  Use the **Derived Column Transformation Editor** dialog box to create expressions that populate new or replacement columns.  
  
 To learn more about the Derived Column transformation, see [Derived Column Transformation](../../Topics\TopicNameNotContainA/Derived-Column-Transformation.md).  
  
## Options  
 **Variables and Columns**  
 Build an expression that uses a variable or an input column by dragging the variable or column from the list of available variables and columns to an existing table row in the pane below, or to a new row at the bottom of the list.  
  
 **Functions and Operators**  
 Build an expression that uses a function or an operator to evaluate input data and direct output data by dragging functions and operators from the list to the pane below.  
  
 **Derived Column Name**  
 Provide a derived column name. The default is a numbered list of derived columns; however, you can choose any unique, descriptive name.  
  
 **Derived Column**  
 Select a derived column from the list. Choose whether to add the derived column as a new output column, or to replace the data in an existing column.  
  
 **Expression**  
 Type an expression or build one by dragging from the previous list of available columns, variables, functions, and operators.  
  
 The value of this property can be specified by using a property expression.  
  
 **Related topics**: [Integration Services &#40;SSIS&#41; Expressions](../Topic/Integration%20Services%20\(SSIS\)%20Expressions.md), [Operators &#40;SSIS Expression&#41;](../Topic/Operators%20\(SSIS%20Expression\).md), and [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
 **Data Type**  
 If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically evaluates the expression and sets the data type appropriately. The value of this column is read\-only. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 **Length**  
 If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically evaluates the expression and sets the column length for string data. The value of this column is read\-only.  
  
 **Precision**  
 If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically sets the precision for numeric data based on the data type. The value of this column is read\-only.  
  
 **Scale**  
 If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically sets the scale for numeric data based on the data type. The value of this column is read\-only.  
  
 **Code Page**  
 If adding data to a new column, the **Derived Column TransformationEditor** dialog box automatically sets code page for the DT\_STR data type. You can update **Code Page**.  
  
 **Configure error output**  
 Specify how to handle errors by using the [Configure Error Output](../../Topics\TopicNameNotContainA/Configure-Error-Output.md) dialog box.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Derive Column Values by Using the Derived Column Transformation](../../Topics\TopicNameNotContainA/Derive-Column-Values-by-Using-the-Derived-Column-Transformation.md)  
  
  