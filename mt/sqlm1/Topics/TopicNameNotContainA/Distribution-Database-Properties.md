---
title: Distribution Database Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0f404ab9-1237-4936-8df5-888baab6a245
---
# Distribution Database Properties
  The **Distribution Database Properties** dialog box allows you to view a number of properties and to set the transaction retention period and history retention period for the database.  
  
## Options  
 **Name**  
 The name of the distribution database, which defaults to 'distribution' \(read\-only\).  
  
 **File locations**  
 The location of the database file and the log file \(read\-only\).  
  
 **Transaction retention period**  
 Also known as the distribution retention period. The length of time transactions are stored for transactional replication. For more information, see [Subscription Expiration and Deactivation](../../Topics\TopicNameNotContainA/Subscription-Expiration-and-Deactivation.md).  
  
 **History retention period**  
 The length of time history metadata is stored for all types of replication.  
  
 **Queue Reader Agent security**  
 The Queue Reader Agent is used by transactional replication with queued updating subscriptions. A Queue Reader Agent is created automatically if you select **Transactional publication with updating subscriptions** on the **Publication Type** page of the New Publication Wizard. Click **Security Settings…** to change the account under which the agent runs and makes connections to the Distributor.  
  
 A Queue Reader Agent can also be created by selecting **Create Queue Reader Agent** on this page \(this option is disabled if the agent has already been created\).  
  
 Additional connection information for the Queue Reader Agent is specified in two places:  
  
-   The agent connects to the Publisher using the credentials specified in the **Publisher Properties** dialog box, which is available from the **Publishers** page of the **Distributor Properties** dialog box.  
  
-   The agent connects to the Subscriber using the credentials specified for the Distribution Agent in the New Subscription Wizard.  
  
 For more information, see  \\[Replication Agent Security Model](../../Topics\TopicNameNotContainA/Replication-Agent-Security-Model.md).  
  
## See Also  
 [Configure Distribution](../../Topics\TopicNameNotContainA/Configure-Distribution.md)   
 [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md)   
 [Create a Push Subscription](../../Topics\TopicNameContainA/Create-a-Push-Subscription.md)   
 [View and Modify Distributor and Publisher Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Distributor-and-Publisher-Properties.md)  
  
  