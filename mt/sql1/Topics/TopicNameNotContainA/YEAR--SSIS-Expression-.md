---
title: "YEAR (SSIS Expression)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9d88dead-ace8-44b9-b8e2-916c1842e155
caps.latest.revision: 36
caps.handback.revision: 0
manager: jhubbard
---
# YEAR (SSIS Expression)
Returns an integer that represents the year datepart of a date.  
  
## Syntax  
  
```  
  
YEAR(date)  
```  
  
## Arguments  
 *date*  
 Is a date in any date format.  
  
## Result Types  
 DT_I4  
  
## Remarks  
 YEAR returns a null result if the argument is null.  
  
 A date literal must be explicitly cast to one of the date data types. For more information, see [Integration Services Data Types](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
> [!NOTE]  
>  The expression fails to validate when a date literal is explicitly cast to one of these date data types: DT_DBTIMESTAMPOFFSET and DT_DBTIMESTAMP2.  
  
 Using the YEAR function is briefer but equivalent to using the DATEPART("Year", date) function.  
  
## Expression Examples  
 This example returns the number of the year in a date literal. If the date is in mm/dd/yyyy format, this example returns "2002".  
  
```  
YEAR((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 This example returns the integer that represents the year in the **ModifiedDate** column.  
  
```  
YEAR(ModifiedDate)  
```  
  
 This example returns the integer that represents the year of the current date.  
  
```  
YEAR(GETDATE())  
```  
  
## See Also  
 [DATEADD (SSIS Expression)](../../Topics/TopicNameNotContainA/DATEADD--SSIS-Expression-.md)   
 [DATEDIFF (SSIS Expression)](../../Topics/TopicNameNotContainA/DATEDIFF--SSIS-Expression-.md)   
 [DATEPART (SSIS Expression)](../../Topics/TopicNameNotContainA/DATEPART--SSIS-Expression-.md)   
 [DAY (SSIS Expression)](../../Topics/TopicNameNotContainA/DAY--SSIS-Expression-.md)   
 [MONTH (SSIS Expression)](../../Topics/TopicNameNotContainA/MONTH--SSIS-Expression-.md)   
 [Functions (SSIS Expression)](../../Topics/TopicNameNotContainA/Functions--SSIS-Expression-.md)