---
title: MSSQL_ENG024070
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 23ac7e00-fab6-429b-9f85-2736a322aa65
---
# MSSQL_ENG024070
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|24070|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|A required privilege is not held by the client.|  
  
## Explanation  
 This is a general error that can be raised regardless of whether replication is being used. For a server in a replication topology, the error is typically raised because the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service account is changed by using the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows Service Control Manager instead of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager. When you try to run an agent job after changing the service account, the job might fail with an error message that is similar to the following:  
  
 "Executed as user: \<UserAccount\>. Replication\-Replication Snapshot Subsystem: agent \<AgentName\> failed. Executed as user: \<UserAccount\>. A required privilege is not held by the client. The step failed. \[SQLSTATE 42000\] \(Error 14151\). The step failed."  
  
 This problem occurs because the Windows Service Control Manager cannot grant the required permissions to the new service account for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent.  
  
## User Action  
 To avoid this problem in the future, always use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager instead of the Windows Service Control Manager to change service accounts and passwords.  
  
 To resolve this problem, use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager to change the service account back to the original account. Then, use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager to change to the new account. When you do this, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager adds the new account to the following security group:  
  
 SQLServer2008SQLAgentUser$ComputerName$InstanceName  
  
 Being a member of this security group grants to the new account the required permissions to run the replication agent job.  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)   
 [Manage Logins and Passwords in Replication](../../Topics\TopicNameNotContainA/Manage-Logins-and-Passwords-in-Replication.md)   
 [SQL Server Configuration Manager](../../Topics\TopicNameNotContainA/SQL-Server-Configuration-Manager.md)  
  
  