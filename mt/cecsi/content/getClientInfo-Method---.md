---
title: getClientInfo Method ()
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b06a5ced-b760-4c78-b17e-854ce95a1a5c
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
# getClientInfo Method ()
  Retrieves a list that contains the name and current value of each client information property supported by the JDBC driver.  
  
## Syntax  
  
```  
  
public java.util.Properties getClientInfo()  
```  
  
## Return Value  
 A Properties object that contains the name and current value of each of the client information properties supported by the driver.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getClientInfo method is specified by the getClientInfo method in the java.sql.Connection interface.  
  
 The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] does not support any client information properties. As a result, this method returns an empty Properties object.  
  
 Similarly, applications can use the [getClientInfoProperties](../content/getClientInfoProperties-Method--SQLServerDatabaseMetaData-.md) method of the [SQLServerDatabaseMetaData](../content/SQLServerDatabaseMetaData-Class.md) class to retrieve a list of the client information properties that the driver supports. The [getClientInfoProperties](../content/getClientInfoProperties-Method--SQLServerDatabaseMetaData-.md) method returns an empty result set.  
  
## See Also  
 [getClientInfo Method &#40;SQLServerConnection&#41;](../content/getClientInfo-Method--SQLServerConnection-.md)   
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  