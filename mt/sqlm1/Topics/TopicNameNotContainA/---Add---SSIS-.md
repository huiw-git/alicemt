---
title: + (Add) (SSIS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
---
# + (Add) (SSIS)
  Adds two numeric expressions.  
  
## Syntax  
  
```  
  
numeric_expression1 + numeric_expression2  
  
```  
  
## Arguments  
 *numeric\_expression1, numeric\_ expression2*  
 Is any valid expression of a numeric data type.  
  
## Result Types  
 Determined by data types of the two arguments. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
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
  
 This example adds a calculated value to the **StandardCost** column. The variable **Profit%** must be enclosed in brackets because the name includes the % character. For more information, see [Identifiers &#40;SSIS&#41;](../Topic/Identifiers%20\(SSIS\).md).  
  
```  
StandardCost + (StandardCost * @[Profit%])  
```  
  
## See Also  
 [Operator Precedence and Associativity](../../Topics\TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators &#40;SSIS Expression&#41;](../Topic/Operators%20\(SSIS%20Expression\).md)  
  
  