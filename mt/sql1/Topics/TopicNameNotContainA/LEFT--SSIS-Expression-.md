---
title: "LEFT (SSIS Expression)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5634dbfb-740d-4c93-8fd5-2854cc741327
caps.latest.revision: 13
caps.handback.revision: 0
manager: jhubbard
---
# LEFT (SSIS Expression)
Returns the specified number of characters from the leftmost portion of the given character expression.  
  
## Syntax  
  
```  
  
LEFT(character_expression,number)  
```  
  
## Arguments  
 *character_expression*  
 Is a character expression from which to extract characters.  
  
 *number*  
 Is an integer expression that indicates the number of characters to be returned.  
  
## Result Types  
 DT_WSTR  
  
## Remarks  
 If *number* is greater than the length of *character_expression*, the function returns *character_expression*.  
  
 If *number* is zero, the function returns a zero-length string.  
  
 If *number* is a negative number, the function returns an error.  
  
 The *number* argument can take variables and columns.  
  
 LEFT works only with the DT_WSTR data type. A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before LEFT performs its operation. Other data types must be explicitly cast to the DT_WSTR data type. For more information, see [Integration Services Data Types](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types.md) and [Cast (SSIS Expression)](../../Topics/TopicNameNotContainA/Cast--SSIS-Expression-.md).  
  
 LEFT returns a null result if either argument is null.  
  
## Expression Examples  
 The following example uses a string literal. The return result is `"Mountain"`.  
  
```  
LEFT("Mountain Bike", 8)  
```  
  
## See Also  
 [RIGHT (SSIS Expression)](../../Topics/TopicNameNotContainA/RIGHT--SSIS-Expression-.md)   
 [Functions (SSIS Expression)](../../Topics/TopicNameNotContainA/Functions--SSIS-Expression-.md)