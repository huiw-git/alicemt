---
title: LEFT (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5634dbfb-740d-4c93-8fd5-2854cc741327
---
# LEFT (SSIS Expression)
  Returns the specified number of characters from the leftmost portion of the given character expression.  
  
## Syntax  
  
```  
  
LEFT(character_expression,number)  
```  
  
## Arguments  
 *character\_expression*  
 Is a character expression from which to extract characters.  
  
 *number*  
 Is an integer expression that indicates the number of characters to be returned.  
  
## Result Types  
 DT\_WSTR  
  
## Remarks  
 If *number* is greater than the length of *character\_expression*, the function returns *character\_expression*.  
  
 If *number* is zero, the function returns a zero\-length string.  
  
 If *number* is a negative number, the function returns an error.  
  
 The *number* argument can take variables and columns.  
  
 LEFT works only with the DT\_WSTR data type. A *character\_expression* argument that is a string literal or a data column with the DT\_STR data type is implicitly cast to the DT\_WSTR data type before LEFT performs its operation. Other data types must be explicitly cast to the DT\_WSTR data type. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md) and [Cast &#40;SSIS Expression&#41;](../Topic/Cast%20\(SSIS%20Expression\).md).  
  
 LEFT returns a null result if either argument is null.  
  
## Expression Examples  
 The following example uses a string literal. The return result is `"Mountain"`.  
  
```  
LEFT("Mountain Bike", 8)  
```  
  
## See Also  
 [RIGHT &#40;SSIS Expression&#41;](../Topic/RIGHT%20\(SSIS%20Expression\).md)   
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  