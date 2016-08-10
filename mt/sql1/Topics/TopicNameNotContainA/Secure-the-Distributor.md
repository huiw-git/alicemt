---
title: "Secure the Distributor"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 76d78229-0ff2-4aa4-9b4e-ad97534c5296
caps.latest.revision: 39
caps.handback.revision: 0
manager: jhubbard
---
# Secure the Distributor
The following replication agents connect to the Distributor: the Log Reader Agent, Snapshot Agent, Queue Reader Agent, Distribution Agent, and Merge Agent. It is important to provide an appropriate login for each of these agents while following the principle of granting the minimal rights necessary and also protecting the storage of all passwords:  
  
-   For information about managing logins and passwords, see [Manage Logins and Passwords in Replication](../../Topics/TopicNameNotContainA/Manage-Logins-and-Passwords-in-Replication.md).  
  
-   For detailed information about the permissions required for each agent, see [Replication Agent Security Model](../../Topics/TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
 In addition to managing logins and passwords appropriately, it is important to understand the role of the **repl_distributor** remote server link and the **distributor_admin** account.  
  
## Securing the Connection from the Publisher to the Distributor  
 To support the communication necessary when administrative stored procedures execute at the Publisher and update information at the Distributor, replication automatically configures the remote server **repl_distributor**. The **repl_distributor** remote server entry is used for communication to the distribution database regardless of whether the distribution database is contained within the Publisher instance (a local Distributor) or resides within a remote [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] instance (a remote Distributor).  
  
 When the distribution database is contained on a local instance, a random password is generated and configured automatically. When the distribution database is located on a remote instance, the administrator configures a shared password during setup of the Publisher and Distributor; this password is then used to provide authentication of traffic that traverses the **repl_distributor** link.  
  
 The Distributor uses the **repl_distributor** remote server entry to verify that the calling server is configured as a Publisher at the Distributor, validates the password supplied by the Publisher, and validates that the stored procedure is a replication stored procedure during execution.  
  
 The password configured for the **repl_distributor** remote server entry during setup is associated with a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login, **distributor_admin**, which is added to the **sysadmin** fixed server role at the Distributor. The **distributor_admin** login is used by replication stored procedures when connecting to the Distributor.  
  
> [!NOTE]  
>  Do not change the password for the **distributor_admin** manually. Always use the **sp_changedistributor_password** stored procedure, or the **Distributor Properties** or **Update Replication Passwords** dialog boxes in [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)], because password changes are then applied to local publications automatically.  
  
## Snapshot Folder Security  
 Ensure that the snapshot share has read access granted to the account under which the Merge Agent (for merge replication) or Distribution Agent (for snapshot or transactional replication) runs and write access granted to the account under which the Snapshot Agent runs. For more information about the snapshot folder, see [Secure the Snapshot Folder](../../Topics/TopicNameNotContainA/Secure-the-Snapshot-Folder.md).  
  
## See Also  
 [View and Modify Replication Security Settings](../../Topics/TopicNameNotContainA/View-and-Modify-Replication-Security-Settings.md)   
 [Enable Encrypted Connections to the Database Engine (SQL Server Configuration Manager)](../../Topics/TopicNameNotContainA/Enable-Encrypted-Connections-to-the-Database-Engine--SQL-Server-Configuration-Manager-.md)   
 [Replication Security Best Practices](../../Topics/TopicNameNotContainA/Replication-Security-Best-Practices.md)   
 [Security and Protection (Replication)](../../Topics/TopicNameNotContainA/Security-and-Protection--Replication-.md)