---
title: "SIGN (SSIS Expression)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
caps.latest.revision: 33
manager: jhubbard
---
# SIGN (SSIS Expression)
Returns the positive (+1), negative (-1), or zero (0) sign of a numeric expression.  
  
## Syntax  
  
```  
  
SIGN(numeric_expression)  
```  
  
## Arguments  
 *numeric_expression*  
 Is a valid signed numeric expression. For more information, see [Integration Services Data Types](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Result Types  
 DT_I4  
  
## Remarks  
 SIGN returns a null result if the argument is null.  
  
## Expression Examples  
 This example returns the sign of a numeric literal. The return result is -1.  
  
```  
SIGN(-123.45)  
```  
  
 This example returns the sign of the result of subtracting the **StandardCost** column from the **DealerPrice** column.  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## See Also  
 [Functions (SSIS Expression)](../../Topics/TopicNameNotContainA/Functions--SSIS-Expression-.md)