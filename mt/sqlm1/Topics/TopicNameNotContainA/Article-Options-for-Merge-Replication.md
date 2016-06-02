---
title: Article Options for Merge Replication
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 670abd41-d204-4cd7-a371-7664e603a0ce
---
# Article Options for Merge Replication
  There are many options for merge table articles that enable you to customize replication behavior to the needs of your applications. By using merge replication, you can do the following:  
  
-   Use row filters, join filters, and column filters. Filtering table articles enables you to create partitions of data to be published. For more information, see [Filter Published Data](../../Topics\TopicNameNotContainA/Filter-Published-Data.md).  
  
-   Specify whether changes at the Subscriber are uploaded to the Publisher. For applications in which some or all data should be read\-only at the Subscriber, download\-only articles provide a performance benefit. For more information, see [Optimize Merge Replication Performance with Download-Only Articles](../../Topics\TopicNameNotContainA/Optimize-Merge-Replication-Performance-with-Download-Only-Articles.md).  
  
-   Specify that deletes for one or more articles should not be tracked by replication triggers and system tables. This option can be useful in many application scenarios. These include scenarios that use batch deletes that do not need to be replicated. For more information, see [Optimize Merge Replication Performance with Conditional Delete Tracking](../../Topics\TopicNameNotContainA/Optimize-Merge-Replication-Performance-with-Conditional-Delete-Tracking.md).  
  
-   Specify the processing order of articles to make sure that articles are processed in the order required by your application. For more information, see [Specify the Processing Order of Merge Articles](../../Topics\TopicNameNotContainA/Specify-the-Processing-Order-of-Merge-Articles.md).  
  
-   Specify that a set of related records should be processed as a unit \(by default, merge replication processes changes to tables on a row\-by\-row basis\). For more information, see [Group Changes to Related Rows with Logical Records](../../Topics\TopicNameNotContainA/Group-Changes-to-Related-Rows-with-Logical-Records.md).  
  
-   Use conflict detection and resolution for cases in which the same data could be changed at more than one node in a topology. For more information, see [Detect and Resolve Merge Replication Conflicts](../../Topics\TopicNameNotContainA/Detect-and-Resolve-Merge-Replication-Conflicts.md).  
  
-   Specify schema options, such as whether constraints and triggers are copied to the Subscriber. For more information, see [Specify Schema Options](../../Topics\TopicNameNotContainA/Specify-Schema-Options.md).  
  
-   Use a business logic handler to respond to many conditions during synchronization. These include data changes, conflicts, and errors. For more information, see [Execute Business Logic During Merge Synchronization](../../Topics\TopicNameNotContainA/Execute-Business-Logic-During-Merge-Synchronization.md).  
  
## See Also  
 [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md)  
  
  