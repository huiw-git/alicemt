---
title: setObject Method (SQLServerCallableStatement)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerCallableStatement.setObject
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 7110f6c5-4af3-4b50-a4d4-1bae1876c70d
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
# setObject Method (SQLServerCallableStatement)
  Sets the value of the designated parameter using the given object.  
  
 Beginning with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0, the behavior of this method is modified by the **sendTimeAsDatetime** connection property \([Setting the Connection Properties](../content/Setting-the-Connection-Properties.md)\) and [SQLServerDataSource.setSendTimeAsDatetime](../content/setSendTimeAsDatetime-Method--SQLServerDataSource-.md).  
  
 For more information, see [Configuring How java.sql.Time Values are Sent to the Server](../content/Configuring-How-java.sql.Time-Values-are-Sent-to-the-Server.md).  
  
## Overload List  
  
|Name|Description|  
|----------|-----------------|  
|[setObject \(java.lang.String, java.lang.Object\)](../content/setObject-Method--java.lang.String--java.lang.Object-.md)|Sets the value of the designated parameter using the given object.|  
|[setObject \(java.lang.String, java.lang.Object, int\)](../content/setObject-Method--java.lang.String--java.lang.Object--int-.md)|Sets the value of the designated parameter using the given object and target type.|  
|[setObject \(java.lang.String, java.lang.Object, int, int\)](../content/setObject-Method--java.lang.String--java.lang.Object--int--int-.md)|Sets the value of the designated parameter using the given object, target type, and scale.|  
  
## See Also  
 [SQLServerCallableStatement Members](../content/SQLServerCallableStatement-Members.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  