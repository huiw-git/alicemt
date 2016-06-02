---
title: Subscription Properties - Publisher
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d4b2bc8b-0431-4331-8305-8992c96d0d34
---
# Subscription Properties - Publisher
  The **Subscription Properties** dialog box at the Publisher allows you to view and set properties for push subscriptions. You can also view some properties for pull subscriptions, but the **Subscriptions Properties** dialog box at the Subscriber displays additional properties and allows properties to be modified.  
  
 Each property in the **Subscription Properties** dialog box includes a description. Click a property to see its description displayed at the bottom of the dialog box. This topic provides additional information on a number of properties, most of which are displayed at the Publisher only for push subscriptions. The properties are grouped into the following categories:  
  
-   Properties that apply to all subscriptions.  
  
-   Properties that apply to transactional subscriptions.  
  
-   Properties that apply to merge subscriptions.  
  
 If an option is displayed as read\-only, it can only be set when the subscription is created. If you want to set options that are not available in the New Subscription Wizard, create the subscription with stored procedures. For more information, see [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md) and [Create a Push Subscription](../../Topics\TopicNameContainA/Create-a-Push-Subscription.md).  
  
## Options for all subscriptions  
 **Security**  
 Click the **Agent process account** row, and then click the properties button \(**...**\) to change the account under which the Distribution Agent or Merge Agent runs at the Distributor. To change the account under which the Distribution Agent or Merge Agent makes connections to the Subscriber, click **Subscriber connection**, and then click the properties button \(**...**\).  
  
 For more information about the permissions required for each agent, see [Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
## Options for transactional subscriptions  
 **Prevent transaction looping**  
 Determines whether the Distribution Agent sends transactions that originated at the Subscriber back to the Subscriber. This option is used for bidirectional transactional replication. For more information, see [Bidirectional Transactional Replication](../../Topics\TopicNameNotContainA/Bidirectional-Transactional-Replication.md).  
  
 **Updatable subscription**  
 Determines whether Subscriber changes are replicated back to the Publisher. Changes can be replicated using queued updating or immediate updating. The option **Subscriber update method** determines which method to use. For more information, see [Updatable Subscriptions for Transactional Replication](../../Topics\TopicNameNotContainA/Updatable-Subscriptions-for-Transactional-Replication.md).  
  
## Options for merge subscriptions  
 **Partition definition \(HOST\_NAME\)**  
 For a publication that uses parameterized filters, merge replication evaluates one of two system functions \(or both if the filter references both functions\) during synchronization to determine the data that a Subscriber should receive: **SUSER\_SNAME\(\)** or **HOST\_NAME\(\)**. By default, **HOST\_NAME\(\)** returns the name of the computer on which the Merge Agent is running, but you can override this value in the New Subscription Wizard. For more information on parameterized filters and overriding **HOST\_NAME\(\)**, see [Parameterized Row Filters](../../Topics\TopicNameNotContainA/Parameterized-Row-Filters.md).  
  
 **Subscription type** and **Priority**  
 Displays whether the subscription is a client or server subscription \(this cannot be changed after the subscription has been created\). Server subscriptions can republish data to other Subscribers and can be assigned a priority for conflict resolution.  
  
 If you selected a subscription type of server in the New Subscription Wizard, the Subscriber is given a priority that is used during conflict resolution.  
  
 **Resolve conflicts interactively**  
 Determines whether to use the Interactive Resolver user interface to resolve conflicts during merge synchronization. This requires a value of **Enable** for **Use Windows Synchronization Manager**. For more information, see [Interactive Conflict Resolution](../../Topics\TopicNameNotContainA/Interactive-Conflict-Resolution.md).  
  
## See Also  
 [View and Modify Pull Subscription Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Pull-Subscription-Properties.md)   
 [View and Modify Push Subscription Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Push-Subscription-Properties.md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)  
  
  