---
title: ! (Logical Not) (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
---
# ! (Logical Not) (SSIS Expression)
  Negates a Boolean operand.  
  
> [!NOTE]  
>  The \! operator cannot be used in conjunction with other operators. For example, you cannot combine the \! and the \> operators into the \!\>. operator.  
  
## Syntax  
  
```  
  
!boolean_expression  
  
```  
  
## Arguments  
 *boolean\_expression*  
 Is any valid expression that evaluates to a Boolean. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Result Types  
 DT\_BOOL  
  
## Remarks  
 The following table shows the result of the \! operation.  
  
|Original Boolean expression|After applying the \! operator|  
|---------------------------------|------------------------------------|  
|TRUE|FALSE|  
|NULL|NULL|  
|FALSE|TRUE|  
  
## Expression Examples  
 This example evaluates to FALSE if the **Color** column value is "red".  
  
```  
!(Color == "red")  
```  
  
 This example evaluates to TRUE if the value of the **MonthNumber** variable is the same as the integer that represents the current month. For more information, see [MONTH &#40;SSIS Expression&#41;](../Topic/MONTH%20\(SSIS%20Expression\).md) and [GETDATE &#40;SSIS Expression&#41;](../Topic/GETDATE%20\(SSIS%20Expression\).md).  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## See Also  
 [Operator Precedence and Associativity](../../Topics\TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators &#40;SSIS Expression&#41;](../Topic/Operators%20\(SSIS%20Expression\).md)  
  
  