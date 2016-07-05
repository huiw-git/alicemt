---
title: getDateTimeOffset Method (int)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8bb00356-4d6e-4625-b924-67646930fdf2
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
# getDateTimeOffset Method (int)
  This method was added in [!INCLUDE[msCoName](../content/includes/msCoName_md.md)] [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0.  
  
 Retrieves the value of the designated parameter as a [DateTimeOffset Class](../content/DateTimeOffset-Class.md) object in the Java programming language given the parameter index.  
  
## Syntax  
  
```  
  
public microsoft.sql.DateTimeOffset getDateTimeOffset(int index)  
```  
  
#### Parameters  
 *index*  
  
 The one\-based parameter ordinal.  
  
## Return Value  
 A [DateTimeOffset Class](../content/DateTimeOffset-Class.md) object.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 You can set a [DateTimeOffset Class](../content/DateTimeOffset-Class.md) parameter value with [SQLServerCallableStatement.setDateTimeOffset](../content/setDateTimeOffset-Method--SQLServerCallableStatement-.md).  
  
## See Also  
 [getDateTimeOffset Method &#40;SQLServerCallableStatement&#41;](../content/getDateTimeOffset-Method--SQLServerCallableStatement-.md)   
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  