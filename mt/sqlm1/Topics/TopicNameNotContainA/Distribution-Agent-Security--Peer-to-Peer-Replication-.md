---
title: Distribution Agent Security (Peer-to-Peer Replication)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: def6bf26-c640-4caf-ad30-05d1e649541d
---
# Distribution Agent Security (Peer-to-Peer Replication)
  The **Distribution Agent Security** page allows you to specify the accounts under which the Distribution Agent runs and makes connections to the computers in a peer\-to\-peer topology. For information on permissions required by agents and best practices for replication security, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md) and [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md).  
  
> [!NOTE]  
>  If the Distribution Agent for a subscription has already been configured in a previous run of this wizard, you cannot change the credentials it uses in this wizard. If you specify new credentials, they are ignored. To change credentials, use the **Subscription Properties** dialog box. For more information, see [View and Modify Replication Security Settings](../../Topics\TopicNameNotContainA/View-and-Modify-Replication-Security-Settings.md).  
  
## Options  
 Click the properties button \(**...**\) in the row for each Subscriber to access the **Distribution Agent Security** dialog box. Click **Help** on the **Distribution Agent Security** dialog box that is launched for more information on the permissions required for accounts used by the agents.  
  
 After settings have been entered in one of the dialog boxes, connection information for the Subscriber is displayed in the grid.  
  
 **Agent for Subscriber**  
 The name of each peer.  
  
 **Peer Database**  
 The database at the peer that will serve as both a publication database and subscription database.  
  
 **Connection to Distributor**  
 The context under which the connection to the Distributor is made. Local connections are always made using the context of the Windows account under which the agent runs. This wizard creates push subscriptions \(the local connection is the connection to the Distributor\), so this field will always display: **Impersonate '\<Domain\>\\\<Login\>'** or **Impersonate '\<Computer\>\\\<Login\>'**.  
  
 **Connection to Subscriber**  
 The context under which the connection to the Subscriber is made. The connection can be made using the context of the Windows account under which the agent runs or under the context of a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login. The field displays one of the following: **Use login '\<Login\>'**, **Impersonate '\<Domain\>\\\<Login\>'** or **Impersonate '\<Computer\>\\\<Login\>'**. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] recommends that all connections be made using the context of the Windows account.  
  
## See Also  
 [Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](../Topic/Administer%20a%20Peer-to-Peer%20Topology%20\(Replication%20Transact-SQL%20Programming\).md)   
 [Peer-to-Peer Transactional Replication](../../Topics\TopicNameNotContainA/Peer-to-Peer-Transactional-Replication.md)  
  
  