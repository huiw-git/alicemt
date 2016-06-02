---
title: Rollback Member Revision History (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d39d3474-20e7-429f-9c8d-fcc4eb0854fc
---
# Rollback Member Revision History (Master Data Services)
  A member revision history is recorded each time a member is changed. You can rollback a member revision history to a previous version.  
  
## Prerequisites  
  
-   You must have permission to update at least one of the attributes of the selected member. When you rollback a revision history, all the attribute values that can be updated will be rolled back to the previous version values.  
  
-   Revision history is available only when the transaction log type of the entity is member.  
  
 **To rollback a member revision history**  
  
1.  In Master Data Manager, click Explorer.  
  
2.  Choose the entity and the member to rollback.  
  
3.  Click **View History.**  
  
4.  Choose the revision to rollback, and then click **Rollback**.  
  
## See Also  
 [Member Revision History &#40;Master Data Services&#41;](../Topic/Member%20Revision%20History%20\(Master%20Data%20Services\).md)   
 [Change the Entity Transaction Log Type &#40;Master Data Services&#41;](../Topic/Change%20the%20Entity%20Transaction%20Log%20Type%20\(Master%20Data%20Services\).md)  
  
  