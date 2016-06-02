---
title: + (Concatenate) (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0fed6334-7a4f-42dc-a611-191fcaa0e443
---
# + (Concatenate) (SSIS Expression)
  Concatenates two expressions into one expression.  
  
## Syntax  
  
```  
  
character_expression1 + character_expression2  
  
```  
  
## Arguments  
 *expression1, expression2*  
 Is any valid DT\_STR, DT\_WSTR, DT\_TEXT, DT\_NTEXT, or DT\_IMAGE data type expression.  
  
## Result Types  
 DT\_WSTR  
  
## Remarks  
 The expression can use either or both of the DT\_STR and DT\_WSTR data types.  
  
 The concatenation of the DT\_STR and DT\_WSTR data types returns a result of the DT\_WSTR type. The length of the string is the sum of the lengths of the original strings expressed in characters.  
  
 Only data with the string data types DT\_STR and DT\_WSTR or the Binary Large Object Block \(BLOB\) data types DT\_TEXT, DT\_NTEXT, and DT\_IMAGE can be concatenated. Other data types must be explicitly converted to one of these data types before concatenation occurs. For more information about legal casts between data types, see [Cast &#40;SSIS Expression&#41;](../Topic/Cast%20\(SSIS%20Expression\).md).  
  
 Both expressions must be of the same data type, or one expression must be implicitly convertible to the data type of the other expression. For example, if the string "Order date is " and the column **OrderDate** are concatenated, the values in **OrderDate** are implicitly converted to a string data type. To concatenate two numeric values, both numeric values must be explicitly cast to a string data type.  
  
 A concatenation can use only one BLOB data type: DT\_TEXT, DT\_NTEXT, or DT\_IMAGE.  
  
 If either element is null, the result is null.  
  
 String literals must be enclosed in quotation marks.  
  
## Expression Examples  
 This example concatenates the values in the **FirstName** and **LastName** columns and inserts a space between them.  
  
```  
FirstName + ' ' + LastName  
```  
  
 This example concatenates the variables **ZIPCode** and **ZIPCode\+4**. Both variables have a string data type. **ZIPCode\+4** must be enclosed in brackets because the variable name includes the \+ character.  
  
```  
@ZIPCcode + "-" + @[ZipCode+4]  
```  
  
## See Also  
 [Operator Precedence and Associativity](../../Topics\TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators &#40;SSIS Expression&#41;](../Topic/Operators%20\(SSIS%20Expression\).md)  
  
  