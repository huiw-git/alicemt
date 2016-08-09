---
title: "(Modulo) (SSIS Expression)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2920821-2f5b-4c76-8db8-8b9eddf4606f
caps.latest.revision: 35
caps.handback.revision: 0
manager: jhubbard
---
# (Modulo) (SSIS Expression)
Provides the integer remainder after dividing the first numeric expression by the second one.  
  
## Syntax  
  
```  
  
dividend % divisor  
  
```  
  
## Arguments  
 *dividend*  
 Is the numeric expression to divide. *dividend* can be any valid numeric expression. For more information, see [Integration Services Data Types](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types.md)  
  
 *divisor*  
 Is the numeric expression to divide the dividend by. *divisor* can be any valid numeric expression except zero.  
  
## Result Types  
 Determined by data types of the two arguments. For more information, see [Integration Services Data Types in Expressions](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types-in-Expressions.md).  
  
## Remarks  
 Both expressions must evaluate to signed or unsigned integer data types.  
  
 If either operand is null, the result is null.  
  
 Modulo zero is not legal.  
  
## Expression Examples  
 This example computes the modulus from two numeric literals. The result is 3.  
  
```  
42 % 13  
```  
  
 This example computes the modulus from the **SalesQuota** column and a numeric literal.  
  
```  
SalesQuota % 12  
```  
  
 This example computes the modulus from two numeric variables **Sales$** and **Month**. The variable **Sales$** must be enclosed in brackets because the name includes the $ character. For more information, see [Identifiers (SSIS)](../../Topics/TopicNameNotContainA/Identifiers--SSIS-.md).  
  
```  
@[Sales$] % @Month  
```  
  
 This example uses the modulo operator to determine if the value of the **Value** variable is even or odd, and uses the conditional operator to return a string that describes the result. For more information, see [? : (Conditional) (SSIS Expression)](../Topic/?%20:%20\(Conditional\)%20\(SSIS%20Expression\).md).  
  
```  
@Value % 2 == 0? "even":"odd"  
```  
  
## See Also  
 [Operator Precedence and Associativity](../../Topics/TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators (SSIS Expression)](../../Topics/TopicNameNotContainA/Operators--SSIS-Expression-.md)