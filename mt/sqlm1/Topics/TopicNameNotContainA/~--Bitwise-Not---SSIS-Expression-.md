---
title: ~ (Bitwise Not) (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
---
# ~ (Bitwise Not) (SSIS Expression)
  Performs a bitwise negation of an integer. This operator can be applied to signed and unsigned integer data types.  
  
## Syntax  
  
```  
  
~integer_expression  
  
```  
  
## Arguments  
 *integer\_expression*  
 Is any valid expression of an integer data type. *integer*\_*expression* is an integer that is transformed into a binary number for the bitwise operation. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Result Types  
 Returns the data type of *integer\_expression.*  
  
## Remarks  
 None  
  
## Expression Examples  
 This example performs a bitwise ~ \(NOT\) operation on the number 170 \(0000 0000 1010 1010\). The number is a signed integer.  
  
```  
  
~ 170  
```  
  
 The expression evaluates to \-170 \(1111111101010101\).  
  
 0000000010101010  
  
 \-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-\-  
  
 1111111101010101  
  
## See Also  
 [Operator Precedence and Associativity](../../Topics\TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators &#40;SSIS Expression&#41;](../Topic/Operators%20\(SSIS%20Expression\).md)  
  
  