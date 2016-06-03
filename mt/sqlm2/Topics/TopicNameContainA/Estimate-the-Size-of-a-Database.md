---
title: Estimate the Size of a Database
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5b240161-eba4-44b0-946c-61a8fc00fc8c
---
# Estimate the Size of a Database
  When you design a database, you may have to estimate how large the database will be when filled with data. Estimating the size of the database can help you determine the hardware configuration you will require to do the following:  
  
-   Achieve the performance required by your applications.  
  
-   Guarantee the appropriate physical amount of disk space required to store the data and indexes.  
  
 Estimating the size of a database can also help you determine whether the database design needs refining. For example, you may determine that the estimated size of the database is too large to implement in your organization and that more normalization is required. Conversely, the estimated size may be smaller than expected. This would allow you to denormalize the database to improve query performance.  
  
 To estimate the size of a database, estimate the size of each table individually and then add the values obtained. The size of a table depends on whether the table has indexes and, if they do, what type of indexes.  
  
## In This Section  
  
|Topic|Description|  
|-----------|-----------------|  
|[Estimate the Size of a Table](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Table.md)|Defines the steps and calculations needed to estimate the amount of space required to store the data in a table and associated indexes.|  
|[Estimate the Size of a Heap](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Heap.md)|Defines the steps and calculations needed to estimate the amount of space required to store the data in a heap. A heap is a table that does not have a clustered index.|  
|[Estimate the Size of a Clustered Index](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Clustered-Index.md)|Defines the steps and calculations needed to estimate the amount of space required to store the data in a clustered index.|  
|[Estimate the Size of a Nonclustered Index](../../Topics\TopicNameContainA/Estimate-the-Size-of-a-Nonclustered-Index.md)|Defines the steps and calculations needed to estimate the amount of space required to store the data in a nonclustered index.|  
  
  