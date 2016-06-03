---
title: Specify a Merge Subscription Type and Conflict Resolution Priority (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
---
# Specify a Merge Subscription Type and Conflict Resolution Priority (SQL Server Management Studio)
  Specify a merge subscription type and conflict resolution priority on the **Subscription Type** page of the New Subscription Wizard. For more information about using this wizard, see [Create a Pull Subscription](../../Topics\TopicNameContainA/Create-a-Pull-Subscription.md) and [Create a Push Subscription](../../Topics\TopicNameContainA/Create-a-Push-Subscription.md).  
  
 Subscription type cannot be modified after a subscription is created, but priority can be modified for the server subscription type in the **Subscription Properties \- \<Publisher\>: \<PublicationDatabase\>** dialog box. For more information about accessing this dialog box, see [View and Modify Push Subscription Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Push-Subscription-Properties.md) and [View and Modify Pull Subscription Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Pull-Subscription-Properties.md).  
  
### To specify a merge subscription type and conflict resolution priority  
  
1.  On the **Subscription Type** page of the New Subscription Wizard, select **Client** or **Server** for the **Subscription Type** option.  
  
2.  If you select a subscription type of **Server**, also enter a value \(0.00 to 99.99\) for the **Priority for Conflict Resolution** option.  
  
### To modify the conflict resolution priority  
  
1.  In the **Subscription Properties \- \<Publisher\>: \<PublicationDatabase\>** at the Publisher, enter a value \(0.00 to 99.99\) for the **Priority** option.  
  
2.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
## See Also  
 [Advanced Merge Replication Conflict Detection and Resolution](../../Topics\TopicNameNotContainA/Advanced-Merge-Replication-Conflict-Detection-and-Resolution.md)   
 [Subscribe to Publications](../../Topics\TopicNameNotContainA/Subscribe-to-Publications.md)  
  
  