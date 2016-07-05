---
title: setDateTimeOffset(int, java.sql.DateTimeOffset) (SQLServerStatement)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8b6e380-6b53-489b-be73-73fcb5258269
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - sv-se
  - zh-cn
  - zh-tw
---
# setDateTimeOffset(int, java.sql.DateTimeOffset) (SQLServerStatement)
  Sets the designated parameter to the given DateTimeOffset value.  
  
## Syntax  
  
```  
  
public void setDateTimeOffset(int parameterIndex, DateTimeOffset dateTime)  
```  
  
#### Parameters  
 *parameterIndex*  
  
 Index of the column to set.  
  
 *dateTimeOffset*  
  
 A DateTimeOffset object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 The DateTimeOffset format is "YYYY\-MM\-DD HH\-MM\-SS\[.nnnnnnn\] \[\+\]\[\-\] HH:MM". Use the following table for reference.  
  
|SQL Type|Insert|  
|--------------|------------|  
|datetime|May only insert: "YYYY\-MM\-DD hh:mm:ss\[.nnn\]"|  
|smalldatetime|May only insert: "YYYY\-MM\-DD hh:mm:ss"|  
|Time|May only insert: "hh:mm:ss\[.nnnnnnn\]"|  
|Date|May only insert: "YYYY\-MM\-DD"|  
|DateTime2|May only insert: "YYYY\-MM\-DD hh:mm:ss\[.nnnnnnn\]"|  
  
## See Also  
 [getDateTimeOffset &#40;SQLServerResultSet&#41;](../content/getDateTimeOffset--SQLServerResultSet-.md)   
 [SQLServerStatement Members](../content/SQLServerStatement-Members.md)   
 [SQLServerStatement Class](../content/SQLServerStatement-Class.md)  
  
  