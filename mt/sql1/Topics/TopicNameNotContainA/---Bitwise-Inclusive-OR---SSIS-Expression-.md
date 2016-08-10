---
title: "| (Bitwise Inclusive OR) (SSIS Expression)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4dce9eb2-3680-4adc-81a3-816ea52cef49
caps.latest.revision: 40
caps.handback.revision: 0
manager: jhubbard
---
# | (Bitwise Inclusive OR) (SSIS Expression)
Performs a bitwise OR operation of two integer values. It compares each bit of its first operand to the corresponding bit of its second operand. If either bit is 1, the corresponding result bit is set to 1. Otherwise, the corresponding result bit is set to zero (0).  
  
 Both conditions must be a signed integer data type or both conditions must be an unsigned integer data type.  
  
## Syntax  
  
```  
  
integer_expression1 | integer_expression2  
  
```  
  
## Arguments  
 *integer_expression1 ,integer_ expression2*  
 Is any valid expression of a signed or unsigned integer data type. For more information, see [Integration Services Data Types](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Result Types  
 Determined by data types of the two arguments. For more information, see [Integration Services Data Types in Expressions](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types-in-Expressions.md).  
  
## Remarks  
 If either condition is null, the expression result is null.  
  
## Expression Examples  
 This example performs a bitwise inclusive OR operation between the variables **NumberA** and **NumberB**. **NumberA** contains 3 (00000011) and **NumberB** contains 9 (00001001).  
  
```  
@NumberA | @NumberB  
```  
  
 The expression evaluates to 11 (00001011).  
  
 00000011  
  
 00001001  
  
 ----------\-  
  
 00001011  
  
 This example performs a bitwise inclusive OR operation between the **ReorderPoint** and **SafetyStockLevel** columns.  
  
```  
ReorderPoint | SafetyStockLevel  
```  
  
 If **ReorderPoint** is 10 and **SafetyStockLevel** is 8, the expression evaluates to 10 (00001010).  
  
 00001010  
  
 00001000  
  
 ----------\-  
  
 00001010  
  
 This example performs a bitwise inclusive OR operation between two integers.  
  
```  
3 | 5   
```  
  
 The expression evaluates to 7 (00000111).  
  
 00000011  
  
 00000101  
  
 ----------\-  
  
 00000111  
  
## See Also  
 [&#124;&#124; (Logical OR) (SSIS Expression)](../Topic/%7C%7C%20\(Logical%20OR\)%20\(SSIS%20Expression\).md)   
 [^ (Bitwise Exclusive OR) (SSIS Expression)](../Topic/%5E%20\(Bitwise%20Exclusive%20OR\)%20\(SSIS%20Expression\).md)   
 [Operator Precedence and Associativity](../../Topics/TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators (SSIS Expression)](../../Topics/TopicNameNotContainA/Operators--SSIS-Expression-.md)