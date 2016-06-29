---
title: Using SSL Encryption
ms.custom: na
ms.prod: sql-non-specified
ms.reviewer: na
ms.suite: na
ms.technology: 
  - drivers
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8e566243-2f93-4b21-8065-3c8336649309
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
# Using SSL Encryption
  Secure Sockets Layer \(SSL\) encryption enables transmitting encrypted data across the network between an instance of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] and a client application.  
  
 Secure Sockets Layer \(SSL\) is a protocol for establishing a secure communication channel to prevent the interception of critical or sensitive information across the network and other Internet communications. SSL allows the client and the server to authenticate the identity of each other. After the participants are authenticated, SSL provides encrypted connections between them for secure message transmission.  
  
 The [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] provides an infrastructure to enable and disable the encryption on a particular connection based on the user specified connection properties and the server and client settings. The user can specify the certificate store location and password, a host name to be used to validate the certificate, and when to encrypt the communication channel.  
  
 Enabling SSL encryption increases the security of data transmitted across networks between instances of [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] and applications. However, enabling encryption does slow performance.  
  
 The topics in this section describe how the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] version supports SSL encryption, including new connection properties, and how you can configure the trust store at the client\-side.  
  
> [!NOTE]  
>  The **hostNameInCertificate** connection property is recommended to validate an SSL certificate.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Understanding SSL Support](../content/Understanding-SSL-Support.md)|Describes how the [!INCLUDE[jdbcNoVersion](../content/includes/jdbcNoVersion_md.md)] supports SSL encryption.|  
|[Connecting with SSL Encryption](../content/Connecting-with-SSL-Encryption.md)|Describes how to connect to a [!INCLUDE[ssNoVersion](../content/includes/ssNoVersion_md.md)] database by using the new SSL specific connection properties.|  
|[Configuring the Client for SSL Encryption](../content/Configuring-the-Client-for-SSL-Encryption.md)|Describes how to configure the default trust store at the client\-side and how to import a private certificate to the client computer's trust store.|  
  
## See Also  
 [Securing JDBC Driver Applications](../content/Securing-JDBC-Driver-Applications.md)  
  
  