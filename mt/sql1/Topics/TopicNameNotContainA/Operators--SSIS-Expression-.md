---
title: "Operators (SSIS Expression)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 33df3a3d-1f5c-429b-a3b9-52b7d8689089
caps.latest.revision: 36
caps.handback.revision: 0
manager: jhubbard
---
# Operators (SSIS Expression)
This section describes the operators the expression language provides and the operator precedence and associativity that the expression evaluator uses.  
  
 The following table lists topics about operators in this section.  
  
|Operator|Description|  
|--------------|-----------------|  
|[Cast (SSIS Expression)](../../Topics/TopicNameNotContainA/Cast--SSIS-Expression-.md)|Converts an expression from one data type to a different data type.|  
|[() (Parentheses) (SSIS Expression)](../../Topics/TopicNameNotContainA/----Parentheses---SSIS-Expression-.md)|Identifies the evaluation order of expressions.|  
|[+ (Add) (SSIS)](../../Topics/TopicNameNotContainA/---Add---SSIS-.md)|Adds two numeric expressions.|  
|[+ (Concatenate) (SSIS Expression)](../../Topics/TopicNameNotContainA/---Concatenate---SSIS-Expression-.md)|Concatenates two expressions.|  
|[- (Subtract) (SSIS Expression)](../../Topics/TopicNameNotContainA/---Subtract---SSIS-Expression-.md)|Subtracts the second numeric expression from the first one.|  
|[- (Negate) (SSIS Expression)](../../Topics/TopicNameNotContainA/---Negate---SSIS-Expression-.md)|Negates a numeric expression.|  
|[* (Multiply) (SSIS Expression)](../../Topics/TopicNameNotContainA/---Multiply---SSIS-Expression-.md)|Multiplies two numeric expressions.|  
|[Divide (SSIS Expression)](../../Topics/TopicNameNotContainA/Divide--SSIS-Expression-.md)|Divides the first numeric expression by the second one.|  
|[(Modulo) (SSIS Expression)](../../Topics/TopicNameNotContainA/-Modulo---SSIS-Expression-.md)|Provides the integer remainder after dividing the first numeric expression by the second one.|  
|[&#124;&#124; (Logical OR) (SSIS Expression)](../Topic/%7C%7C%20\(Logical%20OR\)%20\(SSIS%20Expression\).md)|Performs a logical OR operation.|  
|[&& (Logical AND) (SSIS Expression)](../../Topics/TopicNameNotContainA/----Logical-AND---SSIS-Expression-.md)|Performs a logical AND operation.|  
|[! (Logical Not) (SSIS Expression)](../../Topics/TopicNameNotContainA/!--Logical-Not---SSIS-Expression-.md)|Negates a Boolean operand.|  
|[&#124; (Bitwise Inclusive OR) (SSIS Expression)](../Topic/%7C%20\(Bitwise%20Inclusive%20OR\)%20\(SSIS%20Expression\).md)|Performs a bitwise OR operation of two integer values.|  
|[^ (Bitwise Exclusive OR) (SSIS Expression)](../Topic/%5E%20\(Bitwise%20Exclusive%20OR\)%20\(SSIS%20Expression\).md)|Performs a bitwise exclusive OR operation of two integer values.|  
|[& (Bitwise AND) (SSIS Expression)](../../Topics/TopicNameNotContainA/---Bitwise-AND---SSIS-Expression-.md)|Performs a bitwise AND operation of two integer values.|  
|[~ (Bitwise Not) (SSIS Expression)](../../Topics/TopicNameNotContainA/~--Bitwise-Not---SSIS-Expression-.md)|Performs a bitwise negation of an integer.|  
|[== (Equal) (SSIS Expression)](../../Topics/TopicNameNotContainA/==--Equal---SSIS-Expression-.md)|Performs a comparison to determine if two expressions are equal.|  
|[!= (Unequal) (SSIS Expression)](../../Topics/TopicNameNotContainA/!=--Unequal---SSIS-Expression-.md)|Performs a comparison to determine if two expressions are not equal.|  
|[> (Greater Than) (SSIS Expression)](../Topic/%3E%20\(Greater%20Than\)%20\(SSIS%20Expression\).md)|Performs a comparison to determine if the first expression is greater than the second one.|  
|[< (Less Than) (SSIS Expression)](../Topic/%3C%20\(Less%20Than\)%20\(SSIS%20Expression\).md)|Performs a comparison to determine if the first expression is less than the second one.|  
|[>= (Greater Than or Equal To) (SSIS Expression)](../Topic/%3E=%20\(Greater%20Than%20or%20Equal%20To\)%20\(SSIS%20Expression\).md)|Performs a comparison to determine if the first expression is greater than or equal to the second one.|  
|[<= (Less Than or Equal To) (SSIS Expression)](../Topic/%3C=%20\(Less%20Than%20or%20Equal%20To\)%20\(SSIS%20Expression\).md)|Performs a comparison to determine if the first expression is less than or equal to the second one.|  
|[? : (Conditional) (SSIS Expression)](../Topic/?%20:%20\(Conditional\)%20\(SSIS%20Expression\).md)|Returns one of two expressions based on the evaluation of a Boolean expression.|  
  
 For information about the placement of each operator in the precedence hierarchy, see [Operator Precedence and Associativity](../../Topics/TopicNameNotContainA/Operator-Precedence-and-Associativity.md).  
  
## See Also  
 [Functions (SSIS Expression)](../../Topics/TopicNameNotContainA/Functions--SSIS-Expression-.md)   
 [Examples of Advanced Integration Services Expressions](../../Topics/TopicNameNotContainA/Examples-of-Advanced-Integration-Services-Expressions.md)   
 [Integration Services (SSIS) Expressions](../../Topics/TopicNameNotContainA/Integration-Services--SSIS--Expressions.md)