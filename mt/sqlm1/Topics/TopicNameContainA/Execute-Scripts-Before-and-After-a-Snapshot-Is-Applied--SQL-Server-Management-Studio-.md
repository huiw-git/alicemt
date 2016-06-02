---
title: Execute Scripts Before and After a Snapshot Is Applied (SQL Server Management Studio)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b7bb1e4c-5b48-4bb1-9dc8-47c911f2cc82
---
# Execute Scripts Before and After a Snapshot Is Applied (SQL Server Management Studio)
  Specify an optional script to execute before or after the snapshot is applied on the **Snapshot** page of the **Publication Properties \- \<Publication\>** dialog box. For more information about accessing this dialog box, see [View and Modify Publication Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Publication-Properties.md).  
  
> [!NOTE]  
>  These options are not available if the **Snapshot format** option is set to **Character**.  
  
### To execute a script before or after a snapshot is applied  
  
1.  On the **Snapshot** page of the **Publication Properties \- \<Publication\>** dialog box:  
  
    -   To specify a script to execute before the snapshot is applied, click **Browse** to navigate to the script, or enter a path to the script in the **Before applying the snapshot, execute this script** text box.  
  
        > [!NOTE]  
        >  The Distribution Agent or Merge Agent must have read permissions for the directory you specify. If pull subscriptions are used, you must specify a shared directory as a universal naming convention \(UNC\) path, such as \\\\computername\\scripts\\myscript.sql.  
  
    -   To specify a script to execute after the snapshot is applied, click **Browse** to navigate to the script, or enter a UNC path to the script in the **After applying the snapshot, execute this script** text box.  
  
2.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
## See Also  
 [Configure Snapshot Properties &#40;Replication Transact-SQL Programming&#41;](../Topic/Configure%20Snapshot%20Properties%20\(Replication%20Transact-SQL%20Programming\).md)   
 [Change Publication and Article Properties](../../Topics\TopicNameNotContainA/Change-Publication-and-Article-Properties.md)   
 [Execute Scripts Before and After the Snapshot Is Applied](../../Topics\TopicNameNotContainA/Execute-Scripts-Before-and-After-the-Snapshot-Is-Applied.md)   
 [Initialize a Subscription with a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Subscription-with-a-Snapshot.md)  
  
  