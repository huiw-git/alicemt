---
title: Execute Scripts Before and After the Snapshot Is Applied
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9a6872c2-9bed-477f-9d2f-332d640edcf2
---
# Execute Scripts Before and After the Snapshot Is Applied
  You can specify scripts to execute at the Subscriber before or after the snapshot is applied. Scripts can be used for a variety of reasons, such as creating logins and schemas \(object owners\) at each Subscriber.  
  
 You specify a file location for each script, and the Snapshot Agent copies the script files to the current snapshot folder each time snapshot processing occurs. The Distribution Agent or the Merge Agent runs the pre\-snapshot script before any of the replicated object scripts when applying a snapshot. The Distribution Agent or the Merge Agent runs the post\-snapshot script after all the other replicated object scripts and data have been applied. After the snapshot application is complete and script files run successfully, the script files are removed from the working directory on the Subscriber.  
  
 The script is run by launching the **sqlcmd** utility. Before deploying a script, run it with **sqlcmd** to ensure it executes as expected. The contents of scripts that are executed before and after the snapshot is applied must be repeatable. For example, if you create a table in the script, you should first check for its existence and take appropriate action if it exists. The script must be repeatable because if you need to reinitialize a subscription for which the script has already been applied, the script will be applied again when the new snapshot is applied during reinitialization.  
  
 If you are compressing the snapshot file \(by putting it in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] CAB file format\), the scripts are also compressed and placed in the CAB file. After the compressed snapshot file is transferred to the Subscriber and decompressed to a working directory on the Subscriber, any script indicated as a pre\-snapshot script is executed. Likewise, any post\-snapshot script is decompressed and executed at the Subscriber as the last step in applying the snapshot.  
  
 **To execute scripts before and after the snapshot is applied**  
  
-   [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]: [How to: Execute Scripts Before and After a Snapshot is Applied \(SQL Server Management Studio\)](../Topic/Execute%20Scripts%20Before%20and%20After%20a%20Snapshot%20Is%20Applied%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   Replication [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] programming: [Configure Snapshot Properties &#40;Replication Transact-SQL Programming&#41;](../Topic/Configure%20Snapshot%20Properties%20\(Replication%20Transact-SQL%20Programming\).md)  
  
## See Also  
 [Initialize a Subscription with a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Subscription-with-a-Snapshot.md)   
 [Snapshot Options](../../Topics\TopicNameNotContainA/Snapshot-Options.md)  
  
  