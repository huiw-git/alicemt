---
title: "Operator Precedence and Associativity"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5094164f-dabc-45b5-b611-384feb2b3fe3
caps.latest.revision: 33
caps.handback.revision: 0
manager: jhubbard
---
# Operator Precedence and Associativity
Each operator in the set of operators that the expression evaluator supports has a designated precedence in the precedence hierarchy and includes a direction in which it is evaluated. The direction of evaluation for an operator is operator associativity. Operators with higher precedence are evaluated before operators with lower precedence. If a complex expression has multiple operators, operator precedence determines the order in which the operations are performed. The order of execution can significantly affect the resulting value. Some operators have equal precedence. If an expression contains multiple operators of equal precedence, the operators are evaluated directionally, from left to right or right to left.  
  
 The following table lists the precedence of operators in order of high to low. Operators at the same level have equal precedence.  
  
|Operator symbol|Type of Operation|Associativity|  
|---------------------|-----------------------|-------------------|  
|( )|Expression|Left to right|  
|–, !, ~|Unary|Right to left|  
|casts|Unary|Right to left|  
|*, / ,%|Multiplicative|Left to right|  
|+, –|Additive|Left to right|  
|<, >, <=, >=|Relational|Left to right|  
|==, !=|Equality|Left to right|  
|&|Bitwise AND|Left to right|  
|^|Bitwise exclusive OR|Left to right|  
|&#124;|Bitwise inclusive OR|Left to right|  
|&&|Logical AND|Left to right|  
|&#124;&#124;|Logical OR|Left to right|  
|? :|Conditional expression|Right to left|  
  
## See Also  
 [Operators (SSIS Expression)](../../Topics/TopicNameNotContainA/Operators--SSIS-Expression-.md)