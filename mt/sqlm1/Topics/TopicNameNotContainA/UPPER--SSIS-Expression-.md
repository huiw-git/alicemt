---
title: UPPER (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d33985f7-1048-4023-83e4-274090acda78
---
# UPPER (SSIS Expression)
  Returns a character expression after converting lowercase characters to uppercase characters.  
  
## Syntax  
  
```  
  
UPPER(character_expression)  
```  
  
## Arguments  
 *character\_expression*  
 Is a character expression to convert to uppercase characters.  
  
## Result Types  
 DT\_WSTR  
  
## Remarks  
 UPPER works only with the DT\_WSTR data type. A *character\_expression* argument that is a string literal or a data column with the DT\_STR data type is implicitly cast to the DT\_WSTR data type before UPPER performs its operation. Other data types must be explicitly cast to the DT\_WSTR data type. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md) and [Cast &#40;SSIS Expression&#41;](../Topic/Cast%20\(SSIS%20Expression\).md).  
  
 UPPER returns a null result if the argument is null.  
  
## Expression Examples  
 This example converts a string literal to uppercase characters. The return result is "HELLO".  
  
```  
UPPER("hello")  
```  
  
 This example converts the first character in the **FirstName** column to an uppercase character. If **FirstName** is anna, the return result is "A". For more information, see [SUBSTRING &#40;SSIS Expression&#41;](../Topic/SUBSTRING%20\(SSIS%20Expression\).md).  
  
```  
UPPER(SUBSTRING(FirstName, 1, 1))  
```  
  
 This example converts the value in the **PostalCode** variable to uppercase characters. If **PostalCode** is k4b1s2, the return result is "K4B1S2".  
  
```  
UPPER(@PostalCode)  
```  
  
## See Also  
 [LOWER &#40;SSIS Expression&#41;](../Topic/LOWER%20\(SSIS%20Expression\).md)   
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  