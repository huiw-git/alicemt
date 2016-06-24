---
title: Specify Snapshot Format (SQL Server Management Studio)
H1: na
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
  Specify snapshot format on the **Snapshot** page of the **Publication Properties - <Publication\>** dialog box. For more information about accessing this dialog box, see [View and Modify Publication Properties](../../Topics/TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
### To specify snapshot format  
  
1.  On the **Snapshot** page of the **Publication Properties - <Publication\>** dialog box, select **Native SQL Server - all Subscribers must be servers running SQL Server** or **Character - required if a Publisher or Subscriber is not running SQL Server**.  
  
    > [!NOTE]  
    >  It is recommended to select the native format unless this publication must support subscriptions to a [!INCLUDE[ssEW](../../Topics/TopicNameContainA/includes/ssEW_md.md)] database or a non-[!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] database.  
  
2.  [!INCLUDE[clickOK](../../Topics/TopicNameContainA/includes/clickOK_md.md)]  
  
## See Also  
 [Configure Snapshot Properties &#40;Replication Transact-SQL Programming&#41;](../../Topics/TopicNameNotContainA/Configure-Snapshot-Properties--Replication-Transact-SQL-Programming-.md)   
 [Change Publication and Article Properties](../../Topics/TopicNameNotContainA/Change-Publication-and-Article-Properties.md)   
 [Initialize a Subscription with a Snapshot](../../Topics/TopicNameContainA/Initialize-a-Subscription-with-a-Snapshot.md)  
  
  