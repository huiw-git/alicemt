---
title: LEN (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d961398b-e4d0-4936-be17-8f4c5882a640
---
# LEN (SSIS Expression)
  Returns the number of characters in a character expression. If the string includes leading and trailing blanks, the function includes them in the count. LEN returns identical values for the same string of single and double byte characters.  
  
## Syntax  
  
```  
  
LEN(character_expression)  
```  
  
## Arguments  
 *character\_expression*  
 Is the expression to evaluate.  
  
## Result Types  
 DT\_I4  
  
## Remarks  
 The *character\_expression* argument can be a DT\_WSTR, DT\_TEXT, DT\_NTEXT, or DT\_IMAGE data type. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 If *character\_expression* is a string literal or a data column with the DT\_STR data type, it is implicitly cast to the DT\_WSTR data type before LEN performs its operation. Other data types must be explicitly cast to the DT\_WSTR data type. For more information, see [Cast &#40;SSIS Expression&#41;](../Topic/Cast%20\(SSIS%20Expression\).md).  
  
 If the argument passed to the LEN function has a Binary Large Object Block \(BLOB\) data type, such as DT\_TEXT, DT\_NTEXT, or DT\_IMAGE, the function returns a byte count.  
  
 LEN returns a null result if the argument is null.  
  
## Expression Examples  
 This example returns the length of a string literal. The return result is 12.  
  
```  
LEN("Ball Bearing")  
```  
  
 This example returns the difference between the length of values in the **FirstName** and **LastName** columns.  
  
```  
LEN(FirstName) - LEN(LastName)  
```  
  
 Returns the length of a computer name using the System variable **MachineName**.  
  
```  
LEN(@MachineName)  
```  
  
## See Also  
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  