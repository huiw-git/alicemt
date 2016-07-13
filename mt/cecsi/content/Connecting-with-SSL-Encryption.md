---
title: Connecting with SSL Encryption
ms.custom: na
ms.date: 07/13/2016
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec91fa8a-ab7e-4c1e-a05a-d7951ddf33b1
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
# Connecting with SSL Encryption
  The examples in this topic describe how to use connection string properties that allow applications to use Secure Sockets Layer \(SSL\) encryption in a Java application. For more information about these new connection string properties such as **encrypt**, **trustServerCertificate**, **trustStore**, **trustStorePassword**, and **hostNameInCertificate**, see [Setting the Connection Properties](../content/Setting-the-Connection-Properties.md).  
  
 When the **encrypt** property is set to **true** and the **trustServerCertificate** property is set to **true**, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] will not validate the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] SSL certificate. This is usually required for allowing connections in test environments, such as where the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] instance has only a self signed certificate.  
  
 The following code example demonstrates how to set the **trustServerCertificate** property in a connection string:  
  
```  
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true;trustServerCertificate=true";  
```  
  
 When the **encrypt** property is set to **true** and the **trustServerCertificate** property is set to **false**, the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] will validate the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] SSL certificate. Validating the server certificate is a part of the SSL handshake and ensures that the server is the correct server to connect to. In order to validate the server certificate, the trust material must be supplied at connection time either by using **trustStore** and **trustStorePassword** connection properties explicitly, or by using the underlying Java Virtual Machine \(JVM\)'s default trust store implicitly.  
  
 The **trustStore** property specifies the path \(including filename\) to the certificate trustStore file, which contains the list of certificates that the client trusts. The **trustStorePassword** property specifies the password used to check the integrity of the trustStore data. For more information on using the JVM's default trust store, see the [Configuring the Client for SSL Encryption](../content/Configuring-the-Client-for-SSL-Encryption.md).  
  
 The following code example demonstrates how to set the **trustStore** and **trustStorePassword** properties in a connection string:  
  
```  
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword";  
```  
  
 The JDBC Driver provides an additional property, **hostNameInCertificate**, which specifies the host name of the server. The value of this property must match the subject property of the certificate.  
  
 The following code example demonstrates how to use the **hostNameInCertificate** property in a connection string:  
  
```  
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword" +  
     "hostNameInCertificate=hostName";  
```  
  
> [!NOTE]  
>  Alternatively, you can set the value of connection properties by using the appropriate **setter** methods provided by the [SQLServerDataSource](../content/SQLServerDataSource-Class.md) class.  
  
 If the **encrypt** property is set to **true** and the **trustServerCertificate** property is set to **false** and if the server name in the connection string does not match the server name in the [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] SSL certificate, the following error will be issued: The driver could not establish a secure connection to [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] by using Secure Sockets Layer \(SSL\) encryption. Error: "java.security.cert.CertificateException: Failed to validate the server name in a certificate during Secure Sockets Layer \(SSL\) initialization."  
  
## See Also  
 [Using SSL Encryption](../content/Using-SSL-Encryption.md)   
 [Securing JDBC Driver Applications](../content/Securing-JDBC-Driver-Applications.md)  
  
  