---
title: Cast (SSIS Expression)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d4e915cc-1c7b-4b2e-93b0-13a8b0cb9242
---
# Cast (SSIS Expression)
  Explicitly converts an expression from one data type to a different data type. The cast operator can also function as a truncation operator.  
  
## Syntax  
  
```  
  
(type_spec) expression  
  
```  
  
## Arguments  
 *type\_spec*  
 Is a valid [!INCLUDE[ssIS](../../Token\Other/ssIS_md.md)] data type.  
  
 *expression*  
 Is a valid expression.  
  
## Result Types  
 The data type of *type\_spec*. For more information, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## Remarks  
 The following diagram shows legal cast operations.  
  
 ![Legal and not legal casts between data types](../../Images\Image\ImageNotContaina/data_conversion.gif "data_conversion")  
  
 Casting to some data types requires parameters. The following table lists these data types and their parameters.  
  
|Data type|Parameter|Example|  
|---------------|---------------|-------------|  
|DT\_STR|*charcount*<br /><br /> *codepage*|\(DT\_STR,30,1252\) casts 30 bytes, or 30 single characters, to the DT\_STR data type using the 1252 code page.|  
|DT\_WSTR|*Charcount*|\(DT\_WSTR,20\) casts 20 byte pairs, or 20 Unicode characters, to the DT\_WSTR data type.|  
|DT\_BYTES|*Bytecount*|\(DT\_BYTES,50\) casts 50 bytes to the DT\_BYTES data type.|  
|DT\_DECIMAL|*Scale*|\(DT\_DECIMAL,2\) casts a numeric value to the DT\_DECIMAL data type using a scale of 2.|  
|DT\_NUMERIC|*Precision*<br /><br /> *Scale*|\(DT\_NUMERIC,10,3\) casts a numeric value to the DT\_NUMERIC data type using a precision of 10 and a scale of 3.|  
|DT\_TEXT|*Codepage*|\(DT\_TEXT,1252\) casts a value to the DT\_TEXT data type using the 1252 code page.|  
  
 When a string is cast to a DT\_DATE, or vice versa, the locale of the transformation is used. However, the date is in the ISO format of YYYY\-MM\-DD, regardless of whether the locale preference uses the ISO format.  
  
> [!NOTE]  
>  To convert a string to a date data type other than DT\_DATE, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
 If the code page is a multibyte character code page, the number of bytes and characters may differ. Casting from a DT\_WSTR to a DT\_STR with the same *charcount* value may cause truncation of the final characters in the converted string. If sufficient storage is available in the column of the destination table, set the value of the *charcount* parameter to reflect the number of bytes that the multibyte code page requires. For example, if you cast character data to a DT\_STR data type using the 936 code page, you should set *charcount* to a value up to two times greater than the number of characters that you expect the data to contain; if you cast character data using the UTF\-8 code page, you should set *charcount* to a value up to four times greater.  
  
 For more information about the structure of date data types, see [Integration Services Data Types](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types.md).  
  
## SSIS Expression Examples  
 This example casts a numeric value to an integer.  
  
```  
(DT_I4) 3.57  
```  
  
 This example casts an integer to a character string using the 1252 code page.  
  
```  
(DT_STR,1,1252)5  
```  
  
 This example casts a three\-character string to double\-byte characters.  
  
```  
(DT_WSTR,3)"Cat"  
```  
  
 This example casts an integer to a decimal with a scale of two.  
  
```  
(DT_DECIMAl,2)500  
```  
  
 This example casts an integer to a numeric with a precision of seven and scale of three.  
  
```  
(DT_NUMERIC,7,3)4000  
```  
  
 This example casts values in the **FirstName** column, defined with an **nvarchar** data type and a length of 50, to a character string using the 1252 code page.  
  
```  
(DT_STR,50,1252)FirstName  
```  
  
 This example casts values in the **DateFirstPurchase** column of type DT\_DBDATE, to a Unicode character string with a length of 20.  
  
```  
(DT_WSTR,20)DateFirstPurchase  
```  
  
 This example casts the string literal "True" to a Boolean.  
  
```  
(DT_BOOL)"True"  
```  
  
 This example casts a string literal to DT\_DBDATE.  
  
```  
(DT_DBDATE) "1999-10-11"  
```  
  
 This example casts a string literal to the DT\_DBTIME2 data type that uses 5 digits for fractional seconds. \(The DT\_DBTIME2 data type can have between 0 and 7 digits specified for fractional seconds.\)  
  
```  
(DT_DBTIME2, 5) "16:34:52.12345"  
```  
  
 This example casts a string literal to the DT\_DBTIMESTAMP2 data type that uses 4 digits for fractional seconds. \(The DT\_DBTIMESTAMP2 data type can have between 0 and 7 digits specified for fractional seconds.\)  
  
```  
(DT_DBTIMESTAMP2, 4) "1999-10-11 16:34:52.1234"  
```  
  
 This example casts a string literal to the DT\_DBTIMESTAMPOFFSET data type that uses 7 digits for fractional seconds. \(The DT\_DBTIMESTAMPOFFSET data typecan have between 0 and 7 digits specified for fractional seconds.\)  
  
```  
(DT_DBTIMESTAMPOFFSET, 7) "1999-10-11 16:34:52.1234567 + 5:35"  
```  
  
## See Also  
 [Operator Precedence and Associativity](../../Topics\TopicNameNotContainA/Operator-Precedence-and-Associativity.md)   
 [Operators &#40;SSIS Expression&#41;](../Topic/Operators%20\(SSIS%20Expression\).md)   
 [Integration Services &#40;SSIS&#41; Expressions](../Topic/Integration%20Services%20\(SSIS\)%20Expressions.md)   
 [Integration Services Data Types in Expressions](../../Topics\TopicNameNotContainA/Integration-Services-Data-Types-in-Expressions.md)  
  
  