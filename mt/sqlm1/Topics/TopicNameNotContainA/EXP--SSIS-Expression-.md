---
title: EXP (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cd96d3c-58c9-4a67-a6f6-b72758232912
---
# EXP (SSIS Expression)
  Returns the exponent to base e of a numeric expression. The EXP function complements the action of the LN function and is sometimes referred to as the antilogarithm.  
  
## Syntax  
  
```  
  
EXP(numeric_expression)  
```  
  
## Arguments  
 *numeric\_expression*  
 Is a valid numeric expression.  
  
## Result Types  
 DT\_R8  
  
## Remarks  
 The numeric expression is cast to the DT\_R8 data type before the exponent is computed. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 The return result is always a positive number.  
  
## Expression Examples  
 These examples apply the EXP function to positive and negative values and to zero.  
  
```  
EXP(74)  
```  
  
 Returns 1.373382979540176E\+32.  
  
```  
EXP(-27)  
```  
  
 Returns 1.879528816539083E\-12.  
  
```  
EXP(0)  
```  
  
 Returns 1.  
  
## See Also  
 [LOG &#40;SSIS Expression&#41;](../Topic/LOG%20\(SSIS%20Expression\).md)   
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  