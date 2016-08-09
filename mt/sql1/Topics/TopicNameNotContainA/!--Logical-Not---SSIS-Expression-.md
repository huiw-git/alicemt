---
title: "! (Logical Not) (SSIS Expression)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
caps.latest.revision: 36
caps.handback.revision: 0
manager: jhubbard
---
# ! (Logical Not) (SSIS Expression)
Negates a Boolean operand.  
  
> [!NOTE]  
>  The ! operator cannot be used in conjunction with other operators. For example, you cannot combine the ! and the > operators into the !>. operator.  
  
## Syntax  
  
```  
  
!boolean_expression  
  
```  
  
## Arguments  
 *boolean_expression*  
 Is any valid expression that evaluates to a Boolean. For more information, see [Integration Services Data Types](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Result Types  
 DT_BOOL  
  
## Remarks  
 The following table shows the result of the ! operation.  
  
|Original Boolean expression|After applying the ! operator|  
|---------------------------------|------------------------------------|  
|TRUE|FALSE|  
|NULL|NULL|  
|FALSE|TRUE|  
  
## Expression Examples  
 This example evaluates to FALSE if the **Color** column value is "red".  
  
```  
!(Color == "red")  
```  
  
 This example evaluates to TRUE if the value of the **MonthNumber** variable is the same as the integer that represents the current month. For more information, see [MONTH (SSIS Expression)](../../Topics/TopicNameNotContainA/MONTH--SSIS-Expression-.md) and [GETDATE (SSIS Expression)](../../Topics/TopicNameNotContainA/GETDATE--SSIS-Expression-.md).  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## See Also  
 [Operator Precedence and Associativity](../../Topics/TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators (SSIS Expression)](../../Topics/TopicNameNotContainA/Operators--SSIS-Expression-.md)