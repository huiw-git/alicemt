---
title: () (Parentheses) (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 931e10eb-1707-4121-b2f1-43565561119f
---
# () (Parentheses) (SSIS Expression)
  Identifies the evaluation order of expressions. Expressions enclosed in parentheses have the highest evaluation precedence. Nested expressions enclosed in parentheses are evaluated in inner\-to\-outer order.  
  
 Parentheses are also used to make complex expressions easier to understand.  
  
## Syntax  
  
```  
  
(expression)  
  
```  
  
## Arguments  
 *expression*  
 Is any valid expression.  
  
## Result Types  
 The data type of *expression*. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Expression Examples  
 This example shows how the use of parenthesis modifies the precedence of operators. The first expression evaluates to 100, whereas the second one evaluates to 31.  
  
```  
(5 + 5) * (4 + 6)  
5 + 5 * 4 + 6  
  
```  
  
## See Also  
 [Operator Precedence and Associativity](../../Topics\TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators &#40;SSIS Expression&#41;](../Topic/Operators%20\(SSIS%20Expression\).md)  
  
  