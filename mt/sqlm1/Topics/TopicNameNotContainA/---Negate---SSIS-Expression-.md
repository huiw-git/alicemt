---
title: - (Negate) (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
---
# - (Negate) (SSIS Expression)
  Negates a numeric expression.  
  
## Syntax  
  
```  
  
-numeric_expression  
  
```  
  
## Arguments  
 *numeric\_expression*  
 Is any valid expression of any numeric data type. Only signed numeric data types are supported. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Result Types  
 Returns the data type of *numeric\_expression*.  
  
## Expression Examples  
 This example negates the value of the **Counter** variable and adds the numeric literal 50.  
  
```  
-@Counter + 50  
```  
  
## See Also  
 [Operator Precedence and Associativity](../../Topics\TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators &#40;SSIS Expression&#41;](../Topic/Operators%20\(SSIS%20Expression\).md)  
  
  