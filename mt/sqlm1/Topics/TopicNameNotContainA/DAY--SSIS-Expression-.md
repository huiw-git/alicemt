---
title: DAY (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d8447187-49df-45b7-a98e-142ad44fd3e2
---
# DAY (SSIS Expression)
  Returns an integer that represents the day datepart of a date.  
  
## Syntax  
  
```  
  
DAY(date)  
```  
  
## Arguments  
 *date*  
 Is an expression that returns a valid date or a string in date format.  
  
## Result Types  
 DT\_I4  
  
## Remarks  
 DAY returns a null result if the argument is null.  
  
 A date literal must be explicitly cast to one of the date data types. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
> [!NOTE]  
>  The expression fails to validate when a date literal is explicitly cast to one of these date data types: DT\_DBTIMESTAMPOFFSET and DT\_DBTIMESTAMP2.  
  
 Using the DAY function is briefer but equivalent to using DATEPART\("Day", date\).  
  
## Expression Examples  
 This example returns the number of the day in a date literal. If the date format is in "mm\/dd\/yyyy" format, this example returns 23.  
  
```  
DAY((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 This example returns the integer that represents the day in the **ModifiedDate** column.  
  
```  
DAY(ModifiedDate)  
```  
  
 This example returns the integer that represents the day of the current date.  
  
```  
DAY(GETDATE())  
```  
  
## See Also  
 [DATEADD &#40;SSIS Expression&#41;](../Topic/DATEADD%20\(SSIS%20Expression\).md)   
 [DATEDIFF &#40;SSIS Expression&#41;](../Topic/DATEDIFF%20\(SSIS%20Expression\).md)   
 [DATEPART &#40;SSIS Expression&#41;](../Topic/DATEPART%20\(SSIS%20Expression\).md)   
 [MONTH &#40;SSIS Expression&#41;](../Topic/MONTH%20\(SSIS%20Expression\).md)   
 [YEAR &#40;SSIS Expression&#41;](../Topic/YEAR%20\(SSIS%20Expression\).md)   
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  