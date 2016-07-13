---
title: getClientInfo Method (java.lang.String)
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8e632c4-d6cc-4c5e-b6ad-873579343b19
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
# getClientInfo Method (java.lang.String)
  Retrieves the value of a specified client information property.  
  
## Syntax  
  
```  
  
public java.lang.String getClientInfo (java.lang.String name)  
```  
  
#### Parameters  
 *name*  
  
 A String that contains the name of the client information property to retrieve.  
  
## Return Value  
 A String that contains the value of the client information property.  
  
## Exceptions  
 [SQLServerException](../content/SQLServerException-Class.md)  
  
## Remarks  
 This getClientInfo method is specified by the getClientInfo method in the java.sql.Connection interface.  
  
 The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] does not support any client info properties. As a result, this method returns **null**.  
  
 Similarly, applications can use the [getClientInfoProperties](../content/getClientInfoProperties-Method--SQLServerDatabaseMetaData-.md) method of the [SQLServerDatabaseMetaData](../content/SQLServerDatabaseMetaData-Class.md) class to retrieve a list of the client information properties that the driver supports. The [getClientInfoProperties](../content/getClientInfoProperties-Method--SQLServerDatabaseMetaData-.md) method returns an empty result set.  
  
## See Also  
 [getClientInfo Method &#40;SQLServerConnection&#41;](../content/getClientInfo-Method--SQLServerConnection-.md)   
 [SQLServerConnection Members](../content/SQLServerConnection-Members.md)   
 [SQLServerConnection Class](../content/SQLServerConnection-Class.md)  
  
  