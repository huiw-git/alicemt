---
title: "Notifications (Master Data Services)"
ms.custom: na
ms.date: 07/04/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d7ad32d5-9fe5-48fd-8c61-0b00c0aff082
caps.latest.revision: 16
caps.handback.revision: 0
manager: jhubbard
---
# Notifications (Master Data Services)
[!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] can be configured to send an email notification when business rule validation fails, the status of a model version changes, or the status of a changeset changes.  
  
## How Notifications Are Sent  
 You configure notifications in [!INCLUDE[ssMDScfgmgr](../../Topics/TopicNameContainA/tokens/ssMDScfgmgr_md.md)]. Notifications send email messages by using Database Mail on the instance of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssDE](../../Topics/TopicNameContainA/tokens/ssDE_md.md)] that hosts the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database. For more information about Database Mail, see [Database Mail Configuration Objects](../../Topics/TopicNameNotContainA/Database-Mail-Configuration-Objects.md) in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] Books Online.  
  
## When Notifications Are Sent  
 After notifications are configured, automated email notifications can be sent in the following instances.  
  
|Instance|Description|  
|--------------|-----------------|  
|Data fails business rule validation|Individual business rules must be configured to send email when an attribute value fails business rule validation. The notification contains the following information.<br /><br /> Model<br /><br /> Version<br /><br /> Entity<br /><br /> Member Code<br /><br /> Failed business rule<br /><br /> Link to the member for which the attribute value fails the business rule<br /><br /> Notification issued time<br /><br /> For more information, see [Configure Business Rules to Send Notifications (Master Data Services)](../../Topics/TopicNameNotContainA/Configure-Business-Rules-to-Send-Notifications--Master-Data-Services-.md).|  
|Model version status changes|Each time a model version's status changes, users that are model administrators receive notifications automatically. The notification contains the following information.<br /><br /> Model<br /><br /> Version<br /><br /> Prior and new status of the version<br /><br /> Notification issued time<br /><br /> For more information, see [Administrators (Master Data Services)](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).|  
|Changeset status changes|Each time a changeset status changes for an entity that requires approval, entity administrators and/or change set owners receive notifications automatically. The notification contains the following information.<br /><br /> Model<br /><br /> Version<br /><br /> Changeset Name<br /><br /> Prior Status<br /><br /> New Status<br /><br /> Link to apply the changeset in order to view and modify the pending changes.<br /><br /> For more information, see [Changesets (Master Data Services)](../../Topics/TopicNameNotContainA/Changesets--Master-Data-Services-.md)|  
  
## System Settings  
 There are settings in [!INCLUDE[ssMDScfgmgr](../../Topics/TopicNameContainA/tokens/ssMDScfgmgr_md.md)] that affect notifications. You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../../Topics/TopicNameContainA/tokens/ssMDScfgmgr_md.md)] or directly in the System Settings table in the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database. For more information, see [System Settings (Master Data Services)](../../Topics/TopicNameNotContainA/System-Settings--Master-Data-Services-.md).  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Configure [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] to send email notifications.|[Configure Email Notifications (Master Data Services)](../../Topics/TopicNameNotContainA/Configure-Email-Notifications--Master-Data-Services-.md)|  
|Configure [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] to send notifications when attribute values change.|[Configure Business Rules to Send Notifications (Master Data Services)](../../Topics/TopicNameNotContainA/Configure-Business-Rules-to-Send-Notifications--Master-Data-Services-.md)|  
  
## Related Content  
  
-   [Business Rules (Master Data Services)](../../Topics/TopicNameNotContainA/Business-Rules--Master-Data-Services-.md)  
  
-   [Versions (Master Data Services)](../../Topics/TopicNameNotContainA/Versions--Master-Data-Services-.md)  
  
-   [Troubleshooting Email Notifications (Master Data Services)](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)