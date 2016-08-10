---
title: "+ (Add) (SSIS)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
caps.latest.revision: 28
caps.handback.revision: 0
manager: jhubbard
---
# + (Add) (SSIS)
Adds two numeric expressions.  
  
## Syntax  
  
```  
  
numeric_expression1 + numeric_expression2  
  
```  
  
## Arguments  
 *numeric_expression1, numeric_ expression2*  
 Is any valid expression of a numeric data type.  
  
## Result Types  
 Determined by data types of the two arguments. For more information, see [Integration Services Data Types](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Remarks  
 If either operand is null, the result is null.  
  
## Expression Examples  
 This example adds numeric literals.  
  
```  
5 + 6.09 + 7.0  
```  
  
 This example adds values in the **VacationHours** and **SickLeaveHours** columns.  
  
```  
VacationHours + SickLeaveHours  
```  
  
 This example adds a calculated value to the **StandardCost** column. The variable **Profit%** must be enclosed in brackets because the name includes the % character. For more information, see [Identifiers (SSIS)](../../Topics/TopicNameNotContainA/Identifiers--SSIS-.md).  
  
```  
StandardCost + (StandardCost * @[Profit%])  
```  
  
## See Also  
 [Operator Precedence and Associativity](../../Topics/TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators (SSIS Expression)](../../Topics/TopicNameNotContainA/Operators--SSIS-Expression-.md)