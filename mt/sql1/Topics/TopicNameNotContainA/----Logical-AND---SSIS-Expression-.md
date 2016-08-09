---
title: "&amp;&amp; (Logical AND) (SSIS Expression)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8cb3517-d5d1-4861-9f04-905c719185ff
caps.latest.revision: 34
caps.handback.revision: 0
manager: jhubbard
---
# &amp;&amp; (Logical AND) (SSIS Expression)
Performs a logical AND operation. The expression evaluates to TRUE if all conditions are TRUE.  
  
## Syntax  
  
```  
  
boolean_expression1 && boolean_expression2  
```  
  
## Arguments  
 *boolean _expression1, boolean_expression2*  
 Is any valid expression that evaluates to TRUE, FALSE, or NULL.  
  
## Result Types  
 DT_BOOL  
  
## Remarks  
 The following table shows the result of the && operator.  
  
|Result|Expression|Expression|  
|------------|----------------|----------------|  
|TRUE|TRUE|TRUE|  
|FALSE|TRUE|FALSE|  
|FALSE|FALSE|FALSE|  
|NULL|NULL|NULL|  
|NULL|NULL|TRUE|  
|FALSE|NULL|FALSE|  
  
## Expression Examples  
 This example uses the **StandardCost** and the **ListPrice** columns. The example evaluates to TRUE if the value of the **StandardCost** column is less than 300 and the **ListPrice** column is greater than 500.  
  
```  
StandardCost < 300 && ListPrice > 500  
```  
  
 This example uses the variables **SPrice** and **LPrice** instead of literals.  
  
```  
StandardCost < @SPrice && ListPrice > @LPrice  
```  
  
## See Also  
 [& (Bitwise AND) (SSIS Expression)](../../Topics/TopicNameNotContainA/---Bitwise-AND---SSIS-Expression-.md)   
 [Operator Precedence and Associativity](../../Topics/TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators (SSIS Expression)](../../Topics/TopicNameNotContainA/Operators--SSIS-Expression-.md)