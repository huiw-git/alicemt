---
title: REVERSE (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
---
# REVERSE (SSIS Expression)
  Returns a character expression in reverse order.  
  
## Syntax  
  
```  
  
REVERSE(character_expression)  
```  
  
## Arguments  
 *character\_expression*  
 Is a character expression to be reversed.  
  
## Result Types  
 DT\_WSTR  
  
## Remarks  
 The *character\_expression* argument must have the DT\_WSTR data type.  
  
 REVERSE returns a null result if *character\_expression* is null.  
  
## Expression Examples  
 This example uses a string literal. The return result is "ekiB niatnuoM".  
  
```  
REVERSE("Mountain Bike")  
```  
  
 This example uses a variable. If **Name** contains Touring Bike, the return result is "ekiB gniruoT".  
  
```  
REVERSE(@Name)  
```  
  
## See Also  
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  