---
title: MSSQL_ENG020574
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4e98f8de-287c-4090-81ee-dc8f80dfa6a1
---
# MSSQL_ENG020574
    
## Message Details  
  
|||  
|-|-|  
|Product Name|SQL Server|  
|Event ID|20574|  
|Event Source|MSSQLSERVER|  
|Component|[!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)]|  
|Symbolic Name||  
|Message Text|Subscriber '%s' subscription to article '%s' in publication '%s' failed data validation.|  
  
## Explanation  
 The data at the Subscriber was validated against the data at the Publisher, and the data did not match; therefore validation failed. For more information about validation, see [Validate Replicated Data](../../Topics\TopicNameNotContainA/Validate-Replicated-Data.md).  
  
## User Action  
 We recommend that you do the following:  
  
-   Determine why validation failed.  
  
-   Correct the underlying issue that caused the failure.  
  
-   Bring the data into convergence by reinitializing the subscription or through another method.  
  
## See Also  
 [Errors and Events Reference &#40;Replication&#41;](../Topic/Errors%20and%20Events%20Reference%20\(Replication\).md)  
  
  