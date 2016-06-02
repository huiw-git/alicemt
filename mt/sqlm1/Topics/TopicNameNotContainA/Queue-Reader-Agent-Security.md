---
title: Queue Reader Agent Security
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
---
# Queue Reader Agent Security
  The **Queue Reader Agent Security** dialog box allows you to specify the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows account under which the Queue Reader Agent runs and makes local connections to the Distributor. The agent connects to the Publisher using the account specified in the **Publisher Properties** dialog box \(available from the **Distributor Properties** dialog box\); the agent connects to the Subscriber using the same context as the Distribution Agent for the subscription. For more information, see [View and Modify Replication Security Settings](../../Topics\TopicNameNotContainA/View-and-Modify-Replication-Security-Settings.md).  
  
 The account must be valid with the correct password specified. Accounts and passwords are not validated until an agent runs.  
  
## Options  
 **Process account**  
 Enter a Windows account under which the Queue Reader Agent runs at the Distributor. The Windows account you specify must at minimum be a member of the **db\_owner** fixed database role in the distribution database.  
  
 **Password** and **Confirm password**  
 Enter the password for the Windows account.  
  
## See Also  
 [Manage Logins and Passwords in Replication](../../Topics\TopicNameNotContainA/Manage-Logins-and-Passwords-in-Replication.md)   
 [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md)   
 [Replication Agents Overview](../../Topics\TopicNameNotContainA/Replication-Agents-Overview.md)   
 [Replication Security Best Practices](../../Topics\TopicNameNotContainA/Replication-Security-Best-Practices.md)  
  
  