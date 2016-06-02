---
title: Add Non-SQL Server Subscriber
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
---
# Add Non-SQL Server Subscriber
  Replication supports creating push subscriptions to snapshot and transactional publications for Oracle and IBM DB2 Subscribers.  
  
## Options  
 **Type of Subscriber to add**  
 Select an Oracle Subscriber or IBM DB2 Subscriber. For more information about support for these Subscribers, see [Non-SQL Server Subscribers](../../Topics\TopicNameNotContainA/Non-SQL-Server-Subscribers.md).  
  
 **Data source name**  
 The name used to locate the database on a network. Replication produces a connection string for the database using the data source name, combined with the login, password, and any connection options you specify in the **Distribution Agent Security** page in this wizard.  
  
> [!NOTE]  
>  The data source name and connection string are not validated by [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] until the Distribution Agent attempts to initialize the subscription.  
  
## See Also  
 [Create a Subscription for a Non-SQL Server Subscriber](../../Topics\TopicNameContainA/Create-a-Subscription-for-a-Non-SQL-Server-Subscriber.md)   
 [Non-SQL Server Subscribers](../../Topics\TopicNameNotContainA/Non-SQL-Server-Subscribers.md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)  
  
  