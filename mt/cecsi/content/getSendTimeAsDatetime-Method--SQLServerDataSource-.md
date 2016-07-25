---
title: "getSendTimeAsDatetime Method (SQLServerDataSource)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 02287122-5dc1-455d-987f-95fd9a69d503
caps.latest.revision: 15
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
# getSendTimeAsDatetime Method (SQLServerDataSource)
  This method was added in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0.  
  
 Returns the setting of the **sendTimeAsDatetime** connection property.  
  
## Syntax  
  
```  
  
public boolean getSendTimeAsDatetime();  
```  
  
## Return Value  
 **true** if java.sql.Time values will be sent to the server as a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] **datetime** type. **false** if java.sql.Time values will be sent to the server as a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] **time** type.  
  
## Remarks  
 See [Setting the Connection Properties](../content/Setting-the-Connection-Properties.md) for more information about the **sendTimeAsDatetime** connection property.  
  
 [SQLServerDataSource.setSendTimeAsDatetime](../content/setSendTimeAsDatetime-Method--SQLServerDataSource-.md) lets you programmatically set the **sendTimeAsDatetime** connection property.  
  
 For more information, see [Configuring How java.sql.Time Values are Sent to the Server](../content/Configuring-How-java.sql.Time-Values-are-Sent-to-the-Server.md).  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  