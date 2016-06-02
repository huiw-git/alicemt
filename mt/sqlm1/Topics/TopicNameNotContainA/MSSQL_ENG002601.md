---
title: MSSQL_ENG002601
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 657c3ae6-9e4b-4c60-becc-4caf7435c1dc
---
# MSSQL_ENG002601
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|2601|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name|N\/A|  
|Message Text|Cannot insert duplicate key row in object '%.\*ls' with unique index '%.\*ls'.|  
  
## Explanation  
 This is a general error that can be raised regardless of whether a database is replicated. In replicated databases, the error is typically raised because primary keys have not been managed appropriately across the topology. In a distributed environment it is essential to ensure that the same value is not inserted into a primary key column or any other unique column at more than one node. Possible causes include the following:  
  
-   Inserts and updates to a row are occurring at more than one node. Merge replication and updatable subscriptions for transactional replication both provide conflict detection and resolution, but it is still preferable to insert or update a given row at only one node. Peer\-to\-peer transactional does not provide conflict detection and resolution; it requires that inserts and updates be partitioned.  
  
-   A row was inserted at a Subscriber that should be read\-only. Subscribers to snapshot publications should be treated as read\-only, as should Subscribers to transactional publications unless updatable subscriptions or peer\-to\-peer transactional replication is used.  
  
-   A table with an identity column is being used, but the column is not managed appropriately.  
  
-   In merge replication, this error can also occur during an insert into the system table **MSmerge\_contents**; the error raised is similar to: Cannot insert duplicate key row in object 'MSmerge\_contents' with unique index 'ucl1SycContents.'  
  
## User Action  
 The action required depends on the reason the error was raised:  
  
-   Inserts and updates to a row are occurring at more than one node.  
  
     Regardless of the type of replication used, we recommend that you partition inserts and updates whenever possible, because this reduces the processing required for conflict detection and resolution. For peer\-to\-peer transactional replication, partitioning inserts and updates is required. For more information, see [Peer-to-Peer Transactional Replication](../../Topics\TopicNameNotContainA/Peer-to-Peer-Transactional-Replication.md).  
  
-   A row was inserted at a Subscriber that should be read\-only.  
  
     Do not insert or update rows at the Subscriber unless you are using merge replication, transactional replication with updatable subscriptions, or peer\-to\-peer transactional replication.  
  
-   A table with an identity column is being used, but the column is not managed appropriately.  
  
     For merge replication and transactional replication with updatable subscriptions, identity columns should be managed automatically by replication. For peer\-to\-peer transactional replication, they must be managed manually. For more information, see [Replicate Identity Columns](../../Topics\TopicNameNotContainA/Replicate-Identity-Columns.md).  
  
-   The error occurs during an insert into the system table **MSmerge\_contents**.  
  
     This error can occur because of an incorrect value for the join filter property **join\_unique\_key**. This property should be set to TRUE only if the joined column in the parent table is unique. If the property is set to TRUE, but the column is not unique, this error is raised. For more information on setting this property, see [Define and Modify a Join Filter Between Merge Articles](../../Topics\TopicNameContainA/Define-and-Modify-a-Join-Filter-Between-Merge-Articles.md).  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)  
  
  