---
title: Compressed Snapshots
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 979ffa7c-3a88-4e70-8cf2-b8d452fd7a7f
---
# Compressed Snapshots
  Compressing snapshot files is appropriate when you are transferring snapshots over a slow network or you are saving them to removable media and an uncompressed snapshot is too large to fit on the media. Compressing snapshot files is useful in these situations, but compression increases the time to generate and apply the snapshot.  
  
 Compressed snapshot files are written in the [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] CAB file format, which can compress files of 2 GB or less \(if the snapshot files are larger than 2GB, they cannot be compressed\). To compress files, they must be written to an alternate snapshot folder \(files written to the default snapshot folder cannot be compressed\). For more information on alternate snapshot folders, see [Alternate Snapshot Folder Locations](../../Topics\TopicNameNotContainA/Alternate-Snapshot-Folder-Locations.md).  
  
 Files are uncompressed at the location where the Distribution Agent or Merge Agent runs; pull subscriptions are typically used with compressed snapshots so that files are uncompressed at the Subscriber. When the Subscriber receives a compressed file, the file is written initially to a temporary location. After the compressed file is copied to the Subscriber, the snapshot files in the compressed file are decompressed, in order, one file at a time by the CAB utility. Space required at the Subscriber is the size of the compressed file plus the largest uncompressed file.  
  
> [!NOTE]  
>  Compressed snapshots can, in some cases, improve the performance of transferring snapshot files across the network. However, compressing the snapshot requires additional processing by the Snapshot Agent when generating the snapshot files, and by the Distribution Agent or Merge Agent when applying the snapshot files. This may slow down snapshot generation and increase the time it takes to apply a snapshot in some cases. Additionally, compressed snapshots cannot be resumed if a network failure occurs; therefore they are not suitable for unreliable networks. Consider these tradeoffs carefully when using compressed snapshots across a network.  
  
 **To compress and deliver snapshot files**  
  
-   [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]: [Compress Snapshot Files &#40;SQL Server Management Studio&#41;](../Topic/Compress%20Snapshot%20Files%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   Replication [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] programming: [Configure Snapshot Properties &#40;Replication Transact-SQL Programming&#41;](../Topic/Configure%20Snapshot%20Properties%20\(Replication%20Transact-SQL%20Programming\).md)  
  
## See Also  
 [Initialize a Subscription with a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Subscription-with-a-Snapshot.md)   
 [Snapshot Options](../../Topics\TopicNameNotContainA/Snapshot-Options.md)  
  
  