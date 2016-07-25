---
title: "getBytes Method (SQLServerResultSet)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerResultSet.getBytes
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: d16a0aea-6144-4fcb-bcbc-5d7daa36d327
caps.latest.revision: 11
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
# getBytes Method (SQLServerResultSet)
  Retrieves the value of the designated column in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a **byte** array in the Java programming language.  
  
## Overload List  
  
|Name|Description|  
|----------|-----------------|  
|[getBytes (int)](../content/getBytes-Method--int---SQLServerResultSet-.md)|Retrieves the value of the designated column index in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a **byte** array in the Java programming language.|  
|[getBytes (java.lang.String)](../content/getBytes-Method--java.lang.String---SQLServerResultSet-.md)|Retrieves the value of the designated column name in the current row of this [SQLServerResultSet](../content/SQLServerResultSet-Class.md) object as a **byte** array in the Java programming language.|  
  
## Remarks  
 In a previous version of the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)], you could use SQLServerResultSet.getBytes to convert values between byte arrays and [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] data type **date**, **time**, **datetime2**, or **datetimeoffset**. Now, using this method with those data types will cause an exception indicating that the conversion is not supported.  
  
## See Also  
 [SQLServerResultSet Members](../content/SQLServerResultSet-Members.md)   
 [SQLServerResultSet Class](../content/SQLServerResultSet-Class.md)  
  
  