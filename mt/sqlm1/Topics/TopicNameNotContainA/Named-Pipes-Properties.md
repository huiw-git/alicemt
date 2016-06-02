---
title: Named Pipes Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a5fd5b8e-f889-485b-89e3-d4010ec4c6ec
---
# Named Pipes Properties
  Use the **Protocol**page on the **Named Pipes Properties** dialog box to view or change the named pipe that [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] listens to, when using the Named Pipes protocol.  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] must be restarted to enable or disable the protocol, or change the named pipe.  
  
## Options  
 **Enabled**  
 Possible values are **Yes** and **No**.  
  
 **Pipe Name**  
 Specifies the named pipe on which [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] listens. By default, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] listens on: `\\.\pipe\sql\query` for the default instance and `\\.\pipe\MSSQL$<instancename>\sql\query` for a named instance. This field is limited to 2047 characters.  
  
## Creating an Alternate Named Pipe  
 To change the named pipe, type the new pipe name in the **Pipe Name** box and then stop and restart [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Since **sql\\query** is well known as the named pipe used by [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], changing the pipe can help reduce the risk of attack by malicious programs.  
  
### Example  
 Type **\\\\.\\pipe\\unit\\app** to listen on the **unit\\app** pipe.  
  
 Type **\\\\.\\pipe\\acct** to listen on the **acct** pipe.  
  
## See Also  
 [Enable or Disable a Server Network Protocol](../../Topics\TopicNameContainA/Enable-or-Disable-a-Server-Network-Protocol.md)   
 [Choosing a Network Protocol](../Topic/Choosing%20a%20Network%20Protocol.md)   
 [Creating a Valid Connection String Using Named Pipes](../Topic/Creating%20a%20Valid%20Connection%20String%20Using%20Named%20Pipes.md)  
  
  