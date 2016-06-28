---
title: setFailoverPartner Method (SQLServerDataSource)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDataSource.setFailoverPartner
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 5310b7c2-9d10-474f-ad3a-218fe5da694b
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
# setFailoverPartner Method (SQLServerDataSource)
  Sets the name of the failover server that is used in a database mirroring configuration.  
  
## Syntax  
  
```  
  
public void setFailoverPartner(java.lang.String serverName)  
```  
  
#### Parameters  
 *serverName*  
  
 A **String** that contains the failover server name.  
  
## Remarks  
 The value set by this method is used in the case of an initial connection failure to the principal server; after the initial connection is made, this value is ignored. The [setDatabaseName](../content/setDatabaseName-Method--SQLServerDataSource-.md) method should also be used in conjunction with this method or an exception will be thrown.  
  
 The driver does not support specifying the port number of the failover server when the failover server name is set. However, calling the [setServerName](../content/setServerName-Method--SQLServerDataSource-.md) method and the [setInstanceName](../content/setInstanceName-Method--SQLServerDataSource-.md) method with the [setFailoverPartner](../content/setFailoverPartner-Method--SQLServerDataSource-.md) method is supported.  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  