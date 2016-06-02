---
title: RIGHT (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 83e70e75-4be5-4783-a8cf-032f82afe16e
---
# RIGHT (SSIS Expression)
  Returns the specified number of characters from the rightmost portion of the given character expression.  
  
## Syntax  
  
```  
  
RIGHT(character_expression,integer_expression)  
```  
  
## Arguments  
 *character\_expression*  
 Is a character expression from which to extract characters.  
  
 *integer\_expression*  
 Is an integer expression that indicates the number of characters to be returned.  
  
## Result Types  
 DT\_WSTR  
  
## Remarks  
 If *integer\_expression* is greater than the length of *character\_expression*, the function returns *character\_expression*.  
  
 If *integer\_expression* is zero, the function returns a zero\-length string.  
  
 If *integer\_expression* is a negative number, the function returns an error.  
  
 The *integer\_expression* argument can take variables and columns.  
  
 RIGHT works only with the DT\_WSTR data type. A *character\_expression* argument that is a string literal or a data column with the DT\_STR data type is implicitly cast to the DT\_WSTR data type before RIGHT performs its operation. Other data types must be explicitly cast to the DT\_WSTR data type. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md) and [Cast &#40;SSIS Expression&#41;](../Topic/Cast%20\(SSIS%20Expression\).md).  
  
 RIGHT returns a null result if either argument is null.  
  
## Expression Examples  
 The following example uses a string literal. The return result is `"Bike"`.  
  
```  
RIGHT("Mountain Bike", 4)  
```  
  
 The following example returns the number of rightmost characters that is specified in the `Times` variable, from the `Name` column. If `Name` is `Touring Front Wheel` and `Times` is 5, the return result is `"Wheel"`.  
  
```  
RIGHT(Name, @Times)  
```  
  
 The following example also returns the number of rightmost characters that is specified in the `Times` variable, from the `Name` column. `Times` has a noninteger data type and the expression includes an explicit cast to the DT\_I2 data type. If `Name` is `Touring Front Wheel` and `Times` is `4.32`, the return result is `"heel"` because the RIGHT function converts the value of 4.32 to 4, and then returns the rightmost four characters.  
  
```  
RIGHT(Name, (DT_I2)@Times))  
```  
  
## See Also  
 [LEFT &#40;SSIS Expression&#41;](../Topic/LEFT%20\(SSIS%20Expression\).md)   
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  