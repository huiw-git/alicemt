---
title: Getting Started with System-Versioned Temporal Tables
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-tables
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d431f216-82cf-4d97-825e-bb35d3d53a45
---
# Getting Started with System-Versioned Temporal Tables
  Depending on your scenario, you can either create new system\-versioned temporal tables or modify existing ones by adding temporal attributes to the existing table schema.   
When the data in temporal table is modified, the system builds version history transparently to applications and end users. As a result, working with system\-versioned temporal tables does not require any change to the way table is modified or how the latest \(actual\) state of the data is queried.   
In addition to regular DML and querying, temporal also provides convenient and easy ways to get insights from data history through extended Transact\-SQL syntax.   
Every system\-versioned table has a history table assigned but it is completely transparent for the users unless they want to optimize workload performance or storage footprint by creating additional indexes or choosing different storage options.    
The following diagram depicts typical workflow with  system\-versioned temporal tables:   
![Getting Started with Temporal](../../Images\Image\ImageNotContaina/Getting-Started-with-Temporal.png "Getting Started with Temporal")  
  
 This topic is divided into the following 5 subtopics:  
  
-   [Creating a System-Versioned Temporal Table](../../Topics\TopicNameContainA/Creating-a-System-Versioned-Temporal-Table.md)  
  
-   [Modifying Data in a System-Versioned Temporal Table](../../Topics\TopicNameContainA/Modifying-Data-in-a-System-Versioned-Temporal-Table.md)  
  
-   [Querying Data in a System-Versioned Temporal Table](../../Topics\TopicNameContainA/Querying-Data-in-a-System-Versioned-Temporal-Table.md)  
  
-   [Changing the Schema of a System-Versioned Temporal Table](../../Topics\TopicNameContainA/Changing-the-Schema-of-a-System-Versioned-Temporal-Table.md)  
  
-   [Stopping System-Versioning on a System-Versioned Temporal Table](../../Topics\TopicNameContainA/Stopping-System-Versioning-on-a-System-Versioned-Temporal-Table.md)  
  
## Did this Article Help You? We’re Listening  
 What information are you looking for, and did you find it? We’re listening to your feedback to improve the content. Please submit your comments to [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Getting%20Started%20with%20System-Versioned%20Temporal%20Tables%20page)  
  
## See Also  
 [Temporal Tables](../../Topics\TopicNameNotContainA/Temporal-Tables.md)   
 [Temporal Table System Consistency Checks](../../Topics\TopicNameNotContainA/Temporal-Table-System-Consistency-Checks.md)   
 [Partitioning with Temporal Tables](../../Topics\TopicNameNotContainA/Partitioning-with-Temporal-Tables.md)   
 [Temporal Table Considerations and Limitations](../../Topics\TopicNameNotContainA/Temporal-Table-Considerations-and-Limitations.md)   
 [Temporal Table Security](../../Topics\TopicNameNotContainA/Temporal-Table-Security.md)   
 [Manage Retention of Historical Data in System-Versioned Temporal Tables](../../Topics\TopicNameNotContainA/Manage-Retention-of-Historical-Data-in-System-Versioned-Temporal-Tables.md)   
 [System-Versioned Temporal Tables with Memory-Optimized Tables](../../Topics\TopicNameNotContainA/System-Versioned-Temporal-Tables-with-Memory-Optimized-Tables.md)   
 [Temporal Table Metadata Views and Functions](../../Topics\TopicNameNotContainA/Temporal-Table-Metadata-Views-and-Functions.md)  
  
  