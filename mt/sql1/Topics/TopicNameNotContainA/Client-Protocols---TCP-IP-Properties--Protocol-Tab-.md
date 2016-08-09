---
title: "Client Protocols - TCP IP Properties (Protocol Tab)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d04f1bce-069c-4a02-b561-c87c3282be36
caps.latest.revision: 26
caps.handback.revision: 0
manager: jhubbard
---
# Client Protocols - TCP IP Properties (Protocol Tab)
In [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Configuration Manager, use the **Protocol** tab on the **TCP/IP Properties** dialog box to view or specify the following options. To connect to a different port, type the port number in the **Default Port** box. For more information about connection strings, see [Creating a Valid Connection String Using TCP IP](../../Topics/TopicNameContainA/Creating-a-Valid-Connection-String-Using-TCP-IP.md).  
  
## Options  
 **Default Port**  
 Specifies the port that the TCP/IP Net-library will use to attempt to connect to the target instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. The default value port is 1433.  
  
 When connecting to a default instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)], the client uses this value. If a default instance has been configured to listen on a different port, change this value to that port number.  
  
 When connecting to a named instance of [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)], the client will attempt to obtain the port number from the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Browser Service running on the server computer. If the [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Browser Service is not running, the port number must be provided through this setting, or as part of the connection string.  
  
 **Enabled**  
 Possible values are **Yes** and **No**.  
  
 **Keep Alive**  
 This parameter (in milliseconds) controls how often TCP attempts to verify that an idle connection is still intact by sending a **KEEPALIVE** packet. The default is 30000 milliseconds.  
  
 **Keep Alive Interval**  
 This parameter (in milliseconds) determines the interval separating **KEEPALIVE** retransmissions until a response is received. The default is 1000 milliseconds.  
  
## See Also  
 [Choosing a Network Protocol](assetId:///6565fb7d-b076-4447-be90-e10d0dec359a)   
 [New Alias (Alias Tab)](../../Topics/TopicNameNotContainA/New-Alias--Alias-Tab-.md)   
 [<Alias\> Properties (Alias Tab)](../Topic/%3CAlias%3E%20Properties%20\(Alias%20Tab\).md)