---
title: &lt;AgentName&gt; Agent Security
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
---
# &lt;AgentName&gt; Agent Security
  The **\<AgentName\> Agent Security** page allows you to specify the accounts under which the Distribution Agent \(for transactional and snapshot replication\) or Merge Agent \(for merge replication\) run and make connections to the computers in a replication topology. For information on permissions required by agents and best practices for replication security, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md) and [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md).  
  
## Options  
 Click the properties button \(**...**\) in the row for each Subscriber to access the **Distribution Agent Security** or **Merge Agent Security** dialog box. Click **Help** on the dialog box that is launched for more information on the permissions required for accounts used by the agents.  
  
 After settings have been entered in one of the dialog boxes, connection information for the Subscriber is displayed in the grid.  
  
 **Agent for Subscriber**  
 The name of each Subscriber.  
  
 **Connection to Distributor**  
 Displayed for transactional and snapshot replication. The context under which the connection to the Distributor is made. Local connections are always made using the context of the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows account under which the agent runs:  
  
-   For push subscriptions, the local connection is the connection to the Distributor, so this field will always display: **Impersonate '\<Domain\>\\\<Login\>'** or **Impersonate '\<Computer\>\\\<Login\>'** for push subscriptions.  
  
-   For pull subscriptions, the connection can also be made under the context of a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login. The field displays one of the following: **Use login '\<Login\>'**, **Impersonate '\<Domain\>\\\<Login\>'** or **Impersonate '\<Computer\>\\\<Login\>'**. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] recommends that all connections be made using the context of the Windows account.  
  
 **Connection to Publisher & Distributor**  
 Displayed for merge replication. The context under which the connections to the Publisher and Distributor are made. Local connections are always made using the context of the Windows account under which the agent runs:  
  
-   For push subscriptions, the local connection is the connection to the Publisher and Distributor, so this field will always display: **Impersonate '\<Domain\>\\\<Login\>'** or **Impersonate '\<Computer\>\\\<Login\>'** for push subscriptions.  
  
-   For pull subscriptions, the connection can also be made under the context of a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login. The field displays one of the following: **Use login '\<Login\>'**, **Impersonate '\<Domain\>\\\<Login\>'** or **Impersonate '\<Computer\>\\\<Login\>'**. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] recommends that all connections be made using the context of the Windows account.  
  
 **Connection to Subscriber**  
 The context under which the connection to the Subscriber is made. Local connections are always made using the context of the Windows account under which the agent runs:  
  
-   For pull subscriptions, the local connection is the connection to the Subscriber, so this field will always display: **Impersonate '\<Domain\>\\\<Login\>'** or **Impersonate '\<Computer\>\\\<Login\>'** for push subscriptions.  
  
-   For push subscriptions, the connection can also be made under the context of a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] login. The field displays one of the following: **Use login '\<Login\>'**, **Impersonate '\<Domain\>\\\<Login\>'** or **Impersonate '\<Computer\>\\\<Login\>'**. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] recommends that all connections be made using the context of the Windows account.  
  
## See Also  
 [View and Modify Pull Subscription Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Pull-Subscription-Properties.md)   
 [View and Modify Push Subscription Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Push-Subscription-Properties.md)   
 [Manage Logins and Passwords in Replication](../../Topics\TopicNameNotContainA/Manage-Logins-and-Passwords-in-Replication.md)   
 [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md)   
 [Security and Protection &#40;Replication&#41;](../Topic/Security%20and%20Protection%20\(Replication\).md)  
  
  