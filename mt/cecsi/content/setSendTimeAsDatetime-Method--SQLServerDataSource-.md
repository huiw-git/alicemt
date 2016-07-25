---
title: "setSendTimeAsDatetime Method (SQLServerDataSource)"
ms.custom: na
ms.date: 07/18/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 705a0494-b5e2-43db-940a-1b8cec550cdb
caps.latest.revision: 14
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
# setSendTimeAsDatetime Method (SQLServerDataSource)
  This method was added in [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0.  
  
 Modifies the setting of the **sendTimeAsDatetime** connection property.  
  
## Syntax  
  
```  
  
public void setSendTimeAsDatetime(boolean sendTimeAsDateTime)  
```  
  
#### Parameters  
 *sendTimeAsDateTime*  
  
 A Boolean value. When true, causes java.sql.Time values to be sent to the server as [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] **datetime** types. When false, causes java.sql.Time values to be sent to the server as [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] **time** types.  
  
## Remarks  
 [SQLServerDataSource.getSendTimeAsDatetime](../content/getSendTimeAsDatetime-Method--SQLServerDataSource-.md) returns the setting of the **sendTimeAsDatetime** connection property.  
  
 For more information on the **sendTimeAsDatetime** connection property, see [Setting the Connection Properties](../content/Setting-the-Connection-Properties.md).  
  
 For more information, see [Configuring How java.sql.Time Values are Sent to the Server](../content/Configuring-How-java.sql.Time-Values-are-Sent-to-the-Server.md).  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  