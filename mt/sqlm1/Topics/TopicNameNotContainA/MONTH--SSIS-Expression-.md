---
title: MONTH (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b5a47a11-c2ef-49bd-bd70-235632ff7bf6
---
# MONTH (SSIS Expression)
  Returns an integer that represents the month datepart of a date.  
  
## Syntax  
  
```  
  
MONTH(date)  
```  
  
## Arguments  
 *date*  
 Is a date in any date format.  
  
## Result Types  
 DT\_I4  
  
## Remarks  
 MONTH returns a null result if the argument is null.  
  
 A date literal must be explicitly cast to one of the date data types. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
> [!NOTE]  
>  The expression fails to validate when a date literal is explicitly cast to one of these date data types: DT\_DBTIMESTAMPOFFSET and DT\_DBTIMESTAMP2.  
  
 Using the MONTH function is briefer but equivalent to using DATEPART\("Month", date\).  
  
## Expression Examples  
 This example returns the number of the month in a date literal. If the date is in "mm\/dd\/yyyy" format, this example returns 11.  
  
```  
MONTH((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 This example returns the integer that represents the month in the **ModifiedDate** column.  
  
```  
MONTH(ModifiedDate)  
```  
  
 This example returns the integer that represents the month of the current date.  
  
```  
MONTH(GETDATE())  
```  
  
## See Also  
 [DATEADD &#40;SSIS Expression&#41;](../Topic/DATEADD%20\(SSIS%20Expression\).md)   
 [DATEDIFF &#40;SSIS Expression&#41;](../Topic/DATEDIFF%20\(SSIS%20Expression\).md)   
 [DATEPART &#40;SSIS Expression&#41;](../Topic/DATEPART%20\(SSIS%20Expression\).md)   
 [DAY &#40;SSIS Expression&#41;](../Topic/DAY%20\(SSIS%20Expression\).md)   
 [YEAR &#40;SSIS Expression&#41;](../Topic/YEAR%20\(SSIS%20Expression\).md)   
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  