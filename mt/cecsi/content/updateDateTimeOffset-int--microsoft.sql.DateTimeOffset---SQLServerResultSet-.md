---
title: updateDateTimeOffset(int, microsoft.sql.DateTimeOffset) (SQLServerResultSet)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 21ec0054-c808-4e88-9c8d-c71b696ce658
manager: jhubbard
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
# updateDateTimeOffset(int, microsoft.sql.DateTimeOffset) (SQLServerResultSet)
  This method was added in [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0.  
  
 Updates the value of the column specified to the [DateTimeOffset Class](../content/DateTimeOffset-Class.md) value, given a zero\-based column ordinal.  
  
## Syntax  
  
```  
  
public void updateDateTimeOffset(int index, microsoft.sql.DateTimeOffset x)  
```  
  
#### Parameters  
 *index*  
  
 The zero\-based ordinal of a column.  
  
 *x*  
  
 A [DateTimeOffset Class](../content/DateTimeOffset-Class.md) object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 You can retrieve a [DateTimeOffset Class](../content/DateTimeOffset-Class.md) value with [SQLServerResultSet.getDateTimeOffset](../content/getDateTimeOffset--SQLServerResultSet-.md).  
  
## See Also  
 [updateDateTimeOffset &#40;SQLServerResultSet&#41;](../content/updateDateTimeOffset--SQLServerResultSet-.md)   
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  