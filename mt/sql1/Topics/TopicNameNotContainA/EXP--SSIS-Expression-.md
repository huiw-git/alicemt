---
title: "EXP (SSIS Expression)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
caps.latest.revision: 35
caps.handback.revision: 0
manager: jhubbard
---
# EXP (SSIS Expression)
Returns the exponent to base e of a numeric expression. The EXP function complements the action of the LN function and is sometimes referred to as the antilogarithm.  
  
## Syntax  
  
```  
  
EXP(numeric_expression)  
```  
  
## Arguments  
 *numeric_expression*  
 Is a valid numeric expression.  
  
## Result Types  
 DT_R8  
  
## Remarks  
 The numeric expression is cast to the DT_R8 data type before the exponent is computed. For more information, see [Integration Services Data Types](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 The return result is always a positive number.  
  
## Expression Examples  
 These examples apply the EXP function to positive and negative values and to zero.  
  
```  
EXP(74)  
```  
  
 Returns 1.373382979540176E+32.  
  
```  
EXP(-27)  
```  
  
 Returns 1.879528816539083E-12.  
  
```  
EXP(0)  
```  
  
 Returns 1.  
  
## See Also  
 [LOG (SSIS Expression)](../../Topics/TopicNameNotContainA/LOG--SSIS-Expression-.md)   
 [Functions (SSIS Expression)](../../Topics/TopicNameNotContainA/Functions--SSIS-Expression-.md)