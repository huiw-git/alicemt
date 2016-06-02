---
title: Subscriber Types
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a70656cb-21c9-4489-be77-ccd396747e3b
---
# Subscriber Types
  Merge replication allows you to specify the types of Subscribers that a publication must support. Selecting Subscriber types sets the *publication compatibility level*, which determines which features can be used by a publication.  
  
 After a publication snapshot is created, the publication compatibility level can be increased \(made more restrictive\) on the **General** page of the **Publication Properties** dialog box; the compatibility level cannot be decreased.  
  
## Options  
 Select each Subscriber type that this publication must support.  
  
 [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]  
 The publication can use all features.  
  
 [!INCLUDE[ssEW](../../Token\Other/ssEW_md.md)]  
 The publication requires snapshot files to be in character format \(this is handled automatically by the Snapshot Agent\). [!INCLUDE[ssEW](../../Token\Other/ssEW_md.md)] also has a number of restrictions not related to compatibility level.  
  
 If this option is selected, the Web synchronization option is enabled for the publication. For more information about Web synchronization, see [Web Synchronization for Merge Replication](../../Topics\TopicNameNotContainA/Web-Synchronization-for-Merge-Replication.md).  
  
## See Also  
 [Publish Data and Database Objects](../../Topics\TopicNameNotContainA/Publish-Data-and-Database-Objects.md)   
 [Create a Publication](../../Topics\TopicNameContainA/Create-a-Publication.md)   
 [View and Modify Distributor and Publisher Properties](../../Topics\TopicNameNotContainA/View-and-Modify-Distributor-and-Publisher-Properties.md)   
 [Properties Reference &#40;Replication&#41;](../Topic/Properties%20Reference%20\(Replication\).md)  
  
  