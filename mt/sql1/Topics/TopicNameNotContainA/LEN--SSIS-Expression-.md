---
title: "LEN (SSIS Expression)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d961398b-e4d0-4936-be17-8f4c5882a640
caps.latest.revision: 37
caps.handback.revision: 0
manager: jhubbard
---
# LEN (SSIS Expression)
Returns the number of characters in a character expression. If the string includes leading and trailing blanks, the function includes them in the count. LEN returns identical values for the same string of single and double byte characters.  
  
## Syntax  
  
```  
  
LEN(character_expression)  
```  
  
## Arguments  
 *character_expression*  
 Is the expression to evaluate.  
  
## Result Types  
 DT_I4  
  
## Remarks  
 The *character_expression* argument can be a DT_WSTR, DT_TEXT, DT_NTEXT, or DT_IMAGE data type. For more information, see [Integration Services Data Types](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 If *character_expression* is a string literal or a data column with the DT_STR data type, it is implicitly cast to the DT_WSTR data type before LEN performs its operation. Other data types must be explicitly cast to the DT_WSTR data type. For more information, see [Cast (SSIS Expression)](../../Topics/TopicNameNotContainA/Cast--SSIS-Expression-.md).  
  
 If the argument passed to the LEN function has a Binary Large Object Block (BLOB) data type, such as DT_TEXT, DT_NTEXT, or DT_IMAGE, the function returns a byte count.  
  
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
 [Functions (SSIS Expression)](../../Topics/TopicNameNotContainA/Functions--SSIS-Expression-.md)