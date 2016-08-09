---
title: "- (Negate) (SSIS Expression)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
caps.latest.revision: 34
caps.handback.revision: 0
manager: jhubbard
---
# - (Negate) (SSIS Expression)
Negates a numeric expression.  
  
## Syntax  
  
```  
  
-numeric_expression  
  
```  
  
## Arguments  
 *numeric_expression*  
 Is any valid expression of any numeric data type. Only signed numeric data types are supported. For more information, see [Integration Services Data Types](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Result Types  
 Returns the data type of *numeric_expression*.  
  
## Expression Examples  
 This example negates the value of the **Counter** variable and adds the numeric literal 50.  
  
```  
-@Counter + 50  
```  
  
## See Also  
 [Operator Precedence and Associativity](../../Topics/TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators (SSIS Expression)](../../Topics/TopicNameNotContainA/Operators--SSIS-Expression-.md)