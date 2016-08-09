---
title: "GETUTCDATE (SSIS Expression)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
caps.latest.revision: 33
manager: jhubbard
---
# GETUTCDATE (SSIS Expression)
Returns the current date of the system in UTC time (Universal Time Coordinate or Greenwich Mean Time) using a DT_DBTIMESTAMP format. The GETUTCDATE function takes no arguments.  
  
## Syntax  
  
```  
  
GETUTCDATE()  
```  
  
## Arguments  
 None  
  
## Result Types  
 DT_DBTIMESTAMP  
  
## Expression Examples  
 This example returns the year of the current date in UTC time.  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 This example returns the number of days between a date in the **ModifiedDate** column and the current UTC date.  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 This example adds three months to the current UTC date.  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## See Also  
 [GETDATE (SSIS Expression)](../../Topics/TopicNameNotContainA/GETDATE--SSIS-Expression-.md)   
 [Functions (SSIS Expression)](../../Topics/TopicNameNotContainA/Functions--SSIS-Expression-.md)