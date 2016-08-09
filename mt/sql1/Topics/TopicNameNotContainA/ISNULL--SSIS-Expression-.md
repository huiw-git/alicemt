---
title: "ISNULL (SSIS Expression)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
caps.latest.revision: 29
caps.handback.revision: 0
manager: jhubbard
---
# ISNULL (SSIS Expression)
Returns a Boolean result based on whether an expression is null.  
  
## Syntax  
  
```  
  
ISNULL(expression)  
```  
  
## Arguments  
 *expression*  
 Is a valid expression of any data type.  
  
## Result Types  
 DT_BOOL  
  
## Expression Examples  
 This example returns TRUE if the **DiscontinuedDate** column contains a null value.  
  
```  
ISNULL(DiscontinuedDate)  
```  
  
 This example returns "Unknown last name" if the value in the **LastName** column is null, otherwise it returns the value in **LastName**.  
  
```  
ISNULL(LastName)? "Unknown last name":LastName  
```  
  
 This example always returns TRUE if the **DaysToManufacture** column is null, regardless of the value of the variable **AddDays**.  
  
```  
ISNULL(DaysToManufacture + @AddDays)  
```  
  
## See Also  
 [Functions (SSIS Expression)](../../Topics/TopicNameNotContainA/Functions--SSIS-Expression-.md)   
 [COALESCE (Transact-SQL)](assetId:///fafc0dba-f8a8-4aad-9b7f-908e34b74d88)