---
title: Article Options for Transactional Replication
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
---
# Article Options for Transactional Replication
  There are a number of options for articles in transactional publications. With transactional replication, you can do the following:  
  
-   Specify how changes are propagated from the Publisher to Subscribers. For more information, see [Specify How Changes Are Propagated for Transactional Articles](../../Topics\TopicNameNotContainA/Specify-How-Changes-Are-Propagated-for-Transactional-Articles.md).  
  
-   Specify that the execution of a stored procedure be replicated. This is useful in replicating the results of maintenance\-oriented stored procedures that affect large amounts of data. For more information, see [Publishing Stored Procedure Execution in Transactional Replication](../../Topics\TopicNameNotContainA/Publishing-Stored-Procedure-Execution-in-Transactional-Replication.md).  
  
-   Specify schema options, such as whether constraints and triggers are copied to the Subscriber. For more information, see [Specify Schema Options](../../Topics\TopicNameNotContainA/Specify-Schema-Options.md).  
  
-   Use row filters and column filters. Filtering table articles enables you to create partitions of data to be published. For more information, see [Filter Published Data](../../Topics\TopicNameNotContainA/Filter-Published-Data.md).  
  
## See Also  
 [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md)  
  
  