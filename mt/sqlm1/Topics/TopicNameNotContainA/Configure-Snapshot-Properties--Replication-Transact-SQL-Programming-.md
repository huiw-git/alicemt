---
title: Configure Snapshot Properties (Replication Transact-SQL Programming)
ms.custom: na
ms.devlang: 
  - TSQL
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 978d150f-8971-458a-ab2b-3beba5937b46
---
# Configure Snapshot Properties (Replication Transact-SQL Programming)
  Snapshot properties can be defined and modified programmatically using replication stored procedures, where the stored procedures used depend on the type of publication.  
  
### To configure snapshot properties when creating a snapshot or transactional publication  
  
1.  At the Publisher, execute [sp\_addpublication](../Topic/sp_addpublication%20\(Transact-SQL\).md). Specify a publication name for **@publication**, a value of either **snapshot** or **continuous** for **@repl\_freq**, and one or more of the following snapshot\-related parameters:  
  
    -   **@alt\_snapshot\_folder** \- specify a path if the snapshot for this publication is accessed from that location instead of or in addition to the snapshot default folder.  
  
    -   **@compress\_snapshot** \- specify a value of **true** if the snapshot files in the alternate snapshot folder are compressed in the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] CAB file format.  
  
    -   **@pre\_snapshot\_script** \- specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.  
  
    -   **@post\_snapshot\_script** \- specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.  
  
    -   **@snapshot\_in\_defaultfolder** \- specify a value of **false** if the snapshot is available only in a non\-default location.  
  
     For more information about creating publications, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md).  
  
### To configure snapshot properties when creating a merge publication  
  
1.  At the Publisher, execute [sp\_addmergepublication](../Topic/sp_addmergepublication%20\(Transact-SQL\).md). Specify a publication name for **@publication**, a value of either **snapshot** or **continuous** for **@repl\_freq**, and one or more of the following snapshot\-related parameters:  
  
    -   **@alt\_snapshot\_folder** \- specify a path if the snapshot for this publication is accessed from that location instead of or in addition to the snapshot default folder.  
  
    -   **@compress\_snapshot** \- specify a value of **true** if the snapshot files in the alternate snapshot folder are compressed in the CAB file format.  
  
    -   **@pre\_snapshot\_script** \- specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.  
  
    -   **@post\_snapshot\_script** \- specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.  
  
    -   **@snapshot\_in\_defaultfolder** \- specify a value of **false** if the snapshot is available only in a non\-default location.  
  
2.  For more information about creating publications, see [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md).  
  
### To modify snapshot properties of an existing snapshot or transactional publication  
  
1.  At the Publisher on the publication database, execute [sp\_changepublication](../Topic/sp_changepublication%20\(Transact-SQL\).md). Specify a value of **1** for **@force\_invalidate\_snapshot** and one of the following values for **@property**:  
  
    -   **alt\_snapshot\_folder** \-also specify a new path to the alternate snapshot folder for **@value**.  
  
    -   **compress\_snapshot** \- also specify a value of either **true** or **false** for **@value** to indicate whether the snapshot files in the alternate snapshot folder are compressed in the CAB file format.  
  
    -   **pre\_snapshot\_script** \- also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.  
  
    -   **post\_snapshot\_script** \- also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.  
  
    -   **snapshot\_in\_defaultfolder** \- also specify a value of either **true** or **false** to indicate whether the snapshot is available only in a non\-default location.  
  
2.  \(Optional\) At the Publisher on the publication database, execute [sp\_changepublication\_snapshot](../Topic/sp_changepublication_snapshot%20\(Transact-SQL\).md). Specify **@publication** and one or more of the scheduling or security credential parameters being changed.  
  
    > [!IMPORTANT]  
    >  When possible, prompt users to enter security credentials at runtime. If you must store credentials in a script file, you must secure the file to prevent unauthorized access.  
  
3.  Run the [Replication Snapshot Agent](../../Topics\TopicNameNotContainA/Replication-Snapshot-Agent.md) from the command prompt or start the Snapshot Agent job to generate a new snapshot. For more information, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
### To modify snapshot properties of an existing merge publication  
  
1.  At the Publisher on the publication database, execute [sp\_changemergepublication](../Topic/sp_changemergepublication%20\(Transact-SQL\).md). Specify a value of **1** for **@force\_invalidate\_snapshot** and one of the following values for **@property**:  
  
    -   **alt\_snapshot\_folder** \-also specify a new path to the alternate snapshot folder for **@value**.  
  
    -   **compress\_snapshot** \- also specify a value of either **true** or **false** for **@value** to indicate whether the snapshot files in the alternate snapshot folder are compressed in the CAB file format.  
  
    -   **pre\_snapshot\_script** \- also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization before the initial snapshot is applied.  
  
    -   **post\_snapshot\_script** \- also for **@value** specify the file name and full path of a **.sql** file that will be executed at the Subscriber during initialization after the initial snapshot is applied.  
  
    -   **snapshot\_in\_defaultfolder** \- also specify a value of either **true** or **false** to indicate whether the snapshot is available only in a non\-default location.  
  
2.  Run the [Replication Snapshot Agent](../../Topics\TopicNameNotContainA/Replication-Snapshot-Agent.md) from the command prompt or start the Snapshot Agent job to generate a new snapshot. For more information, see [Create and Apply the Initial Snapshot](../../Topics\TopicNameNotContainA/Create-and-Apply-the-Initial-Snapshot.md).  
  
## Example  
 This example creates a publication that uses an alternate snapshot folder and a compressed snapshot.  
  
 [!CODE [HowTo#sp_mergealtsnapshot](../CodeSnippet/SQL15/replication/howto#sp_mergealtsnapshot)]  
  
## See Also  
 [Alternate Snapshot Folder Locations](../../Topics\TopicNameNotContainA/Alternate-Snapshot-Folder-Locations.md)   
 [Compressed Snapshots](../../Topics\TopicNameNotContainA/Compressed-Snapshots.md)   
 [Execute Scripts Before and After the Snapshot Is Applied](../../Topics\TopicNameNotContainA/Execute-Scripts-Before-and-After-the-Snapshot-Is-Applied.md)   
 [Replication System Stored Procedures Concepts](../Topic/Replication%20System%20Stored%20Procedures%20Concepts.md)   
 [Transfer Snapshots Through FTP](../../Topics\TopicNameNotContainA/Transfer-Snapshots-Through-FTP.md)   
 [Change Publication and Article Properties](../../Topics\TopicNameNotContainA/Change-Publication-and-Article-Properties.md)  
  
  