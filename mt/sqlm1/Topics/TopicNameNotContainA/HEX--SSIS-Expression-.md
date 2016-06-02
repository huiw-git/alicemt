---
title: HEX (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5d471ee-aeef-421c-b6e1-55b9676c3842
---
# HEX (SSIS Expression)
  Returns a string representing the hexadecimal value of an integer.  
  
## Syntax  
  
```  
  
HEX(integer_expression)  
```  
  
## Arguments  
 *integer\_expression*  
 Is a signed or unsigned integer.  
  
## Result Types  
 DT\_WSTR  
  
## Remarks  
 HEX returns null if *integer\_expression* is null.  
  
 The *integer\_expression* argument must evaluate to an integer. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 The return result does not include qualifiers such as the 0x prefix. To include a prefix, use the \+ \(Concatenate\) operator. For more information, see [+ &#40;Concatenate&#41; &#40;SSIS Expression&#41;](../Topic/+%20\(Concatenate\)%20\(SSIS%20Expression\).md).  
  
 The letters A – F, used in HEX notations, appear as uppercase characters.  
  
 The length of the resulting string for integer data types is as follows:  
  
-   DT\_I1 and DT\_UI1 return a string with a maximum length of 2.  
  
-   DT\_I2 and DT\_UI2 return a string with a maximum length of 4.  
  
-   DT\_I4 and DT\_UI4 return a string with a maximum length of 8.  
  
-   DT\_I8 and DT\_UI8 return a string with a maximum length of 16.  
  
## Expression Examples  
 This example uses a numeric literal. The function returns the value 190.  
  
```  
HEX(400)   
```  
  
 This example uses the **ReorderPoint** column. The column data type is **smallint**. If **ReorderPoint** is 750, the function returns 2EE.  
  
```  
HEX(ReorderPoint)   
```  
  
 This example uses **LocaleID**, a system variable. If **LocaleID** is 1033, the function returns 409.  
  
```  
HEX(@LocaleID)  
```  
  
## See Also  
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  