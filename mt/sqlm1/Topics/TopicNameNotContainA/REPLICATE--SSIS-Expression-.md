---
title: REPLICATE (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e7a37b93-6d1d-42d5-9a65-de1790abf6a5
---
# REPLICATE (SSIS Expression)
  Returns a character expression that is replicated a number of times. The *times* argument must evaluate to an integer.  
  
> [!NOTE]  
>  The REPLICATE function frequently uses long strings, and therefore is more likely to incur the 4000\-character limit on expression length. If the evaluation result of an expression has the Integration Services data type DT\_WSTR or DT\_STR, the expression will be truncated at 4000 characters. If the result type of a sub\-expression is DT\_STR or DT\_WSTR, that sub\-expression likewise will be truncated to 4000 characters, regardless of the overall expression result type. The consequences of truncation can be handled gracefully or cause a warning or an error. For more information, see [Syntax &#40;SSIS&#41;](../Topic/Syntax%20\(SSIS\).md).  
  
## Syntax  
  
```  
  
REPLICATE(character_expression,times)  
```  
  
## Arguments  
 *character\_expression*  
 Is a character expression to replicate.  
  
 *times*  
 Is an integer expression that specifies the number of times *character\_expression* is replicated.  
  
## Result Types  
 DT\_WSTR  
  
## Remarks  
 If *times* is zero, the function returns a zero\-length string.  
  
 If *times* is a negative number, the function returns an error.  
  
 The *times* argument can also use variables and columns.  
  
 REPLICATE works only with the DT\_WSTR data type. A *character\_expression* argument that is a string literal or a data column with the DT\_STR data type is implicitly cast to the DT\_WSTR data type before REPLICATE performs its operation. Other data types must be explicitly cast to the DT\_WSTR data type. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md) and [Cast &#40;SSIS Expression&#41;](../Topic/Cast%20\(SSIS%20Expression\).md).  
  
 REPLICATE returns a null result if either argument is null.  
  
## Expression Examples  
 This example replicates a string literal three times. The return result is "Mountain BikeMountain BikeMountain Bike".  
  
```  
REPLICATE("Mountain Bike", 3)  
```  
  
 This example replicates values in the **Name** column by the value in the **Times** variable. If **Times** is 3 and **Name** is Touring Front Wheel, the return result is Touring Front WheelTouring Front WheelTouring Front Wheel.  
  
```  
REPLICATE(Name, @Times)  
```  
  
 This example replicates the value in the **Name** variable by the value in the **Times** column. **Times** has a non\-integer data type and the expression includes an explicit cast to an integer data type. If **Name** contains Helmet and **Times** is 2, the return result is "HelmetHelmet".  
  
```  
REPLICATE(@Name, (DT_I4(Times))  
```  
  
## See Also  
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  