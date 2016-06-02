---
title: LTRIM (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d082f42a-d7e7-49f5-a503-ac44ba630832
---
# LTRIM (SSIS Expression)
  Returns a character expression after removing leading spaces.  
  
> [!NOTE]  
>  LTRIM does not remove white\-space characters such as the tab or line feed characters. Unicode provides code points for many different types of spaces, but this function recognizes only the Unicode code point 0x0020. When double\-byte character set \(DBCS\) strings are converted to Unicode they may include space characters other than 0x0020 and the function cannot remove such spaces. To remove all kinds of spaces, you can use the Microsoft Visual Basic .NET LTrim method in a script run from the Script component.  
  
## Syntax  
  
```  
  
LTRIM(character expression)  
```  
  
## Arguments  
 *character\_expression*  
 Is a character expression from which to remove spaces.  
  
## Result Types  
 DT\_WSTR  
  
## Remarks  
 LTRIM works only with the DT\_WSTR data type. A *character\_expression* argument that is a string literal or a data column with the DT\_STR data type is implicitly cast to the DT\_WSTR data type before LTRIM performs its operation. Other data types must be explicitly cast to the DT\_WSTR data type. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md) and [Cast &#40;SSIS Expression&#41;](../Topic/Cast%20\(SSIS%20Expression\).md).  
  
 LTRIM returns a null result if the argument is null.  
  
## Expression Examples  
 This example removes leading spaces from a string literal. The return result is "Hello".  
  
```  
LTRIM("    Hello")  
```  
  
 This example removes leading spaces from the **FirstName** column.  
  
```  
LTRIM(FirstName)  
```  
  
 This example removes leading spaces from the **FirstName** variable.  
  
```  
LTRIM(@FirstName)  
```  
  
## See Also  
 [RTRIM &#40;SSIS Expression&#41;](../Topic/RTRIM%20\(SSIS%20Expression\).md)   
 [TRIM &#40;SSIS Expression&#41;](../Topic/TRIM%20\(SSIS%20Expression\).md)   
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  