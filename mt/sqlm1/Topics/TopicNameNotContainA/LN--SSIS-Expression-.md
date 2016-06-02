---
title: LN (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 55d7b657-b5fd-4753-9c81-54ed7575e720
---
# LN (SSIS Expression)
  Returns the natural logarithm of a numeric expression.  
  
## Syntax  
  
```  
  
LN(numeric_expression)  
```  
  
## Arguments  
 *numeric\_expression*  
 Is a valid non\-zero and non\-negative numeric expression.  
  
## Result Types  
 DT\_R8  
  
## Remarks  
 The numeric expression is cast to the DT\_R8 data type before the logarithm is computed. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 If *numeric\_expression* evaluates to zero or a negative value, the return result is null.  
  
## Expression Examples  
 This example uses a numeric literal. The function returns the value 3.737766961828337.  
  
```  
LN(42)  
```  
  
 This example uses the column **Length**. If the column value is 53.99, the function returns 3.9887988442302.  
  
```  
LN(Length)   
```  
  
 This example uses the variable **Length**. The variable must have a numeric data type or the expression must include an explicit cast to a numeric data type. If **Length** is 234.567, the function returns 5.45774126708797.  
  
```  
LN(@Length)   
```  
  
## See Also  
 [LOG &#40;SSIS Expression&#41;](../Topic/LOG%20\(SSIS%20Expression\).md)   
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  