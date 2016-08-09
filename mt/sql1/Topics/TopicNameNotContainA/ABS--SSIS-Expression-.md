---
title: "ABS (SSIS Expression)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
caps.latest.revision: 29
manager: jhubbard
---
# ABS (SSIS Expression)
Returns the absolute, positive value of a numeric expression.  
  
## Syntax  
  
```  
  
ABS(numeric_expression)  
```  
  
## Arguments  
 *numeric_expression*  
 Is a signed or unsigned numeric expression.  
  
## Result Types  
 The data type of the numeric expression submitted to the function.  
  
## Remarks  
 ABS returns a null result if the argument is null.  
  
## Expression Examples  
 These examples apply the ABS function to a positive and a negative number. Both return 1.23.  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 This example applies the ABS function to an expression that subtracts values in the variables **HighTemperature** and **LowTempature**.  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## See Also  
 [Functions (SSIS Expression)](../../Topics/TopicNameNotContainA/Functions--SSIS-Expression-.md)