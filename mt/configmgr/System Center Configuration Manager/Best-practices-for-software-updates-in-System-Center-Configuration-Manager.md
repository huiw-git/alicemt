---
title: "Best practices for software updates in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-sum
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 6d20389a-9de2-4a64-bced-9fc4fa519174
caps.latest.revision: 6
---
# Best practices for software updates in System Center Configuration Manager
This topic includes best practices for software updates in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)]. The information is sorted into best practices for initial installation and best practices for ongoing operations.  
  
## Installation best practices  
 Use the following best practices when you install software updates in [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)].  
  
### Use a Shared WSUS Database for Software Update Points  
 When you install more than one software update point at a primary site, use the same WSUS database for each software update point in the same Active Directory forest. By sharing the same database you can significantly mitigate the client and network performance impact that can occur when clients switch to a new software update point. When a client switches to a new software update point that shares a database with the old software update point, a delta scan still occurs, but this scan is much smaller than it would be if the WSUS server had its own database.  
  
> [!IMPORTANT]  
>  You must also share the local WSUS content folders when you use a shared WSUS database for software update points.  
  
 For more information about software update point switching, see the [Software update point switching](../System Center Configuration Manager/Plan-for-software-updates-in-System-Center-Configuration-Manager.md#BKMK_SUPSwitching) section in the [Plan for software updates in System Center Configuration Manager](../System Center Configuration Manager/Plan-for-software-updates-in-System-Center-Configuration-Manager.md) topic.  
  
### When Configuration Manager and WSUS use the same SQL Server, configure one of these to use a named instance and the other to use the default instance of SQL Server  
 When the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and WSUS databases use the same SQL Server and share the same instance of SQL Server, you cannot easily determine the resource usage between the two applications. When you use a different SQL Server instance for [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] and WSUS, it is easier to troubleshoot and diagnose resource usage issues that might occur for each application.  
  
### Specify the "Store updates locally" setting for the WSUS installation  
 When you install WSUS 3.0, select the **Store updates locally** setting. When this setting is selected, the license terms that are associated with software updates are downloaded during the synchronization process and stored on the local hard drive for the WSUS server. When this setting is not selected, client computers might fail to scan for software updates compliance for software updates that have license terms. When you install the software update point, WSUS Synchronization Manager verifies that this setting is enabled every 60 minutes, by default.  
  
## Operational Best Practices  
 Use the following best practices when you use software updates:  
  
### Limit software updates to 1000 in a single software update deployment  
 You must limit the number of software updates to 1000 for each software update deployment. When you create an automatic deployment rule, verify that the criteria that you specify does not result in more than 1000 software updates. When you manually deploy software updates, do not select more than 1000 updates to deploy.  
  
### Create a new software update group each time an automatic deployment rule runs for “Patch Tuesday” and for general deployment  
 There is a limit of 1000 software updates for a software update deployment. When you create an automatic deployment rule, you specify whether to use an existing update group or create a new update group each time the rule runs. When you specify criteria in an automatic deployment rule that results in multiple software updates and the rule runs on a recurring schedule, specify to create a new software update group each time the rule runs. This will prevent the deployment from surpassing the limit of 1000 software updates per deployment.  
  
### Use an existing software update group for automatic deployment rules for Endpoint Protection definition updates  
 Always use an existing software update group when you use an automatic deployment rule to deploy Endpoint Protection definition updates on a frequent basis. Otherwise, potentially hundreds of software update groups will be created over time. Typically, definition update publishers will set definition updates to expire when they are superseded by four newer updates. Therefore, the software update group that is created by the automatic deployment rule will never contain more than four definition updates for the publisher: one active and three superseded.  
  
## See Also  
 [Plan for software updates in System Center Configuration Manager](../System Center Configuration Manager/Plan-for-software-updates-in-System-Center-Configuration-Manager.md)