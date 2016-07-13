---
title: updateBytes Method (SQLServerResultSet)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.updateBytes
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 3050c836-fbb3-4475-99e5-05637a48a932
manager:jhubbard
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
# updateBytes Method (SQLServerResultSet)
  Updates the designated column with an array of **byte** values.  
  
## Overload List  
  
|Name|Description|  
|----------|-----------------|  
|[updateBytes \(int, byte&#91;&#93;\)](../content/updateBytes-Method--int--byte-.md)|Updates the designated column with an array of **byte** values given the column index.|  
|[updateBytes \(java.lang.String, byte&#91;&#93;\)](../content/updateBytes-Method--java.lang.String--byte-.md)|Updates the designated column with an array of **byte** values given the column name.|  
  
## Remarks  
 In a previous version of [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)], you could use SQLServerResultSet.updateBytes to convert values between byte arrays and [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data type **date**, **time**, **datetime2**, or **datetimeoffset**. Now, using this method with those data types will cause an exception indicating that the conversion is not supported.  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  