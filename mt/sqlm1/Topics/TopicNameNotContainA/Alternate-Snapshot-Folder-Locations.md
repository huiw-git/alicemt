---
title: Alternate Snapshot Folder Locations
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 437553b0-19df-4522-8f27-06b5bc747c69
---
# Alternate Snapshot Folder Locations
  Alternate snapshot locations enable you to store snapshot files in a location other than, or in addition to, the default location, which is typically located on the Distributor. Alternate locations can be on another server, on a network drive, or on removable media such as CD\-ROMs or removable disks.  
  
 Alternate snapshot locations are stored as a property of the publication. Because the alternate snapshot location is a publication property, the Distribution Agent and the Merge Agent are able to locate the proper snapshot as part of the synchronization process.  
  
 If you want to specify an alternate snapshot folder location or if you want to compress snapshot files, create the publication without creating the initial snapshot immediately, set the publication properties for the snapshot location, and then run the Snapshot Agent for that publication. If you change the alternate location after creating the initial snapshot, the location of any generated snapshot for the publication will not be relocated to the new alternate location. In this case, depending on the publication settings, the Merge Agent or Distribution Agent might not be able to find the snapshot files at the new alternate location.  
  
> [!NOTE]  
>  Do not specify an alternate location \(using the **Publication Properties** dialog box or [sp_changepublication &#40;Transact-SQL&#41;](../Topic/sp_changepublication%20\(Transact-SQL\).md)\) that is the same as the default snapshot folder location.  
  
> [!CAUTION]  
>  Do not use both WebSync and alternate snapshot folder locations at the same time.  
  
 **To specify alternate snapshot locations**  
  
-   [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)]: [Specify an Alternate Snapshot Folder Location &#40;SQL Server Management Studio&#41;](../Topic/Specify%20an%20Alternate%20Snapshot%20Folder%20Location%20\(SQL%20Server%20Management%20Studio\).md)  
  
-   Replication [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] programming: [Configure Snapshot Properties &#40;Replication Transact-SQL Programming&#41;](../Topic/Configure%20Snapshot%20Properties%20\(Replication%20Transact-SQL%20Programming\).md)  
  
## See Also  
 [Initialize a Subscription with a Snapshot](../../Topics\TopicNameContainA/Initialize-a-Subscription-with-a-Snapshot.md)   
 [Snapshot Options](../../Topics\TopicNameNotContainA/Snapshot-Options.md)  
  
  