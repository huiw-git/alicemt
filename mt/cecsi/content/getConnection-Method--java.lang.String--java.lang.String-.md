---
title: getConnection Method (java.lang.String, java.lang.String)
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - SQLServerDataSource.getConnection (java.lang.String, java.lang.String)
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: 78db89d6-a8a0-4116-8885-548e627220ed
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
# getConnection Method (java.lang.String, java.lang.String)
  Tries to establish a connection with the data source that this [SQLServerDataSource](../content/SQLServerDataSource-Class.md) object represents by using the given user name and password.  
  
## Syntax  
  
```  
  
public java.sql.Connection getConnection(java.lang.String username,  
                                         java.lang.String password)  
```  
  
#### Parameters  
 *username*  
  
 A **String** that contains the user name.  
  
 *password*  
  
 A **String** that contains the password.  
  
## Return Value  
 A [SQLServerConnection](../content/SQLServerConnection-Class.md) object.  
  
## Exceptions  
 java.sql.SQLException  
  
## Remarks  
 This getConnection method is specified by the getConnection method in the javax.sql.DataSource interface.  
  
 Calling the getConnection method with a non\-null user name or password will replace the user name and password properties that are set on the SQLServerDataSource class when initializing the SQLServerConnection object. For example, if the caller has called [setUser](../content/setUser-Method--SQLServerDataSource-.md) and [setPassword](../content/setPassword-Method--SQLServerDataSource-.md) on the data source, and then calls getConnection and supplies a non\-null user name or a non\-null password, the user name and password set by setUser and setPassword will be replaced by the user name and password passed into getConnection.  
  
> [!NOTE]  
>  The user name and password that are set inside the URL by using a call to the [setURL](../content/setURL-Method--SQLServerDataSource-.md) method will not be changed in this case.  
  
## See Also  
 [getConnection Method &#40;SQLServerDataSource&#41;](../content/getConnection-Method--SQLServerDataSource-.md)   
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  