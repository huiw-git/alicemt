---
title: "setDateTimeOffset Method (SQLServerCallableStatement)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9383e14d-c83e-43c5-980c-50a3e0bedc31
caps.latest.revision: 8
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
# setDateTimeOffset Method (SQLServerCallableStatement)
  This method was added in [!INCLUDE[msCoName](../content/includes/msCoName_md.md)][!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0.  
  
 Sets the value of the column specified to the [DateTimeOffset Class](../content/DateTimeOffset-Class.md) value.  
  
## Syntax  
  
```  
  
public void setDateTimeOffset(String sCol, microsoft.sql.DateTimeOffset t)  
```  
  
#### Parameters  
 *sCol*  
  
 The name of a column.  
  
 *t*  
  
 The [DateTimeOffset Class](../content/DateTimeOffset-Class.md) object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 You can retrieve a [DateTimeOffset Class](../content/DateTimeOffset-Class.md) value with [SQLServerCallableStatement.getDateTimeOffset](../content/getDateTimeOffset-Method--SQLServerCallableStatement-.md).  
  
 [setDateTimeOffset](../content/setDateTimeOffset-Method--SQLServerPreparedStatement-.md) takes the ordinal of the column.  
  
## See Also  
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  