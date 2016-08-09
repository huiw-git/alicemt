---
title: "- (Subtract) (SSIS Expression)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b48da086-37dd-460a-8a4b-912f52c9b158
caps.latest.revision: 33
caps.handback.revision: 0
manager: jhubbard
---
# - (Subtract) (SSIS Expression)
Subtracts the second numeric expression from the first one.  
  
## Syntax  
  
```  
  
numeric_expression1 – numeric_expression2  
  
```  
  
## Arguments  
 *numeric_expression1, numeric_expression2*  
 Is any valid expression of a numeric data type. For more information, see [Integration Services Data Types](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Result Types  
 Determined by the data types of the two arguments. For more information, see [Integration Services Data Types in Expressions](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types-in-Expressions.md).  
  
## Remarks  
 Enclose the minus unary expression in parenthesis to ensure that the expression is evaluated in the correct order  
  
## Remarks  
 If either operand is null, the result is null.  
  
## Expression Examples  
 This example subtracts numeric literals.  
  
```  
5 - 6.09  
```  
  
 This example subtracts the value in the **StandardCost** column from the value in the **ListPrice** column.  
  
```  
ListPrice - StandardCost  
```  
  
 This example subtracts a calculated value from the **ListPrice** column. The variable **Discount%** must be enclosed in brackets because the name includes the % character. For more information, see [Identifiers (SSIS)](../../Topics/TopicNameNotContainA/Identifiers--SSIS-.md).  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## See Also  
 [Operator Precedence and Associativity](../../Topics/TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators (SSIS Expression)](../../Topics/TopicNameNotContainA/Operators--SSIS-Expression-.md)