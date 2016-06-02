---
title: POWER (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: db48ae65-bfa6-4db1-8d3c-d0d4f8a399bc
---
# POWER (SSIS Expression)
  Returns the result of raising a numeric expression to a power. The power parameter must evaluate to an integer.  
  
## Syntax  
  
```  
  
POWER(numeric_expression,power)  
```  
  
## Arguments  
 *numeric\_expression*  
 Is a valid numeric expression.  
  
 *power*  
 Is a valid numeric expression.  
  
## Result Types  
 DT\_R8  
  
## Remarks  
 The *numeric\_expression* and *power* arguments are cast to the DT\_R8 data type before the power is computed. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 If *numeric\_expression* evaluates to zero and *power* is negative, the expression evaluator returns an error and sets the return result to null.  
  
 If *numeric\_expression* or *power* evaluate to indeterminate results, the return result is null.  
  
 The *power* argument can be a fraction. For example, you can use the value 0.5 as the power.  
  
## Expression Examples  
 This example uses a numeric literal. The function raises 4 to the power of 3 and returns 64.  
  
```  
POWER(4,3)  
```  
  
 This example uses the **Length** column and the **DimensionCount** variable. If **Length** is 8, and **DimensionCount** is 2, the return result is 64.  
  
```  
POWER(Length, @DimensionCount)   
```  
  
## See Also  
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  