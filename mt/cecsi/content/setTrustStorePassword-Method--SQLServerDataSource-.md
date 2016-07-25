---
title: "setTrustStorePassword Method (SQLServerDataSource)"
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
  - setTrustStorePassword Method (SQLServerDataSource)
apilocation: 
  - setTrustStorePassword Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: fa87cbde-71cc-4f21-bc07-f8ba2b6a0a3f
caps.latest.revision: 16
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
# setTrustStorePassword Method (SQLServerDataSource)
  Sets the password that is used to check the integrity of the trustStore data.  
  
## Syntax  
  
```  
  
public void setTrustStorePassword(java.lang.String trustStorePassword)  
```  
  
#### Parameters  
 *trustStorePassword*  
  
 A **String** that contains the password that is used to check the integrity of the trustStore data.  
  
## Remarks  
 The trustStorePassword property can be specified along with the trustStore property and its value is used to check the integrity of the trustStore file.  
  
 If the trustStore property is set but the trustStorePassword property is not set, the integrity of the trustStore is not checked.  
  
 When both trustStore and trustStorePassword properties are unspecified, the driver will use the Java Virtual Machine (JVM) system properties, "javax.net.ssl.trustStore" and "javax.net.ssl.trustStorePassword". If the "javax.net.ssl.trustStorePassword" system property is not specified, the integrity of the trustStore is not checked.  
  
 If the trustStore property is not set but the trustStorePassword property is set, the JDBC driver will use the file specified by the "javax.net.ssl.trustStore" as a trust store and the integrity of the trust store is checked by using the specified trustStorePassword. This might be needed when the client application does not want to store the password in the JVM system property.  
  
 For more information, see [Setting the Connection Properties](../content/Setting-the-Connection-Properties.md).  
  
 Beginning in JDBC Driver 3.0, if you set SQLServerDataSource.setTrustStorePassword before binding the data source properties, you must call SQLServerDataSource.setTrustStorePassword before getting the connection. For more information, see [SQLServerDataSource.getReference](../content/getReference-Method--SQLServerDataSource-.md).  
  
## See Also  
 [SQLServerDataSource Members](../content/SQLServerDataSource-Members.md)   
 [SQLServerDataSource Class](../content/SQLServerDataSource-Class.md)  
  
  