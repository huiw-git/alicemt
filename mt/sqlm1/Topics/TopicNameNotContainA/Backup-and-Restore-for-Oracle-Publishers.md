---
title: Backup and Restore for Oracle Publishers
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5f181d0-cacf-442b-8b7a-202b3cfc358b
---
# Backup and Restore for Oracle Publishers
  Follow these guidelines when backing up and restoring:  
  
-   Ensure the Log Reader Agent does not run and that other database activity on the published tables does not occur while the Publisher is being backed up.  
  
-   Backup up the Publisher and Distributor at the same time.  
  
-   If the Publisher or Distributor must be restored, reinitialize all subscriptions.  
  
-   To restore a Subscriber from a backup \(without having to reinitialize subscriptions\), the transactions delivered to the distribution database after the last subscription database backup was completed must still be available. The length of time transactions are available depends on distribution retention settings. For information on these settings, see [Subscription Expiration and Deactivation](../../Topics\TopicNameNotContainA/Subscription-Expiration-and-Deactivation.md).  
  
-   If the Publisher or Distributor becomes out of sync as the result of a database restore, the replication agents log error messages. At this point, you must drop and recreate all relevant publications and subscriptions:  
  
    1.  Script the definition of the publications and subscriptions. For more information, see [Scripting Replication](../../Topics\TopicNameNotContainA/Scripting-Replication.md).  
  
         If the definition of the publications has changed between the versions of the Publisher and Distributor states, you will need to modify the scripts.  
  
    2.  Drop the publications and subscriptions.  
  
    3.  Run the scripts created in step 1.  
  
     If the Publisher must be dropped and reconfigured, drop the **MSSQLSERVERDISTRIBUTOR** public synonym and the configured Oracle replication user with the **CASCADE** option to remove all replication objects from the Oracle Publisher.  
  
## See Also  
 [Back Up and Restore Replicated Databases](../../Topics\TopicNameNotContainA/Back-Up-and-Restore-Replicated-Databases.md)   
 [Configure an Oracle Publisher](../../Topics\TopicNameNotContainA/Configure-an-Oracle-Publisher.md)   
 [Oracle Publishing Overview](../../Topics\TopicNameNotContainA/Oracle-Publishing-Overview.md)  
  
  