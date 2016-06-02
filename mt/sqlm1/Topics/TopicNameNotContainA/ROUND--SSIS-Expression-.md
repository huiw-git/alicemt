---
title: ROUND (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 376f1947-4fc5-4611-ad86-823e4db1b468
---
# ROUND (SSIS Expression)
  Returns a numeric expression that is rounded to the specified length or precision. The length parameter must evaluate to an integer.  
  
## Syntax  
  
```  
  
ROUND(numeric_expression,length)  
```  
  
## Arguments  
 *numeric\_expression*  
 Is an expression of a valid numeric type. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 *length*  
 Is an integer expression. It is the precision to which *numeric\_expression* is rounded.  
  
## Result Types  
 The same type as *numeric*\_*expression.*  
  
## Remarks  
 The *length* argument must evaluate to a positive integer or zero.  
  
 ROUND returns a null result if the argument is null.  
  
## Expression Examples  
 These examples round numeric literals to a length of three. The first return result is 137.1570, the second 137.1580.  
  
```  
ROUND(137.1574,3)  
ROUND(137.1575,3)  
```  
  
## See Also  
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  