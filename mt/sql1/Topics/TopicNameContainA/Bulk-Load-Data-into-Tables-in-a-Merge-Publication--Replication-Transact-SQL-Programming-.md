---
title: "Bulk-Load Data into Tables in a Merge Publication (Replication Transact-SQL Programming)"
ms.custom: na
ms.date: 06/29/2016
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
caps.latest.revision: 34
manager: jhubbard
---
# Bulk-Load Data into Tables in a Merge Publication (Replication Transact-SQL Programming)
When data is loaded into tables using the [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md) or the [BULK INSERT](assetId:///be3984e1-5ab3-4226-a539-a9f58e1e01e2) command, by default, the merge replication triggers that maintain tracking data in the [MSmerge_contents](assetId:///8d68a61a-683f-4b20-92f9-c0a8d9ba0ad1) system table are not fired. You can either force the merge replication triggers to fire as the data is loaded, or you can insert the generated replication metadata programmatically after the bulk copy operation using replication stored procedures.  
  
### To bulk-load data into tables published by merge replication using the bcp utility  
  
1.  At either the Publisher or Subscriber, execute the [bcp Utility](../../Topics/TopicNameNotContainA/bcp-Utility.md) or [BULK INSERT](assetId:///be3984e1-5ab3-4226-a539-a9f58e1e01e2) to insert data into a table published using merge replication.  
  
2.  Use one of the following methods to ensure that replication metadata is generated for the inserted data.  
  
    -   Execute the bulk copy using the FIRE_TRIGGERS option.  
  
    -   On the database into which data was inserted, execute [sp_addtabletocontents (Transact-SQL)](assetId:///2ea27001-74f4-463e-bf1b-b6b5a86b9219). Specify the table name into which the data was inserted for **@table_name**.