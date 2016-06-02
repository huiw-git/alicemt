---
title: &amp; (Bitwise AND) (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 06d2958e-66a5-44d8-8bc4-56209ebe1ff2
---
# &amp; (Bitwise AND) (SSIS Expression)
  Performs a bitwise AND operation of two integer values. It compares each bit of its first operand to the corresponding bit of its second operand. If both bits are 1, the corresponding result bit is set to 1. Otherwise, the corresponding result bit is set to 0.  
  
 Both conditions must be a signed integer type or both conditions must be an unsigned integer type.  
  
## Syntax  
  
```  
  
integer_expression1 & integer_expression2  
  
```  
  
## Arguments  
 *integer\_expression1, integer\_expression2*  
 Is any valid expression of a signed or unsigned integer data type. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Result Types  
 Determined by data types of the two arguments. For more information, see [Integration Services Data Types in Expressions](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types-in-Expressions.md).  
  
## Remarks  
 If either condition is null, the expression result is null.  
  
## Expression Examples  
 This example performs a bitwise AND operation between the columns **NumberA** and **NumberB**. **NumberA** contains 3 \(0000011\) and column **NumberB** contains 7 \(00000111\).  
  
```  
NumberA & NumberB  
```  
  
 The expression evaluates to 3 \(00000011\).  
  
 00000011  
  
 00000111  
  
 \-\-\-\-\-\-\-\-\-\-\-  
  
 00000011  
  
 This example performs a bitwise AND operation between the **ReorderPoint** and **SafetyStockLevel** columns.  
  
```  
ReorderPoint & SafetyStockLevel  
```  
  
 If **ReorderPoint** is 10 and **SafetyStockLevel** is 8, the expression evaluates to 8 \(00001000\).  
  
 00001010  
  
 00001000  
  
 \-\-\-\-\-\-\-\-\-\-\-  
  
 00001000  
  
 This example performs a bitwise AND operation between two integers.  
  
```  
3 & 5   
```  
  
 The expression evaluates to 1\(00000001\).  
  
 00000011  
  
 00000101  
  
 \-\-\-\-\-\-\-\-\-\-\-  
  
 00000001  
  
## See Also  
 [&& &#40;Logical AND&#41; &#40;SSIS Expression&#41;](../Topic/&&%20\(Logical%20AND\)%20\(SSIS%20Expression\).md)   
 [Operator Precedence and Associativity](../../Topics\TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators &#40;SSIS Expression&#41;](../Topic/Operators%20\(SSIS%20Expression\).md)  
  
  