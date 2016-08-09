---
title: "REPLACE (SSIS Expression)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a6837043-ea70-4c6a-9c7a-6868b02b2adc
caps.latest.revision: 42
caps.handback.revision: 0
manager: jhubbard
---
# REPLACE (SSIS Expression)
Returns a character expression after replacing a character string within the expression with either a different character string or an empty string.  
  
> [!NOTE]  
>  The REPLACE function frequently uses long strings. The consequences of truncation can be handled gracefully or cause a warning or an error. For more information, see [Syntax (SSIS)](../../Topics/TopicNameNotContainA/Syntax--SSIS-.md).  
  
## Syntax  
  
```  
  
REPLACE(character_expression,searchstring,replacementstring)  
```  
  
## Arguments  
 *character_expression*  
 Is a valid character expression that the function searches.  
  
 *searchstring*  
 Is a valid character expression that the function attempts to locate.  
  
 *replacementstring*  
 Is a valid character expression that is the replacement expression.  
  
## Result Types  
 DT_WSTR  
  
## Remarks  
 The length of *searchstring* must not be zero.  
  
 The length of *replacementstring* may be zero.  
  
 The *searchstring* and *replacementstring* arguments can use variables and columns.  
  
 REPLACE works only with the DT_WSTR data type. *character_expression1, character_expression2,* and *character_expression3* arguments that are string literals or data columns with the DT_STR data type are implicitly cast to the DT_WSTR data type before REPLACE performs its operation. Other data types must be explicitly cast to the DT_WSTR data type. For more information, see [Cast (SSIS Expression)](../../Topics/TopicNameNotContainA/Cast--SSIS-Expression-.md).  
  
 REPLACE returns a null result if any argument is null.  
  
## Expression Examples  
 This example uses a string literal. The return result is "All Terrain Bike".  
  
```  
REPLACE("Mountain Bike", "Mountain","All Terrain")  
```  
  
 This example removes the string "Bike" from the **Product** column.  
  
```  
REPLACE(Product, "Bike","")  
```  
  
 This example replaces values in the **DaysToManufacture** column. The column has an integer data type and the expression includes casting **DaysToManufacture** to the DT_WSTR data type.  
  
```  
REPLACE((DT_WSTR,8)DaysToManufacture,"6","5")  
```  
  
## See Also  
 [SUBSTRING (SSIS Expression)](../../Topics/TopicNameNotContainA/SUBSTRING--SSIS-Expression-.md)   
 [Functions (SSIS Expression)](../../Topics/TopicNameNotContainA/Functions--SSIS-Expression-.md)