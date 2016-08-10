---
title: "Alternate Snapshot Folder Locations"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 437553b0-19df-4522-8f27-06b5bc747c69
caps.latest.revision: 37
caps.handback.revision: 0
manager: jhubbard
---
# Alternate Snapshot Folder Locations
Alternate snapshot locations enable you to store snapshot files in a location other than, or in addition to, the default location, which is typically located on the Distributor. Alternate locations can be on another server, on a network drive, or on removable media such as CD-ROMs or removable disks.  
  
 Alternate snapshot locations are stored as a property of the publication. Because the alternate snapshot location is a publication property, the Distribution Agent and the Merge Agent are able to locate the proper snapshot as part of the synchronization process.  
  
 If you want to specify an alternate snapshot folder location or if you want to compress snapshot files, create the publication without creating the initial snapshot immediately, set the publication properties for the snapshot location, and then run the Snapshot Agent for that publication. If you change the alternate location after creating the initial snapshot, the location of any generated snapshot for the publication will not be relocated to the new alternate location. In this case, depending on the publication settings, the Merge Agent or Distribution Agent might not be able to find the snapshot files at the new alternate location.  
  
> [!NOTE]  
>  Do not specify an alternate location (using the **Publication Properties** dialog box or [Snapshot Options](assetId:///c36e5865-25d5-42b7-b045-dc5036225081)) that is the same as the default snapshot folder location.  
  
> [!CAUTION]  
>  Do not use both WebSync and alternate snapshot folder locations at the same time.  
  
 **To specify alternate snapshot locations**  
  
-   [!INCLUDE[ssManStudioFull](../../Topics/TopicNameContainA/tokens/ssManStudioFull_md.md)]: [Specify an Alternate Snapshot Folder Location \(SQL Server Management Studio\)](../../Topics/TopicNameNotContainA/Specify-an-Alternate-Snapshot-Folder-Location--SQL-Server-Management-Studio-.md)  
  
-   Replication [!INCLUDE[tsql](../../Topics/TopicNameContainA/tokens/tsql_md.md)] programming: [Configure Snapshot Properties (Replication Transact-SQL Programming)](../../Topics/TopicNameNotContainA/Configure-Snapshot-Properties--Replication-Transact-SQL-Programming-.md)  
  
## See Also  
 [Initialize a Subscription with a Snapshot](../../Topics/TopicNameContainA/Initialize-a-Subscription-with-a-Snapshot.md)   
 [Snapshot Options](../../Topics/TopicNameNotContainA/Snapshot-Options.md)