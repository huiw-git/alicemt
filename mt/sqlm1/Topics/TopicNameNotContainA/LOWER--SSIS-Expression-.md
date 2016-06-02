---
title: LOWER (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 109328e1-5604-40ff-895e-f2e7c13fff41
---
# LOWER (SSIS Expression)
  Returns a character expression after converting uppercase characters to lowercase characters.  
  
## Syntax  
  
```  
  
LOWER(character_expression)  
```  
  
## Arguments  
 *character\_expression*  
 Is a character expression to convert to lowercase characters.  
  
## Result Types  
 DT\_WSTR  
  
## Remarks  
 LOWER works only with the DT\_WSTR data type. A *character\_expression* argument that is a string literal or a data column with the DT\_STR data type is implicitly cast to the DT\_WSTR data type before LOWER performs its operation. Other data types must be explicitly cast to the DT\_WSTR data type. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md) and [Cast &#40;SSIS Expression&#41;](../Topic/Cast%20\(SSIS%20Expression\).md).  
  
 LOWER returns a null result if the argument is null.  
  
## Expression Examples  
 This example converts a string literal to lowercase characters. The return result is "new york".  
  
```  
LOWER("New York")  
```  
  
 This example converts all characters from the **Color** input column, except the first character, to lowercase characters. If Color is YELLOW, the return result is "Yellow". For more information, see [SUBSTRING &#40;SSIS Expression&#41;](../Topic/SUBSTRING%20\(SSIS%20Expression\).md).  
  
```  
LOWER(SUBSTRING(Color, 2, 15))  
```  
  
 This example converts the value in the **CityName** variable to lowercase characters.  
  
```  
LOWER(@CityName)  
```  
  
## See Also  
 [UPPER &#40;SSIS Expression&#41;](../Topic/UPPER%20\(SSIS%20Expression\).md)   
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  