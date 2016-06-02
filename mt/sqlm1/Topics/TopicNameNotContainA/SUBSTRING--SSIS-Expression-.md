---
title: SUBSTRING (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a46748a-f5f8-4a6c-9108-673666754068
---
# SUBSTRING (SSIS Expression)
  Returns the part of a character expression that starts at the specified position and has the specified length. The *position* parameter and the *length* parameter must evaluate to integers.  
  
## Syntax  
  
```  
  
SUBSTRING(character_expression, position, length)  
```  
  
## Arguments  
 *character\_expression*  
 Is a character expression from which to extract characters.  
  
 *position*  
 Is an integer that specifies where the substring begins.  
  
 *length*  
 Is an integer that specifies the length of the substring as number of characters.  
  
## Result Types  
 DT\_WSTR  
  
## Remarks  
 SUBSTRING uses a one\-based index. If *position* is 1, the substring begins with the first character in *character\_expression*.  
  
 SUBSTRING works only with the DT\_WSTR data type. A *character\_expression* argument that is a string literal or a data column with the DT\_STR data type is implicitly cast to the DT\_WSTR data type before SUBSTRING performs its operation. Other data types must be explicitly cast to the DT\_WSTR data type. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md) and [Cast &#40;SSIS Expression&#41;](../Topic/Cast%20\(SSIS%20Expression\).md).  
  
 SUBSTRING returns a null result if the argument is null.  
  
 All arguments in the expression can use variables and columns.  
  
 The *length* argument can exceed the length of the string. In that case, the function returns the remainder of the string.  
  
## Expression Examples  
 This example returns two characters, beginning with character 4, from a string literal. The return result is "ph".  
  
```  
SUBSTRING("elephant",4,2)  
```  
  
 This example returns the remainder of a string literal, beginning at the fourth character. The return result is "phant". It is not an error for the *length* argument to exceed the length of the string.  
  
```  
SUBSTRING ("elephant",4,50)  
```  
  
 This example returns the first letter from the **MiddleName** column.  
  
```  
SUBSTRING(MiddleName,1,1)  
```  
  
 This example uses variables in the *position* and *length* arguments. If **Start** is 1 and **Length** is 5, the function returns the first five characters in the **Name** column.  
  
```  
SUBSTRING(Name,@Start,@Length)  
```  
  
 This example returns the last four characters from the **PostalCode** variable beginning at the sixth character.  
  
```  
SUBSTRING (@PostalCode,6,4)  
```  
  
 This example returns a zero\-length string from a string literal.  
  
```  
SUBSTRING ("Redmond",4,0)  
```  
  
## See Also  
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  