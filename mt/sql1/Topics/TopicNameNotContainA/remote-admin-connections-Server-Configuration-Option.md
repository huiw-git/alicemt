---
title: "remote admin connections Server Configuration Option"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bf32b60a-7a48-401f-b6be-b5e2e46c413f
caps.latest.revision: 16
caps.handback.revision: 0
manager: jhubbard
---
# remote admin connections Server Configuration Option
[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] provides a dedicated administrator connection (DAC). The DAC lets an administrator access a running server to execute diagnostic functions or [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] statements, or to troubleshoot problems on the server, even when the server is locked or running in an abnormal state and not responding to a [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] connection. By default, the DAC is only available from a client on the server. To enable client applications on remote computers to use the DAC, use the remote admin connections option of sp_configure.  
  
 By default, the DAC only listens on the loop-back IP address (127.0.0.1), port 1434. If TCP port 1434 is not available, a TCP port is dynamically assigned when the [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] starts up. When more than one instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] is installed on a computer, check the error log for the TCP port number.  
  
 The following table lists the possible values for the remote admin connections option.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Indicates only local connections are allowed by using the DAC.|  
|1|Indicates remote connections are allowed by using the DAC.|  
  
## Example  
 The following example enables the DAC from a remote computer.  
  
```  
sp_configure 'remote admin connections', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## See Also  
 [Diagnostic Connection for Database Administrators](../../Topics/TopicNameNotContainA/Diagnostic-Connection-for-Database-Administrators.md)