---
title: "Database Logins, Users, and Roles (Master Data Services)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 72ee383e-a619-461b-9f9d-1cac162ab0c5
caps.latest.revision: 10
caps.handback.revision: 0
manager: jhubbard
---
# Database Logins, Users, and Roles (Master Data Services)
[!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] includes logins, users, and roles that are automatically installed on the [!INCLUDE[ssDEnoversion](../../Topics/TopicNameContainA/tokens/ssDEnoversion_md.md)] instance that hosts the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database. These logins, users, and roles should not be modified.  
  
## Logins  
  
|Login|Description|  
|-----------|-----------------|  
|**mds_dlp_login**|Allows creation of UNSAFE assemblies. For more information, see [Creating an Assembly](assetId:///a2bc503d-b6b2-4963-8beb-c11c323f18e0).<br /><br /> -Disabled login with randomly-generated password.<br /><br /> -Maps to dbo for the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database.<br /><br /> -For msdb, mds_clr_user maps to this login.|  
|**mds_email_login**|Enabled login used for notifications.<br /><br /> For msdb and the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database, mds_email_user maps to this login.|  
  
## msdb Users  
  
|User|Description|  
|----------|-----------------|  
|**mds_clr_user**|Not used. Maps to mds_dlp_login.|  
|**mds_email_user**|Used for notifications.<br /><br /> -Maps to mds_email_login.<br /><br /> -Is a member of the role: DatabaseMailUserRole.|  
  
## Master Data Services Database Users  
  
|User|Description|  
|----------|-----------------|  
|**mds_email_user**|Used for notifications.<br /><br /> -Has SELECT permission for the mdm schema.<br /><br /> -Has EXECUTE permission for the mdm.MemberGetCriteria user defined table type.<br /><br /> -Has EXECUTE permission for the mdm.udpNotificationQueueActivate stored procedure.|  
|**mds_schema_user**|Owns the mdm and mdq schemas. The default schema is mdm.<br /><br /> Does not have a login mapped to it.|  
|**mds_ssb_user**|Used to execute Service Broker tasks.<br /><br /> -Has DELETE, INSERT, REFERENCES, SELECT, and UPDATE permission all schemas.<br /><br /> -Does not have a login mapped to it.|  
  
## Master Data Services Database Role  
  
|Role|Description|Permissions|  
|----------|-----------------|-----------------|  
|**mds_exec**|This role contains the account you designate in [!INCLUDE[ssMDScfgmgr](../../Topics/TopicNameContainA/tokens/ssMDScfgmgr_md.md)] when you create a [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] web application and designate an account for the application pool.|EXECUTE permission on all schemas.<br /><br /> <br /><br /> ALTER, INSERT, and SELECT permission on these tables:<br /><br /> mdm.tblStgMember<br /><br /> mdm.tblStgMemberAttribute<br /><br /> mdm.tbleStgRelationship<br /><br /> <br /><br /> SELECT permission on these tables:<br /><br /> mdm.tblUser<br /><br /> mdm.tblUserGroup<br /><br /> mdm.tblUserPreference<br /><br /> <br /><br /> SELECT permission on these views:<br /><br /> mdm.viw_SYSTEM_SECURITY_NAVIGATION<br /><br /> mdm.viw_SYSTEM_SECURITY_ROLE_ACCCESSCONTROL<br /><br /> mdm.viw_SYSTEM_SECURITY_ROLE_ACCCESSCONTROL_MEMBER<br /><br /> mdm.viw_SYSTEM_SECURITY_USER_MODEL|  
  
## Schemas  
  
|Role|Description|  
|----------|-----------------|  
|**mdm**|Contains all [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database and Service Broker objects other than the functions contained in the mdq schema.|  
|**mdq**|Contains [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database functions related to filtering member results based on regular expressions or similarity, and for formatting notification emails.|  
|**stg**|Contains [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database tables, stored procedures, and views related to the staging process. Do not delete any of these objects. For more information about the staging process, see [Overview: Importing Data from Tables (Master Data Services)](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md).|  
  
## See Also  
 [Database Object Security (Master Data Services)](../../Topics/TopicNameNotContainA/Database-Object-Security--Master-Data-Services-.md)