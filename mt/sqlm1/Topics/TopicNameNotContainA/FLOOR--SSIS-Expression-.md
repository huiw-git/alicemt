---
title: FLOOR (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
---
# FLOOR (SSIS Expression)
  Returns the largest integer that is less than or equal to a numeric expression.  
  
## Syntax  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## Arguments  
 *numeric\_expression*  
 Is a valid numeric expression.  
  
## Result Types  
 The numeric data type of the argument expression. The result is the integer portion of the calculated value in the same data type as *numeric\_expression.*  
  
## Remarks  
 FLOOR returns a null result if the argument is null.  
  
## Expression Examples  
 These examples apply the FLOOR function to positive, negative, and zero values.  
  
```  
FLOOR(123.45)  
```  
  
 Returns 123.00  
  
```  
FLOOR(-123.45)  
```  
  
 Returns \-124.00  
  
```  
FLOOR(0.00)  
```  
  
 Returns 0.00  
  
## See Also  
 [CEILING &#40;SSIS Expression&#41;](../Topic/CEILING%20\(SSIS%20Expression\).md)   
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  