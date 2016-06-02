---
title: GETDATE (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
---
# GETDATE (SSIS Expression)
  Returns the current date of the system in a DT\_DBTIMESTAMP format. The GETDATE function takes no arguments.  
  
> [!NOTE]  
>  The length of the return result from the GETDATE function is 29 characters.  
  
## Syntax  
  
```  
  
GETDATE()  
```  
  
## Arguments  
 None  
  
## Result Types  
 DT\_DBTIMESTAMP  
  
## Expression Examples  
 This example returns the year of the current date.  
  
```  
DATEPART("year",GETDATE())  
```  
  
 This example returns the number of days between a date in the **ModifiedDate** column and the current date.  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 This example adds three months to the current date.  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## See Also  
 [GETUTCDATE &#40;SSIS Expression&#41;](../Topic/GETUTCDATE%20\(SSIS%20Expression\).md)   
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  