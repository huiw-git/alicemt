---
title: "Partitioning with Temporal Tables"
ms.custom: 
  - SQL2016_New_Updated
ms.date: 2016-04-26
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - dbe-tables
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 313714b8-4ad1-4c14-93a3-7f628a334a51
caps.latest.revision: 12
manager: jhubbard
---
# Partitioning with Temporal Tables
You can use partitioning on both the current and the history table independently. However, partitioning cannot be used to change the content of the data without system-versioning.  
  
> [!NOTE]  
>  Partitioning is an Enterprise Edition feature.  
  
-   **Current Table:**  
  
    -   **SWITCH IN** to the current table can be used to facilitate data loading and querying while **SYSTEM_VERSIONING** is **ON**  
  
    -   **SWITCH OUT** is not permitted while **SYSTEM_VERSIONING** is **ON**  
  
-   **History Table:**  
  
    -   **SWITCH OUT** from history table can performed while **SYSTEM_VERSIONING** is **ON** to purge portions of history data that is no longer relevant.  
  
    -   **SWITCH IN** is not allowed while **SYSTEM_VERSIONING** is **ON** since it can invalidate temporal data consistency.  
  
## Did this Article Help You? We’re Listening  
 What information are you looking for, and did you find it? We’re listening to your feedback to improve the content. Please submit your comments to [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Partitioning%20with%20Temporal%20Tables%20page)  
  
## See Also  
 [Temporal Tables](../../Topics/TopicNameNotContainA/Temporal-Tables.md)   
 [Getting Started with System-Versioned Temporal Tables](../../Topics/TopicNameNotContainA/Getting-Started-with-System-Versioned-Temporal-Tables.md)   
 [Temporal Table System Consistency Checks](../../Topics/TopicNameNotContainA/Temporal-Table-System-Consistency-Checks.md)   
 [Temporal Table Considerations and Limitations](../../Topics/TopicNameNotContainA/Temporal-Table-Considerations-and-Limitations.md)   
 [Temporal Table Security](../../Topics/TopicNameNotContainA/Temporal-Table-Security.md)   
 [Manage Retention of Historical Data in System-Versioned Temporal Tables](../../Topics/TopicNameNotContainA/Manage-Retention-of-Historical-Data-in-System-Versioned-Temporal-Tables.md)   
 [System-Versioned Temporal Tables with Memory-Optimized Tables](../../Topics/TopicNameNotContainA/System-Versioned-Temporal-Tables-with-Memory-Optimized-Tables.md)   
 [Temporal Table Metadata Views and Functions](../../Topics/TopicNameNotContainA/Temporal-Table-Metadata-Views-and-Functions.md)