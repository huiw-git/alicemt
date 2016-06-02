---
title: LOG (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7fccace-c178-4e13-bde9-7dc4ef1d98fa
---
# LOG (SSIS Expression)
  Returns the base\-10 logarithm of a numeric expression.  
  
## Syntax  
  
```  
  
LOG(numeric_expression)  
```  
  
## Arguments  
 *numeric\_expression*  
 Is a valid nonzero or nonnegative numeric expression.  
  
## Result Types  
 DT\_R8  
  
## Remarks  
 The *numeric expression* is cast to the DT\_R8 data type before the logarithm is computed. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 If *numeric\_expression* evaluates to zero or a negative value, the return result is null.  
  
## Expression Examples  
 This example uses a numeric literal. The function returns the value 1.988291341907488.  
  
```  
LOG(97.34)  
```  
  
 This example uses the column **Length**. If the column is 101.24, the function returns 2.005352136486217.  
  
```  
LOG(Length)   
```  
  
 This example uses the variable **Length**. The variable must have a numeric data type or the expression must include an explicit cast to a numeric [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] data type. If **Length** is 234.567, the function returns 2.370266913465859.  
  
```  
LOG(@Length)   
```  
  
## See Also  
 [EXP &#40;SSIS Expression&#41;](../Topic/EXP%20\(SSIS%20Expression\).md)   
 [LN &#40;SSIS Expression&#41;](../Topic/LN%20\(SSIS%20Expression\).md)   
 [Functions &#40;SSIS Expression&#41;](../Topic/Functions%20\(SSIS%20Expression\).md)  
  
  