---
title: Bulk-Load Data into Tables in a Merge Publication (Replication Transact-SQL Programming)
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
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
---
# Bulk-Load Data into Tables in a Merge Publication (Replication Transact-SQL Programming)
  When data is loaded into tables using the [bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md) or the [BULK INSERT](../Topic/BULK%20INSERT%20\(Transact-SQL\).md) command, by default, the merge replication triggers that maintain tracking data in the [MSmerge\_contents](../Topic/MSmerge_contents%20\(Transact-SQL\).md) system table are not fired. You can either force the merge replication triggers to fire as the data is loaded, or you can insert the generated replication metadata programmatically after the bulk copy operation using replication stored procedures.  
  
### To bulk\-load data into tables published by merge replication using the bcp utility  
  
1.  At either the Publisher or Subscriber, execute the [bcp Utility](../../Topics\TopicNameNotContainA/bcp-Utility.md) or [BULK INSERT](../Topic/BULK%20INSERT%20\(Transact-SQL\).md) to insert data into a table published using merge replication.  
  
2.  Use one of the following methods to ensure that replication metadata is generated for the inserted data.  
  
    -   Execute the bulk copy using the FIRE\_TRIGGERS option.  
  
    -   On the database into which data was inserted, execute [sp_addtabletocontents &#40;Transact-SQL&#41;](../Topic/sp_addtabletocontents%20\(Transact-SQL\).md). Specify the table name into which the data was inserted for **@table\_name**.  
  
  