---
title: setObject Method (SQLServerPreparedStatement)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerPreparedStatement.setObject
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 93a2b22c-82b4-48c7-a428-369ebe98a372
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
# setObject Method (SQLServerPreparedStatement)
  Sets the value of the designated parameter by using the given object.  
  
 Beginning with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0, the behavior of this method is modified by the **sendTimeAsDatetime** connection property \([Setting the Connection Properties](../content/Setting-the-Connection-Properties.md)\) and [SQLServerDataSource.setSendTimeAsDatetime](../content/setSendTimeAsDatetime-Method--SQLServerDataSource-.md).  
  
 For more information, see [Configuring How java.sql.Time Values are Sent to the Server](../content/Configuring-How-java.sql.Time-Values-are-Sent-to-the-Server.md).  
  
## Overload List  
  
|Name|Description|  
|----------|-----------------|  
|[setObject \(int, java.lang.Object\)](../content/setObject-Method--int--java.lang.Object-.md)|Sets the value of the designated parameter by using the given object.|  
|[setObject \(int, java.lang.Object, int\)](../content/setObject-Method--int--java.lang.Object--int-.md)|Sets the value of the designated parameter by using the given object and target type.|  
|[setObject \(int, java.lang.Object, int, int\)](../content/setObject-Method--int--java.lang.Object--int--int-.md)|Sets the value of the designated parameter by using the given object, target type, and scale.|  
  
## See Also  
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)   
 [SQLServerPreparedStatement Class](../content/SQLServerPreparedStatement-Class.md)  
  
  