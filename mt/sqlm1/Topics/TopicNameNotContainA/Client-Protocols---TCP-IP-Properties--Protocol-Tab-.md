---
title: Client Protocols - TCP IP Properties (Protocol Tab)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d04f1bce-069c-4a02-b561-c87c3282be36
---
# Client Protocols - TCP IP Properties (Protocol Tab)
  In [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager, use the **Protocol** tab on the **TCP\/IP Properties** dialog box to view or specify the following options. To connect to a different port, type the port number in the **Default Port** box. For more information about connection strings, see [Creating a Valid Connection String Using TCP IP](../../Topics\TopicNameContainA/Creating-a-Valid-Connection-String-Using-TCP-IP.md).  
  
## Options  
 **Default Port**  
 Specifies the port that the TCP\/IP Net\-library will use to attempt to connect to the target instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. The default value port is 1433.  
  
 When connecting to a default instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], the client uses this value. If a default instance has been configured to listen on a different port, change this value to that port number.  
  
 When connecting to a named instance of [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], the client will attempt to obtain the port number from the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser Service running on the server computer. If the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Browser Service is not running, the port number must be provided through this setting, or as part of the connection string.  
  
 **Enabled**  
 Possible values are **Yes** and **No**.  
  
 **Keep Alive**  
 This parameter \(in milliseconds\) controls how often TCP attempts to verify that an idle connection is still intact by sending a **KEEPALIVE** packet. The default is 30000 milliseconds.  
  
 **Keep Alive Interval**  
 This parameter \(in milliseconds\) determines the interval separating **KEEPALIVE** retransmissions until a response is received. The default is 1000 milliseconds.  
  
## See Also  
 [Choosing a Network Protocol](../Topic/Choosing%20a%20Network%20Protocol.md)   
 [New Alias &#40;Alias Tab&#41;](../Topic/New%20Alias%20\(Alias%20Tab\).md)   
 [&#60;Alias&#62; Properties &#40;Alias Tab&#41;](../Topic/%3CAlias%3E%20Properties%20\(Alias%20Tab\).md)  
  
  