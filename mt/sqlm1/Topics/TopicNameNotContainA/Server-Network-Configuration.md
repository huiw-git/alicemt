---
title: Server Network Configuration
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 890c09a1-6dad-4931-aceb-901c02ae34c5
---
# Server Network Configuration
  Server network configuration tasks include enabling protocols, modifying the port or pipe used by a protocol, configuring encryption, configuring the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser service, exposing or hiding the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] on the network, and registering the Server Principal Name. Most of the time, you do not have to change the server network configuration. Only reconfigure the server network protocols if special network requirements.  
  
 Network configuration for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is done using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager. For earlier versions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], use the Server Network Utility that ships with those products.  
  
## Protocols  
 Use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager to enable or disable the protocols used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], and to configure the options available for the protocols. More than one protocol can be enabled. You must enable all protocols that you want clients to use. All protocols have equal access to the server. For information about which protocols you should use, see [Enable or Disable a Server Network Protocol](../../Topics\TopicNameContainA/Enable-or-Disable-a-Server-Network-Protocol.md).  
  
### Changing a Port  
 You can configure the TCP\/IP protocol to listen on a designated port. By default, the default instance of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] listens on TCP port 1433. Named instances of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and [!INCLUDE[ssEW](../../Token\Other/ssEW_md.md)] are configured for dynamic ports. This means they select an available port when the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] service is started. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser service helps clients identify the port when they connect.  
  
 When configured for dynamic ports, the port used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] may change each time it is started. When connecting to [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] through a firewall, you must open the port used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Configure [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to use a specific port, so you can configure the firewall to allow communication to the server. For more information, see [Configure a Server to Listen on a Specific TCP Port &#40;SQL Server Configuration Manager&#41;](../Topic/Configure%20a%20Server%20to%20Listen%20on%20a%20Specific%20TCP%20Port%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
### Changing a Named Pipe  
 You can configure the named pipe protocol to listen on a designated named pipe. By default, the default instance of [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] listens on pipe \\\\.\\pipe\\sql\\query for the default instance and \\\\.\\pipe\\MSSQL$*\<instancename\>*\\sql\\query for a named instance. The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] can only listen on one named pipe, but you can change the pipe to another name if you wish. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser service helps clients identify the pipe when they connect. For more information, see [Configure a Server to Listen on an Alternate Pipe &#40;SQL Server Configuration Manager&#41;](../Topic/Configure%20a%20Server%20to%20Listen%20on%20an%20Alternate%20Pipe%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
## Force Encryption  
 The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] can be configured to require encryption when communicating with client applications. For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md).  
  
## Extended Protection for Authentication  
 Support for Extended Protection for Authentication by using channel binding and service binding is available for operating systems that support Extended Protection. For more information, see [Connect to the Database Engine Using Extended Protection](../../Topics\TopicNameNotContainA/Connect-to-the-Database-Engine-Using-Extended-Protection.md).  
  
## Authenticating by Using Kerberos  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supports Kerberos authentication. For more information, see [Register a Service Principal Name for Kerberos Connections](../../Topics\TopicNameContainA/Register-a-Service-Principal-Name-for-Kerberos-Connections.md) and [Microsoft Kerberos Configuration Manager for SQL Server](http://www.microsoft.com/download/details.aspx?id=39046).  
  
### Registering a Server Principal Name \(SPN\)  
 The Kerberos authentication service uses an SPN to authenticate a service. For more information, see [Register a Service Principal Name for Kerberos Connections](../../Topics\TopicNameContainA/Register-a-Service-Principal-Name-for-Kerberos-Connections.md).  
  
 SPNs may also be used to make client authentication more secure when connecting with NTLM. For more information, see [Connect to the Database Engine Using Extended Protection](../../Topics\TopicNameNotContainA/Connect-to-the-Database-Engine-Using-Extended-Protection.md).  
  
## SQL Server Browser Service  
 The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser service runs on the server, and helps client computers to find instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser service does not need to be configured, but must be running under some connection scenarios. For more information about [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser, see [SQL Server Browser Service &#40;Database Engine and SSAS&#41;](../Topic/SQL%20Server%20Browser%20Service%20\(Database%20Engine%20and%20SSAS\).md)  
  
## Hiding SQL Server  
 When running, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser responds to queries, with the name, version, and connection information for each installed instance. For [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], the **HideInstance** flag, indicates that [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser should not respond with information about this server instance. Client applications can still connect, but they must know the required connection information. For more information, see [Hide an Instance of SQL Server Database Engine](../../Topics\TopicNameNotContainA/Hide-an-Instance-of-SQL-Server-Database-Engine.md).  
  
## Related Content  
 [Client Network Configuration](../../Topics\TopicNameNotContainA/Client-Network-Configuration.md)  
  
 [Manage the Database Engine Services](../../Topics\TopicNameNotContainA/Manage-the-Database-Engine-Services.md)  
  
  