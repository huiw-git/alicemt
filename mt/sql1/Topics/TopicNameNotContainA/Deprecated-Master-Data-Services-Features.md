---
title: "Deprecated Master Data Services Features"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d8506bda-66dd-45a4-bfc9-3a10fa665acc
caps.latest.revision: 19
caps.handback.revision: 0
manager: mblythe
---
# Deprecated Master Data Services Features
This topic describes the deprecated [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] features that are still available in [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)]. These features are scheduled to be removed in a future release of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. Deprecated features should not be used in new applications.  
  
## Explicit Hierarchies, Collections, and Related Components  
 Explicit hierarchies, collections and related components are deprecated. Members that before were modeled as consolidated member types (explicit hierarchy parent) and collection member types will be modeled as leaf members in derived hierarchies. The following new features enable derived hierarchies to take the place of explicit hierarchies.  
  
-   Recursive Derived Hierarchies can now be used to assign member security permissions.  
  
     An explicit hierarchy is analogous to a recursive derived hierarchy with a single, non-recursive level below the recursive level. A recursive derived hierarchy can be complex by including level(s) below and/or above a recursive level.  
  
-   In Explorer, the derived hierarchy page now shows unassigned (unused) members for each hierarchy level. Unused nodes are grouped by hierarchy level. Members can be moved between the Unused and Root nodes, by dragging and dropping or by cutting and pasting.  
  
     In System Administration, unused nodes are visible in the **Preview** pane. In Security, the unused nodes are visible in the **Hierarchy Member Permissions** pane. Any member whether under the **Root** node or **Unused** node, can be assigned a permission. The **Root**, **Unused**, and **Unused** pseudo members can also be assigned permissions.  
  
-   The stored procedure, mdm.udpConvertCollectionAndConsolidatedMembersToLeaf, converts explicit hierarchies to recursive derived hierarchies, and coverts consolidated and collection members to leaf members.  
  
     Explicit hierarchies and consolidated and collection member types are still supported, so running the stored procedure is optional. However, if you use these items it is recommended that you run the stored procedure because they are deprecated.  
  
 For information about explicit hierarchies, collections, and consolidated members see the following topics.  
  
-   [Explicit Hierarchies (Master Data Services)](../../Topics/TopicNameNotContainA/Explicit-Hierarchies--Master-Data-Services-.md)  
  
-   [Collections (Master Data Services)](../../Topics/TopicNameNotContainA/Collections--Master-Data-Services-.md)  
  
-   [Members (Master Data Services)](../../Topics/TopicNameNotContainA/Members--Master-Data-Services-.md)  
  
## External Resources  
 Blog post, [Deprecated: Explicit Hierarchies and Collections](http://go.microsoft.com/fwlink/p/?LinkId=615373), on msdn.com.  
  
## See Also  
 [Discontinued Master Data Services Features](../../Topics/TopicNameNotContainA/Discontinued-Master-Data-Services-Features.md)