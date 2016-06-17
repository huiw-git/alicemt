---
title: DATEPART (SSIS Expression)
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3e590094-fc49-4144-805f-fdc1bf2fe509
---
# DATEPART (SSIS Expression)
  Returns an integer representing a datepart of a date.  
  
## Syntax  
  
```  
  
DATEPART(datepart, date)  
```  
  
## Arguments  
 *datepart*  
 Is the parameter that specifies for which part of the date to return a new value.  
  
 *date*  
 Is an expression that returns a valid date or a string in date format.  
  
## Result Types  
 DT\_I4  
  
## Remarks  
 DATEPART returns a null result if the argument is null.  
  
 A date literal must be explicitly cast to one of the date data types. For more information, see [Integration Services Data Types](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 The following table lists the dateparts and abbreviations recognized by the expression evaluator. Datepart names are not case sensitive.  
  
|Datepart|Abbreviations|  
|--------------|-------------------|  
|Year|yy, yyyy|  
|Quarter|qq, q|  
|Month|mm, m|  
|Dayofyear|dy, y|  
|Day|dd, d|  
|Week|wk, ww|  
|Weekday|dw|  
|Hour|Hh|  
|Minute|mi, n|  
|Second|ss, s|  
|Millisecond|Ms|  
  
## SSIS Expression Examples  
 This example returns the integer that represents the month in a date literal. If the date is in mm\/dd\/yyyy" format, this example returns 11.  
  
```  
DATEPART("month", (DT_DBTIMESTAMP)"11/04/2002")  
```  
  
 This example returns the integer that represents the day in the **ModifiedDate** column.  
  
```  
DATEPART("dd", ModifiedDate)  
```  
  
 This example returns the integer that represents the year of the current date.  
  
```  
DATEPART("yy",GETDATE())  
```  
  
## See Also  
 [DATEADD &#40;SSIS Expression&#41;](../../Topics/TopicNameNotContainA/DATEADD--SSIS-Expression-.md)   
 [DATEDIFF &#40;SSIS Expression&#41;](../../Topics/TopicNameNotContainA/DATEDIFF--SSIS-Expression-.md)   
 [DAY &#40;SSIS Expression&#41;](../../Topics/TopicNameNotContainA/DAY--SSIS-Expression-.md)   
 [MONTH &#40;SSIS Expression&#41;](../../Topics/TopicNameNotContainA/MONTH--SSIS-Expression-.md)   
 [YEAR &#40;SSIS Expression&#41;](../../Topics/TopicNameNotContainA/YEAR--SSIS-Expression-.md)   
 [Functions &#40;SSIS Expression&#41;](../../Topics/TopicNameNotContainA/Functions--SSIS-Expression-.md)  
  
  