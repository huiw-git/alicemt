---
title: Log Reader Agent Security (Peer-to-Peer Replication)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6575e2a8-16bb-449c-bdca-4a4202d0972f
---
# Log Reader Agent Security (Peer-to-Peer Replication)
  The **Log Reader Agent Security** page allows you to specify the accounts under which the Log Reader Agent at each peer runs and makes connections. For information on permissions required by agents and best practices for replication security, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md) and [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md).  
  
> [!NOTE]  
>  There is one Log Reader Agent for each database that is published using transactional replication. If the Log Reader Agent for a database has already been configured \(either for a publication in a previous run of this wizard or for another transactional publication in the same database\), you cannot change the credentials it uses in this wizard. If you specify new credentials, they are ignored. To change credentials, use the **Publication Properties** dialog box. For more information, see [View and Modify Replication Security Settings](../../Topics\TopicNameNotContainA/View-and-Modify-Replication-Security-Settings.md).  
  
## Options  
 Click the properties button \(**...**\) in the row for each peer to access the **Log Reader Agent Security** dialog box. Click **Help** on the **Log Reader Agent Security** dialog box that is launched for more information on the permissions required for accounts used by the agents.  
  
 After settings have been entered in the dialog box, connection information for the Subscriber is displayed in the grid.  
  
 **Agents for Publisher**  
 The name of each peer server instance.  
  
 **Peer Database**  
 The database that serves as the publication database and subscription database at each peer.  
  
 **Connection to Distributor**  
 The context under which the connection to the Distributor is made. The local connection to the Distributor is always made using the context of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows account under which the agent runs, so this field will always display **Impersonate '\<Domain\>\\\<Login\>'** or **Impersonate '\<Computer\>\\\<Login\>'**.  
  
 **Connection to Publisher**  
 The context under which the connection to the Publisher is made. The connection to the Publisher can be made using a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login or using the context of the Windows account under which the agent runs. The field displays one of the following: **Use login '\<Login\>'**, **Impersonate '\<Domain\>\\\<Login\>'** or **Impersonate '\<Computer\>\\\<Login\>'**. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] recommends that all connections be made using the context of the Windows account.  
  
## See Also  
 [Administer a Peer-to-Peer Topology &#40;Replication Transact-SQL Programming&#41;](../Topic/Administer%20a%20Peer-to-Peer%20Topology%20\(Replication%20Transact-SQL%20Programming\).md)   
 [Peer-to-Peer Transactional Replication](../../Topics\TopicNameNotContainA/Peer-to-Peer-Transactional-Replication.md)  
  
  