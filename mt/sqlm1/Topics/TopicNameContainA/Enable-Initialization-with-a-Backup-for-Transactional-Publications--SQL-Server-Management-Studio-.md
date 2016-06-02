---
title: Enable Initialization with a Backup for Transactional Publications (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
---
# Enable Initialization with a Backup for Transactional Publications (SQL Server Management Studio)
  To initialize a subscription to a transactional publication from a backup, enable the publication to allow initialization from a backup, and then specify backup information when creating the subscription:  
  
-   Enable the publication on the **Subscription Options** page of the **Publication Properties \- \<Publication\>** dialog box. For more information about accessing this dialog box, see [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
-   Specify backup information with the stored procedure [sp_addsubscription &#40;Transact-SQL&#41;](../Topic/sp_addsubscription%20\(Transact-SQL\).md). For more information about the parameters required by **sp\_addsubscription**, see [Initialize a Transactional Subscription from a Backup &#40;Replication Transact-SQL Programming&#41;](../Topic/Initialize%20a%20Transactional%20Subscription%20from%20a%20Backup%20\(Replication%20Transact-SQL%20Programming\).md).  
  
### To enable initialization with a backup  
  
1.  On the **Subscription Options** page of the **Publication Properties \- \<Publication\>** dialog box, select a value of **True** for the **Allow initialization from backup files** option.  
  
## See Also  
 [Initialize a Transactional Subscription Without a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Transactional-Subscription-Without-a-Snapshot.md)  
  
  