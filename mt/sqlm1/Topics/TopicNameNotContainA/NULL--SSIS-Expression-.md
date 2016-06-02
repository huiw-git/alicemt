---
title: NULL (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df144237-3fbb-41ac-8624-efd92b6522b9
---
# NULL (SSIS Expression)
  Returns a null value of a requested data type.  
  
## Syntax  
  
```  
  
NULL(typespec)  
```  
  
## Arguments  
 *typespec*  
 Is a valid data type. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Result Types  
 Any valid data type with a null value.  
  
## Remarks  
 NULL returns a null result if the argument is null.  
  
 Parameters are required to request a null value for some data types. The following table lists these data types and their parameters.  
  
|Data type|Parameter|Example|  
|---------------|---------------|-------------|  
|DT\_STR|*charcount*<br /><br /> *codepage*|\(DT\_STR,30,1252\) casts 30 characters to the DT\_STR data type using the 1252 code page.|  
|DT\_WSTR|*charcount*|\(DT\_WSTR,20\) casts 20 characters to the DT\_WSTR data type.|  
|DT\_BYTES|*bytecount*|\(DT\_BYTES,50\) casts 50 bytes to the DT\_BYTES data type.|  
|DT\_DECIMAL|*scale*|\(DT\_DECIMAL,2\) casts a numeric value to the DT\_DECIMAL data type using a scale of 2.|  
|DT\_NUMERIC|*precision*<br /><br /> *scale*|\(DT\_NUMERIC,10,3\) casts a numeric value to the DT\_NUMERIC data type using a precision of 10 and a scale of 3.|  
|DT\_TEXT|*codepage*|\(DT\_TEXT,1252\) casts a value to the DT\_TEXT data type using the 1252 code page.|  
  
## Expression Examples  
 These examples return the null value of the data types: DT\_STR, DT\_DATE, and DT\_BOOL.  
  
```  
NULL(DT_STR,10,1252)  
NULL(DT_DATE)  
NULL(DT_BOOL)  
```  
  
## See Also  
 [ISNULL &#40;SSIS Expression&#41;](../Topic/ISNULL%20\(SSIS%20Expression\).md)   
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  