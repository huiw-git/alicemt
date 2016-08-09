---
title: "== (Equal) (SSIS Expression)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 36fd2354-7b93-4c95-9cf3-51ee24568950
caps.latest.revision: 54
caps.handback.revision: 0
manager: jhubbard
---
# == (Equal) (SSIS Expression)
Performs a comparison to determine if two expressions are equal. The expression evaluator automatically converts many data types before it performs the comparison. For more information, see [Integration Services Data Types in Expressions](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types-in-Expressions.md).  
  
 However, some data types require that the expression include an explicit cast before the expression can be evaluated successfully. For more information about legal casts between data types, see [Cast (SSIS Expression)](../../Topics/TopicNameNotContainA/Cast--SSIS-Expression-.md).  
  
## Syntax  
  
```  
  
expression1 == expression2  
  
```  
  
## Arguments  
 *expression1, expression2*  
 Is any valid expression.  
  
## Result Types  
 DT_BOOL  
  
## Remarks  
 If either expression in the comparison is null, the comparison result is null. If both expressions are null, the result is null.  
  
 The expression set, *expression1* and *expression2*, must follow one of these rules:  
  
-   **Numeric** Both *expression1* and *expression2* must be a numeric data type. The intersection of the data types must be a numeric data type, as specified in the rules about the implicit numeric conversions that the expression evaluator performs. The intersection of the two numeric data types cannot be null. For more information, see [Integration Services Data Types in Expressions](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types-in-Expressions.md).  
  
-   **Character** Both *expression1* and *expression2* must evaluate to either a DT_STR or a DT_WSTR data type. The two expressions can evaluate to different string data types.  
  
    > [!NOTE]  
    >  String comparisons are case, accent, kana, and width-sensitive.  
  
-   **Date, Time, or Date/Time** Both *expression1* and *expression2* must evaluate to one of the following data types: DT_DBDATE, DT_DATE, DT_DBTIME, DT_DBTIME2, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, DT_DBTIMESTAPMOFFSET, or DT_FILETIME.  
  
    > [!NOTE]  
    >  The system does not support comparisons between an expression that evaluates to a time data type and an expression that evaluates to either a date or a date/time data type. The system generates an error.  
  
     When comparing the expressions, the system applies the following conversion rules in the order listed:  
  
    -   When the two expressions evaluate to the same data type, a comparison of that data type is performed.  
  
    -   If one expression is a DT_DBTIMESTAMPOFFSET data type, the other expression is implicitly converted to DT_DBTIMESTAMPOFFSET and a DT_DBTIMESTAMPOFFSET comparison is performed. For more information, see [Integration Services Data Types in Expressions](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types-in-Expressions.md).  
  
    -   If one expression is a DT_DBTIMESTAMP2 data type, the other expression is implicitly converted to DT_DBTIMESTAMP2 and a DT_DBTIMESTAMP2 comparison is performed.  
  
    -   If one expression is a DT_DBTIME2 data type, the other expression is implicitly converted to DT_DBTIME2, and a DT_DBTIME2 comparison is performed.  
  
    -   If one expression is of a type other than DT_DBTIMESTAMPOFFSET, DT_DBTIMESTAMP2, or DT_DBTIME2, the expressions are converted to the DT_DBTIMESTAMP data type before they are compared.  
  
     When comparing the expressions, the system makes the following assumptions:  
  
    -   If each expression is a data type that includes fractional seconds, the system assumes that the data type with the least number of digits for fractional seconds has zeros for the remaining digits.  
  
    -   If each expression is a date data type, but only one has a time zone offset, the system assumes that the date data type without the time zone offset is in Coordinated Universal Time (UTC).  
  
-   **Logical** Both *expression1* and *expression2* must evaluate to a Boolean.  
  
-   **GUID** Both *expression1* and *expression2* must evaluate to the DT_GUID data type.  
  
-   **Binary** Both *expression1* and *expression2* must evaluate to the DT_BYTES data type.  
  
-   **BLOB** Both *expression1* and *expression2* must evaluate to the same Binary Large Object Block (BLOB) data type: DT_TEXT, DT_NTEXT, or DT_IMAGE.  
  
 For more information about data types, see [Integration Services Data Types](../../Topics/TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Expression Examples  
 This example evaluates to TRUE if the current date is July 4, 2003. For more information, see [GETDATE (SSIS Expression)](../../Topics/TopicNameNotContainA/GETDATE--SSIS-Expression-.md).  
  
 "7/4/2003" == GETDATE()  
  
 This example evaluates to TRUE if the value in the **ListPrice** column is 500.  
  
```  
ListPrice == 500  
```  
  
 This example uses the variable **LPrice**. It evaluates to TRUE if the value of **LPrice** is 500. The data type of the variable must be numeric for the expression to parse successfully.  
  
```  
@LPrice == 500  
```  
  
## See Also  
 [!= (Unequal) (SSIS Expression)](../../Topics/TopicNameNotContainA/!=--Unequal---SSIS-Expression-.md)   
 [Operator Precedence and Associativity](../../Topics/TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators (SSIS Expression)](../../Topics/TopicNameNotContainA/Operators--SSIS-Expression-.md)