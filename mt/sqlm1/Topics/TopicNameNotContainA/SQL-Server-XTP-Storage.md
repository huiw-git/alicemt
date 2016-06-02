---
title: SQL Server XTP Storage
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - database-engine
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4070580b-880d-4f4c-abcc-626a4fe0c9a2
---
# SQL Server XTP Storage
  The SQL Server XTP Storage performance object contains counters related to on\-disk storage for In\-Memory OLTP in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 This table describes the **SQL Server XTP Storage** counters.  
  
|Counter|Description|  
|-------------|-----------------|  
|**Checkpoints Closed**|Count of checkpoints closed done by online agent.|  
|**Checkpoints Completed**|Count of checkpoints processed by offline checkpoint thread.|  
|**Core Merges Completed**|The number of core merges completed by the merge worker thread. These merges still need to be installed.|  
|**Merge Policy Evaluations**|The number of merge policy evaluations since the server started.|  
|**Merge Requests Outstanding**|The number of merge requests outstanding since the server started.|  
|**Merges Abandoned**|The number of merges abandoned due to failure.|  
|**Merges Installed**|The number of merges successfully installed.|  
|**Total Files Merged**|The total number of source files merged. This count can be used to find the average number of source files in the merge.|  
  
## See Also  
 [SQL Server XTP &#40;In-Memory OLTP&#41; Performance Counters](../Topic/SQL%20Server%20XTP%20\(In-Memory%20OLTP\)%20Performance%20Counters.md)  
  
  