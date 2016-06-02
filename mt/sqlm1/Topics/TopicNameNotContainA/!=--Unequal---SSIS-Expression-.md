---
title: != (Unequal) (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fad20e85-c0e6-42bf-af70-2bc80ee09be5
---
# != (Unequal) (SSIS Expression)
  Performs a comparison to determine if two expressions with compatible data types are not equal. The expression evaluator automatically converts many data types before it performs the comparison.  
  
 However, some data types require that the expression include an explicit cast before the expression can be evaluated successfully. For more information about legal casts between data types, see [Cast &#40;SSIS Expression&#41;](../Topic/Cast%20\(SSIS%20Expression\).md).  
  
## Syntax  
  
```  
  
expression1 != expression2  
  
```  
  
## Arguments  
 *expression1, expression2*  
 Is any valid expression.  
  
## Result Types  
 DT\_BOOL  
  
## Remarks  
 If either expression in the comparison is null, the comparison result is null. If both expressions are null, the result is null.  
  
 The expression set, *expression1* and *expression2*, must follow one of these rules:  
  
-   **Numeric** Both *expression1* and *expression2* must be a numeric data type. The intersection of the data types must be a numeric data type, as specified in the rules about the implicit numeric conversions that the expression evaluator performs. The intersection of the two numeric data types cannot be null. For more information, see [Integration Services Data Types in Expressions](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types-in-Expressions.md).  
  
-   **Character** Both *expression1* and *expression2* must evaluate to either a DT\_STR or a DT\_WSTR data type. The two expressions can evaluate to different string data types.  
  
    > [!NOTE]  
    >  String comparisons are case, accent, kana, and width\-sensitive.  
  
-   **Date, Time, or Date\/Time** Both *expression1* and *expression2* must evaluate to one of the following data types: DT\_DBDATE, DT\_DATE, DT\_DBTIME, DT\_DBTIME2, DT\_DBTIMESTAMP, DT\_DBTIMESTAMP2, DT\_DBTIMESTAPMOFFSET, or DT\_FILETIME.  
  
    > [!NOTE]  
    >  The system does not support comparisons between an expression that evaluates to a time data type and an expression that evaluates to either a date or a date\/time data type. The system generates an error.  
  
     When comparing the expressions, the system applies the following conversion rules in the order listed:  
  
    -   When the two expressions evaluate to the same data type, a comparison of that data type is performed.  
  
    -   If one expression is a DT\_DBTIMESTAMPOFFSET data type, the other expression is implicitly converted to DT\_DBTIMESTAMPOFFSET and a DT\_DBTIMESTAMPOFFSET comparison is performed. For more information, see [Integration Services Data Types in Expressions](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types-in-Expressions.md).  
  
    -   If one expression is a DT\_DBTIMESTAMP2 data type, the other expression is implicitly converted to DT\_DBTIMESTAMP2 and a DT\_DBTIMESTAMP2 comparison is performed.  
  
    -   If one expression is a DT\_DBTIME2 data type, the other expression is implicitly converted to DT\_DBTIME2, and a DT\_DBTIME2 comparison is performed.  
  
    -   If one expression is of a type other than DT\_DBTIMESTAMPOFFSET, DT\_DBTIMESTAMP2, or DT\_DBTIME2, the expressions are converted to the DT\_DBTIMESTAMP data type before they are compared.  
  
     When comparing the expressions, the system makes the following assumptions:  
  
    -   If each expression is a data type that includes fractional seconds, the system assumes that the data type with the least number of digits for fractional seconds has zeros for the remaining digits.  
  
    -   If each expression is a date data type, but only one has a time zone offset, the system assumes that the date data type without the time zone offset is in Coordinated Universal Time \(UTC\).  
  
-   **Logical** Both *expression1* and *expression2* must evaluate to a Boolean.  
  
-   **GUID** Both *expression1* and *expression2* must evaluate to the DT\_GUID data type.  
  
-   **Binary** Both *expression1* and *expression2* must evaluate to the DT\_BYTES data type.  
  
-   **BLOB** Both *expression1* and *expression2* must evaluate to the same Binary Large Object Block \(BLOB\) data type: DT\_TEXT, DT\_NTEXT, or DT\_IMAGE.  
  
 For more information about data types, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Expression Examples  
 This example evaluates to TRUE only if the current date is not July 4, 2003. For more information, see [GETDATE &#40;SSIS Expression&#41;](../Topic/GETDATE%20\(SSIS%20Expression\).md).  
  
```  
"7/4/2003" != GETDATE()  
```  
  
 This example evaluates to TRUE if the value in the **ListPrice** column is not 500.  
  
```  
ListPrice != 500  
```  
  
 This example uses the variable **LPrice**. It evaluates to TRUE if the value of **LPrice** is not 500. The data type on the variable must be numeric in order for the expression to parse.  
  
```  
@LPrice != 500  
```  
  
## See Also  
 [== &#40;Equal&#41; &#40;SSIS Expression&#41;](../Topic/==%20\(Equal\)%20\(SSIS%20Expression\).md)   
 [Operator Precedence and Associativity](../../Topics\TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators &#40;SSIS Expression&#41;](../Topic/Operators%20\(SSIS%20Expression\).md)  
  
  