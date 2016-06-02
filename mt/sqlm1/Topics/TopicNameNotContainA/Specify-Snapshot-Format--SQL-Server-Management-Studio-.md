---
title: Specify Snapshot Format (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c95f545-731a-4743-9acb-0b325ef9b98b
---
# Specify Snapshot Format (SQL Server Management Studio)
  Specify snapshot format on the **Snapshot** page of the **Publication Properties \- \<Publication\>** dialog box. For more information about accessing this dialog box, see [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
### To specify snapshot format  
  
1.  On the **Snapshot** page of the **Publication Properties \- \<Publication\>** dialog box, select **Native SQL Server \- all Subscribers must be servers running SQL Server** or **Character \- required if a Publisher or Subscriber is not running SQL Server**.  
  
    > [!NOTE]  
    >  It is recommended to select the native format unless this publication must support subscriptions to a [!INCLUDE[ssEW](../../Token\Other/ssEW_md.md)] database or a non\-[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] database.  
  
2.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
## See Also  
 [Configure Snapshot Properties &#40;Replication Transact-SQL Programming&#41;](../Topic/Configure%20Snapshot%20Properties%20\(Replication%20Transact-SQL%20Programming\).md)   
 [Change Publication and Article Properties](../../Topics\TopicNameNotContainA/Change-Publication-and-Article-Properties.md)   
 [Initialize a Subscription with a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Subscription-with-a-Snapshot.md)  
  
  