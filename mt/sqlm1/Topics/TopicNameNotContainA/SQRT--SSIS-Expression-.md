---
title: SQRT (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 54a75389-c501-4e22-87b8-905f66d6a3a5
---
# SQRT (SSIS Expression)
  Returns the square root of a numeric expression.  
  
## Syntax  
  
```  
  
SQRT(numeric_expression)  
```  
  
## Arguments  
 *numeric\_expression*  
 Is a numeric expression of any numeric data type. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Result Types  
 DT\_R8  
  
## Remarks  
 SQRT returns a null result if the argument is null.  
  
 SQRT fails if the argument is a negative value.  
  
 The argument is cast to the DT\_R8 data type before the square root operation.  
  
## Expression Examples  
 This example returns the square root of a numeric literal. The return result is 12.  
  
```  
SQRT(144)  
```  
  
 This example returns the square root of an expression, the result of subtracting values in the **Value1** and **Value2** columns.  
  
```  
SQRT(Value1 - Value2)  
```  
  
 This example returns the length of the third side of a right triangle by applying the SQUARE function to two variables and then calculating the square root of their sum. If **Side1** contains 3 and **Side2** contains 4, the SQRT function returns 5.  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  In expressions, variable names always include the @ prefix.  
  
## See Also  
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  