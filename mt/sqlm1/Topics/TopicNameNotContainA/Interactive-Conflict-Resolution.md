---
title: Interactive Conflict Resolution
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - replication
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 172c60c7-f605-4eb5-b185-54ae9e9d3c60
---
# Interactive Conflict Resolution
  [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] replication provides an Interactive Resolver, which allows you to resolve conflicts manually during on\-demand synchronization in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows Synchronization Manager. Activated at run time, the Interactive Resolver is a graphical interface that displays data for each conflicting row, and provides options for viewing and editing the conflict data, and resolving each conflict individually.  
  
 The Interactive Resolver resembles the Conflict Viewer. However, the Conflict Viewer displays the results of conflicts that are already resolved after merge synchronization, and the Interactive Resolver displays each conflict prior to resolution, allowing you to determine the outcome of each conflict during merge synchronization. Someone should be available to monitor the Interactive Resolver when a conflict occurs.  
  
> [!NOTE]  
>  Interactive Resolution requires Windows Synchronization Manager. If a synchronization is performed outside of Windows Synchronization Manager \(as a scheduled synchronization or an on demand synchronization in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] or Replication Monitor\), conflicts are resolved automatically without user intervention, according to the resolver specified for the article. Conflicts that involve logical records are not displayed in the Interactive Resolver. To view information about these conflicts, use replication stored procedures. For more information, see [View Conflict Information for Merge Publications &#40;Replication Transact-SQL Programming&#41;](../Topic/View%20Conflict%20Information%20for%20Merge%20Publications%20\(Replication%20Transact-SQL%20Programming\).md).  
  
## Article Resolvers and the Interactive Resolver  
 Conflict resolvers \(either the default resolver, a business logic handler, or a custom resolver\) are assigned to specific articles when a publication is created, and use a set of rules to determine which set of data should be used when conflicting row data is entered. The Interactive Resolver is not a separate conflict resolver with rules for determining conflict winners and losers, but a tool used in conjunction with default and custom resolvers. The article resolver still determines the winning and losing row, but the Interactive Resolver allows user intervention to accept, reject, or modify the results.  
  
 To use the Interactive Resolver, interactive resolution must be enabled for each article and subscription that requires it. After it is enabled for one or more articles and subscriptions, the Interactive Resolver is used when a conflict is detected during merge synchronization.  
  
 To use the Interactive Resolver, see [Specify Interactive Conflict Resolution for Merge Articles](../../Topics\TopicNameNotContainA/Specify-Interactive-Conflict-Resolution-for-Merge-Articles.md) and [Synchronize a Subscription Using Windows Synchronization Manager &#40;Windows Synchronization Manager&#41;](../Topic/Synchronize%20a%20Subscription%20Using%20Windows%20Synchronization%20Manager%20\(Windows%20Synchronization%20Manager\).md).  
  
## See Also  
 [Advanced Merge Replication Conflict Detection and Resolution](../../Topics\TopicNameNotContainA/Advanced-Merge-Replication-Conflict-Detection-and-Resolution.md)  
  
  