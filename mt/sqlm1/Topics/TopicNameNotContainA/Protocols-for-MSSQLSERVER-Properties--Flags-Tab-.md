---
title: Protocols for MSSQLSERVER Properties (Flags Tab)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d38e6e9-f95f-4e79-ae45-89f631037528
---
# Protocols for MSSQLSERVER Properties (Flags Tab)
  When a certificate is installed on the server, use the **Flags** tab on the **Protocols for MSSQLSERVER Properties** dialog box to view or specify the protocol encryption and hide instance options. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] must be restarted to enable or disable the **ForceEncryption** setting.  
  
 To encrypt connections, you should provision the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] with a certificate. If a certificate is not installed, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] will generate a self\-signed certificate when the instance is started. This self\-signed certificate can be used instead of a certificate from a trusted certificate authority, but it does not provide authentication or non\-repudiation.  
  
> [!CAUTION]  
>  Secure Sockets Layer \(SSL\) connections encrypted using a self\-signed certificate do not provide strong security. They are susceptible to man\-in\-the\-middle attacks. You should not rely on SSL using self\-signed certificates in a production environment or on servers that are connected to the Internet.  
  
 For more in formation on encryption, see "Encrypting Connections to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]" in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.  
  
 The login process is always encrypted. When **ForceEncryption** is set to **Yes**, all client\/server communication is encrypted, and clients connecting to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] must be configured to trust the root authority of the server certificate. For more information, see "How to: Enable Encrypted Connections to the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] \([!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager\)" in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.  
  
## Cluster Servers  
 If you want to use encryption with a failover cluster, you must install the server certificate with the fully qualified DNS name of the virtual server on all nodes in the failover cluster. For example, if you have a two\-node cluster, with nodes named "test1.*\<your company\>*.com" and "test2.*\<your company\>*.com" and a virtual server named "virtsql", you need to install a certificate for "virtsql.*\<your company\>*.com" on both nodes. You can then check the **ForceEncryption** check box on the **SQL Server Configuration Manager** to configure your failover cluster for encryption.  
  
## Options  
 **ForceEncryption**  
 Force protocol encryption. Encryption is a method for keeping sensitive information confidential by changing data into an unreadable form. Encryption ensures that data remains secure, even if the transmission packets are viewed during the transmission process. To use channel binding, set **Force Encryption** to **On** and configure **Extended Protection** on the **Advanced** tab.  
  
 **HideInstance**  
 Prevent the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser Service from exposing this instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] to client computers that try to locate the instance by using the **Browse** button. In the case of named instances on the server, to connect, client applications must specify the protocol endpoint information. For example, the port number or the named pipe name, such as **tcp:server,5000**. For more information, see [Logging In to SQL Server](../../Topics\TopicNameNotContainA/Logging-In-to-SQL-Server.md).  
  
 For more information, see "How to: Enable Encryption Connections to the Database Engine \(SQL Server Configuration Manager\)" in Books Online.  
  
  