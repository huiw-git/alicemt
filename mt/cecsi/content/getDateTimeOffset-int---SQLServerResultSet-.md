---
title: getDateTimeOffset(int) (SQLServerResultSet)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 60abf83d-6f97-4e47-b9d3-5072bd09d869
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
# getDateTimeOffset(int) (SQLServerResultSet)
  This method was added in [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0.  
  
 Retrieves the value of the designated column as a [DateTimeOffset Class](../content/DateTimeOffset-Class.md) object in the Java programming language given the parameter index.  
  
## Syntax  
  
```  
  
public microsoft.sql.DateTimeOffset getDateTimeOffset(int columnIndex)  
```  
  
#### Parameters  
 *columnIndex*  
  
 The column ordinal.  
  
## Return Value  
 A [DateTimeOffset Class](../content/DateTimeOffset-Class.md) object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 You can update a [DateTimeOffset Class](../content/DateTimeOffset-Class.md) value with [SQLServerResultSet.updateDateTimeOffset](../content/updateDateTimeOffset--SQLServerResultSet-.md).  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  