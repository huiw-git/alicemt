---
title: Replication Security Best Practices
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1ab2635d-0992-4c99-b17d-041d02ec9a7c
---
# Replication Security Best Practices
  Replication moves data in distributed environments ranging from intranets on a single domain to applications that access data between untrusted domains and over the Internet. It is important to understand the best approach for securing replication connections under these different circumstances.  
  
 The following information is relevant to replication in all environments:  
  
-   Encrypt the connections between computers in a replication topology using an industry standard method, such as Virtual Private Networks \(VPN\), Secure Sockets Layer \(SSL\), or IP Security \(IPSEC\). For more information, see [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md). For information about using VPN and SSL for replicating data over the Internet, see [Securing Replication Over the Internet](../../Topics\TopicNameNotContainA/Securing-Replication-Over-the-Internet.md).  
  
     If you use SSL to secure the connections between computers in a replication topology, specify a value of **1** or **2** for the **\-EncryptionLevel** parameter of each replication agent \(a value of **2** is recommended\). A value of **1** specifies that encryption is used, but the agent does not verify that the SSL server certificate is signed by a trusted issuer; a value of **2** specifies that the certificate is verified. Agent parameters can be specified in agent profiles and on the command line. For more information, see:  
  
    -   [Work with Replication Agent Profiles](../../Topics\TopicNameNotContainA/Work-with-Replication-Agent-Profiles.md)  
  
    -   [View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;](../Topic/View%20and%20Modify%20Replication%20Agent%20Command%20Prompt%20Parameters%20\(SQL%20Server%20Management%20Studio\).md)  
  
    -   [Replication Agent Executables Concepts](../Topic/Replication%20Agent%20Executables%20Concepts.md)  
  
-   Run each replication agent under a different Windows account, and use Windows Authentication for all replication agent connections. For more information about specifying accounts, see [Manage Logins and Passwords in Replication](../../Topics\TopicNameNotContainA/Manage-Logins-and-Passwords-in-Replication.md).  
  
-   Grant only the required permissions to each agent. For more information, see the "Permissions Required by Agents" section of [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
-   Ensure all Merge Agent and Distribution Agent accounts are in the publication access list \(PAL\). For more information, see [Secure the Publisher](../../Topics\TopicNameNotContainA/Secure-the-Publisher.md).  
  
-   Follow the principle of least privilege by allowing accounts in the PAL only the permissions they need to perform replication tasks. Do not add the logins to any fixed server roles that are not required for replication.  
  
-   Configure the snapshot share to allow read access by all Merge Agents and Distribution Agents. In the case of snapshots for publications with parameterized filters, ensure that each folder is configured to allow access only to the appropriate Merge Agent accounts.  
  
-   Configure the snapshot share to allow write access by the Snapshot Agent.  
  
-   If you use pull subscriptions, use a network share rather than a local path for the snapshot folder.  
  
 If your replication topology includes computers that are not in the same domain or are in domains that do not have trust relationships with each other, you can use Windows Authentication or [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication for the connections made by agents \(For more information about domains, see the Windows documentation\). It is recommended as a security best practice that you use Windows Authentication.  
  
-   To use Windows Authentication:  
  
    -   Add a local Windows account \(not a domain account\) for each agent at the appropriate nodes \(use the same name and password at each node\). For example, the Distribution Agent for a push subscription runs at the Distributor and makes connections to the Distributor and Subscriber. The Windows account for the Distribution Agent should be added to the Distributor and Subscriber.  
  
    -   Ensure that a given agent \(for example the Distribution Agent for a subscription\) runs under the same account at each computer.  
  
-   To use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication:  
  
    -   Add a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] account for each agent at the appropriate nodes \(use the same account name and password at each node\). For example, the Distribution Agent for a push subscription runs at the Distributor and makes connections to the Distributor and Subscriber. The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] account for the Distribution Agent should be added to the Distributor and Subscriber.  
  
    -   Ensure that a given agent \(for example the Distribution Agent for a subscription\) makes connections under the same account at each computer.  
  
    -   In situations that require [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Authentication, access to UNC snapshot shares is often not available \(for example access might be blocked by a firewall\). In this case, you can transfer the snapshot to Subscribers through file transfer protocol \(FTP\). For more information, see [Transfer Snapshots Through FTP](../../Topics\TopicNameNotContainA/Transfer-Snapshots-Through-FTP.md).  
  
## See Also  
 [Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;](../Topic/Enable%20Encrypted%20Connections%20to%20the%20Database%20Engine%20\(SQL%20Server%20Configuration%20Manager\).md)   
 [Replication over the Internet](../../Topics\TopicNameNotContainA/Replication-over-the-Internet.md)   
 [Secure the Subscriber](../../Topics\TopicNameNotContainA/Secure-the-Subscriber.md)   
 [Secure the Distributor](../../Topics\TopicNameNotContainA/Secure-the-Distributor.md)   
 [Secure the Publisher](../../Topics\TopicNameNotContainA/Secure-the-Publisher.md)   
 [Security and Protection &#40;Replication&#41;](../Topic/Security%20and%20Protection%20\(Replication\).md)  
  
  