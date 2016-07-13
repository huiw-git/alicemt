---
title: setTime Method (SQLServerPreparedStatement)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerPreparedStatement.setTime
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: b3a83ea3-6636-4096-842b-71b37340fa07
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
# setTime Method (SQLServerPreparedStatement)
  Sets the designated parameter to the given time value.  
  
 Beginning with [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0, the behavior of this method is modified by the **sendTimeAsDatetime** connection property \([Setting the Connection Properties](../content/Setting-the-Connection-Properties.md)\) and [SQLServerDataSource.setSendTimeAsDatetime](../content/setSendTimeAsDatetime-Method--SQLServerDataSource-.md).  
  
 For more information, see [Configuring How java.sql.Time Values are Sent to the Server](../content/Configuring-How-java.sql.Time-Values-are-Sent-to-the-Server.md).  
  
## Overload List  
  
|Name|Description|  
|----------|-----------------|  
|[setTime \(int, java.sql.Time\)](../content/setTime-Method--int--java.sql.Time-.md)|Sets the designated parameter to the given time value.|  
|[setTime \(int, java.sql.Time, java.util.Calendar\)](../content/setTime-Method--int--java.sql.Time--java.util.Calendar-.md)|Sets the designated parameter to the given time and calendar values.|  
  
## See Also  
 [SQLServerPreparedStatement Members](../content/SQLServerPreparedStatement-Members.md)   
 [SQLServerPreparedStatement Class](../content/SQLServerPreparedStatement-Class.md)  
  
  