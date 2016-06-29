---
title: MSSQL_ENG018456
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3daa8144-d81f-445a-b6c3-4bb3e9fd1526
---
# MSSQL_ENG018456
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|18456|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/includes/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Login failed for user '%.*ls'.%.\*ls|  
  
## Explanation  
 Error MSSQL_ENG018456 is raised whenever a login attempt fails. If the error message includes the account **distributor_admin** (Login failed for user 'distributor_admin'.), the issue is with an account used by replication. Replication creates a remote server, **repl_distributor**, which allows communication between the Distributor and Publisher. The login **distributor_admin** is associated with this remote server and must have a valid password.  
  
## User Action  
 Ensure that you have specified a password for this account. For more information, see [Secure the Distributor](../../Topics/TopicNameNotContainA/Secure-the-Distributor.md).  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../../Topics/TopicNameNotContainA/Errors-and-Events-Reference--Replication-.md)  
  
  