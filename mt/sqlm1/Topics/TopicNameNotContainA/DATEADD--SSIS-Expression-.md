---
title: DATEADD (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fa5c37b1-2ddc-4857-8f8e-f6d5643b654f
---
# DATEADD (SSIS Expression)
  Returns a new DT\_DBTIMESTAMP value after adding a number that represents a date or time interval to the specified datepart in a date. The number parameter must evaluate to an integer, and the date parameter must evaluate to a valid date.  
  
## Syntax  
  
```  
  
DATEADD(datepart, number, date)  
```  
  
## Arguments  
 *datepart*  
 Is the parameter that specifies which part of the date to add a number to.  
  
 *number*  
 Is the value used to increment *datepart*. The value must be an integer value that is known when the expression is parsed.  
  
 *date*  
 Is an expression that returns a valid date or a string in date format.  
  
## Result Types  
 DT\_DBTIMESTAMP  
  
## Remarks  
 The following table lists the dateparts and abbreviations recognized by the expression evaluator. Datepart names are not case sensitive.  
  
|Datepart|Abbreviations|  
|--------------|-------------------|  
|Year|yy, yyyy|  
|Quarter|qq, q|  
|Month|mm, m|  
|Dayofyear|dy, y|  
|Day|dd, d|  
|Week|wk, ww|  
|Weekday|dw, w|  
|Hour|Hh|  
|Minute|mi, n|  
|Second|ss, s|  
|Millisecond|Ms|  
  
 The *number* argument must be available when the expression is parsed. The argument can be a constant or a variable. You cannot use column values because the values are not known when the expression is parsed.  
  
 The *datepart* argument must be enclosed by quotation marks.  
  
 A date literal must be explicitly cast to one of the date data types. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 DATEADD returns a null result if the argument is null.  
  
 Errors occur if a date is invalid, if the date or time unit is not a string, or if the increment is not a static integer.  
  
## SSIS Expression Examples  
 This example adds one month to the current date.  
  
```  
DATEADD("Month", 1,GETDATE())  
```  
  
 This example adds 21 days to the dates in the **ModifiedDate** column.  
  
```  
DATEADD("day", 21, ModifiedDate)  
```  
  
 This example adds 2 years to a literal date.  
  
```  
DATEADD("yyyy", 2, (DT_DBTIMESTAMP)"8/6/2003")  
```  
  
## See Also  
 [DATEDIFF &#40;SSIS Expression&#41;](../Topic/DATEDIFF%20\(SSIS%20Expression\).md)   
 [DATEPART &#40;SSIS Expression&#41;](../Topic/DATEPART%20\(SSIS%20Expression\).md)   
 [DAY &#40;SSIS Expression&#41;](../Topic/DAY%20\(SSIS%20Expression\).md)   
 [MONTH &#40;SSIS Expression&#41;](../Topic/MONTH%20\(SSIS%20Expression\).md)   
 [YEAR &#40;SSIS Expression&#41;](../Topic/YEAR%20\(SSIS%20Expression\).md)   
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  