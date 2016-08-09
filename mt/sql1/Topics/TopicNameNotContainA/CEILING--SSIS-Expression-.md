---
title: "CEILING (SSIS Expression)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
caps.latest.revision: 29
caps.handback.revision: 0
manager: jhubbard
---
# CEILING (SSIS Expression)
Returns the smallest integer that is greater than or equal to a numeric expression.  
  
## Syntax  
  
```  
  
CEILING(numeric_expression)  
```  
  
## Arguments  
 *numeric_expression*  
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
  
 Returns -124.00  
  
```  
CEILING(0.00)  
```  
  
 Returns 0.00  
  
## See Also  
 [FLOOR (SSIS Expression)](../../Topics/TopicNameNotContainA/FLOOR--SSIS-Expression-.md)   
 [Functions (SSIS Expression)](../../Topics/TopicNameNotContainA/Functions--SSIS-Expression-.md)