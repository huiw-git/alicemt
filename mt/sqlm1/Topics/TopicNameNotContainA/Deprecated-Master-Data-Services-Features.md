---
title: Deprecated Master Data Services Features
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d8506bda-66dd-45a4-bfc9-3a10fa665acc
---
# Deprecated Master Data Services Features
  This topic describes the deprecated [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] features that are still available in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. These features are scheduled to be removed in a future release of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. Deprecated features should not be used in new applications.  
  
## Explicit Hierarchies, Collections, and Related Components  
 Explicit hierarchies, collections and related components are deprecated. Members that before were modeled as consolidated member types \(explicit hierarchy parent\) and collection member types will be modeled as leaf members in derived hierarchies. The following new features enable derived hierarchies to take the place of explicit hierarchies.  
  
-   Recursive Derived Hierarchies can now be used to assign member security permissions.  
  
     An explicit hierarchy is analogous to a recursive derived hierarchy with a single, non\-recursive level below the recursive level. A recursive derived hierarchy can be complex by including level\(s\) below and\/or above a recursive level.  
  
-   In Explorer, the derived hierarchy page now shows unassigned \(unused\) members for each hierarchy level. Unused nodes are grouped by hierarchy level. Members can be moved between the Unused and Root nodes, by dragging and dropping or by cutting and pasting.  
  
     In System Administration, unused nodes are visible in the **Preview** pane. In Security, the unused nodes are visible in the **Hierarchy Member Permissions** pane. Any member whether under the **Root** node or **Unused** node, can be assigned a permission. The **Root**, **Unused**, and **Unused** pseudo members can also be assigned permissions.  
  
-   The stored procedure, mdm.udpConvertCollectionAndConsolidatedMembersToLeaf, converts explicit hierarchies to recursive derived hierarchies, and coverts consolidated and collection members to leaf members.  
  
     Explicit hierarchies and consolidated and collection member types are still supported, so running the stored procedure is optional. However, if you use these items it is recommended that you run the stored procedure because they are deprecated.  
  
 For information about explicit hierarchies, collections, and consolidated members see the following topics.  
  
-   [Explicit Hierarchies &#40;Master Data Services&#41;](../Topic/Explicit%20Hierarchies%20\(Master%20Data%20Services\).md)  
  
-   [Collections &#40;Master Data Services&#41;](../Topic/Collections%20\(Master%20Data%20Services\).md)  
  
-   [Members &#40;Master Data Services&#41;](../Topic/Members%20\(Master%20Data%20Services\).md)  
  
## Attribute Entity Transaction Log Type  
Entity transaction log type "Attribute" is deprecated, please migrate to the "Member" entity transaction log type. For information about entity transaction log types, see the following topic:
* [Change the Entity Transaction Log Type (Master Data Services)](Change%20the%20Entity%20Transaction%20Log%20Type%20\(Master%20Data%20Services\).md)
* [Member Revision History](Member%20Revision%20History%20\(Master%20Data%20Services\).md)
  
## External Resources  
 Blog post, [Deprecated: Explicit Hierarchies and Collections](http://go.microsoft.com/fwlink/p/?LinkId=615373), on msdn.com.  
  
## See Also  
 [Discontinued Master Data Services Features](../../Topics\TopicNameNotContainA/Discontinued-Master-Data-Services-Features.md)  
  
  