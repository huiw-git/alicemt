---
title: CEILING (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
---
# CEILING (SSIS Expression)
  Returns the smallest integer that is greater than or equal to a numeric expression.  
  
## Syntax  
  
```  
  
CEILING(numeric_expression)  
```  
  
## Arguments  
 *numeric\_expression*  
 Is a valid numeric expression.  
  
## Result Types  
 The data type of the numeric expression submitted to the function.  
  
## Remarks  
 CEILING returns a null result if the argument is null.  
  
## Expression Examples  
 These examples apply the CEILING function to positive, negative, and zero values.  
  
```  
CEILING(123.74)  
```  
  
 Returns 124.00  
  
```  
CEILING(-124.27)  
```  
  
 Returns \-124.00  
  
```  
CEILING(0.00)  
```  
  
 Returns 0.00  
  
## See Also  
 [FLOOR &#40;SSIS Expression&#41;](../Topic/FLOOR%20\(SSIS%20Expression\).md)   
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  