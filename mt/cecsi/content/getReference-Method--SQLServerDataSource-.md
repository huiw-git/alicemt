---
title: getReference Method (SQLServerDataSource)
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
  - SQLServerDataSource.getReference
apilocation: 
  - sqljdbc.jar
apitype: Assembly
ms.assetid: b3fb1a97-86ee-4977-adca-c35ae199dbb3
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
# getReference Method (SQLServerDataSource)
  Returns a reference to this [SQLServerDataSource](../content/SQLServerDataSource-Class.md) object.  
  
## Syntax  
  
```  
  
public javax.naming.Reference getReference()  
```  
  
## Return Value  
 A Reference object.  
  
## Remarks  
 This getReference method is specified by the getReference method in the javax.naming.Referenceable interface.  
  
 Prior to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] JDBC Driver 3.0, if SQLServerDataSource.setTrustStorePassword was called on a SQLServerDataSource object, the password would be present in the object returned by SQLServerDataSource.getReference, allowing the object to be used to make additional connections. In JDBC Driver 3.0, you will need to set the password on the object returned by SQLServerDataSource.getReference before you make connections with the object.  
  
 Also, if you set SQLServerDataSource.setTrustStorePassword before binding the data source properties, you must call SQLServerDataSource.setTrustStorePassword before getting the connection. For example,  
  
```  
ctx = new InitialContext(System.getProperties());  
  
SQLServerDataSource ds1 = (SQLServerDataSource) ctx.lookup(jndiName);  
  
ds1.setTrustStorePassword("XXXXX");  
Connection con = ds1.getConnection("user", "XXXXXX");  
  
ctx.rebind(jndiName, ds1);  
SQLServerDataSource ds2 = (SQLServerDataSource) ctx.lookup(jndiName);  
ds2.setTrustStorePassword("XXXXX");   // reset the truststore password  
con = ds2.getConnection("user", "XXXXXX");   // provide userid and password again  
```  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  