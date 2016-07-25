---
title: "setTime Method (SQLServerCallableStatement)"
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
  - SQLServerCallableStatement.setTime
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 04ea83b2-db5e-4b46-b016-9e496363827e
caps.latest.revision: 18
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
# setTime Method (SQLServerCallableStatement)
  Sets the designated parameter to the given time value.  
  
 Beginning with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0, the behavior of this method is modified by the **sendTimeAsDatetime** connection property ([Setting the Connection Properties](../content/Setting-the-Connection-Properties.md)) and [SQLServerDataSource.setSendTimeAsDatetime](../content/setSendTimeAsDatetime-Method--SQLServerDataSource-.md).  
  
 For more information, see [Configuring How java.sql.Time Values are Sent to the Server](../content/Configuring-How-java.sql.Time-Values-are-Sent-to-the-Server.md).  
  
## Overload List  
  
|Name|Description|  
|----------|-----------------|  
|[setTime (java.lang.String, java.sql.Time)](../content/setTime-Method--java.lang.String--java.sql.Time-.md)|Sets the designated parameter to the given time value.|  
|[setTime (java.lang.String, java.sql.Time, java.util.Calendar)](../content/setTime-Method--java.lang.String--java.sql.Time--java.util.Calendar-.md)|Sets the designated parameter to the given time and calendar values.|  
  
## See Also  
 [SQLServerCallableStatement Methods](../content/SQLServerCallableStatement-Methods.md)   
 [SQLServerCallableStatement Class](../content/SQLServerCallableStatement-Class.md)  
  
  