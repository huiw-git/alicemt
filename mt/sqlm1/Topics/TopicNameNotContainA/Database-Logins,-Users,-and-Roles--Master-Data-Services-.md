---
title: Database Logins, Users, and Roles (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 72ee383e-a619-461b-9f9d-1cac162ab0c5
---
# Database Logins, Users, and Roles (Master Data Services)
  [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] includes logins, users, and roles that are automatically installed on the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)] instance that hosts the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. These logins, users, and roles should not be modified.  
  
## Logins  
  
|Login|Description|  
|-----------|-----------------|  
|**mds\_dlp\_login**|Allows creation of UNSAFE assemblies. For more information, see [Creating an Assembly](../Topic/Creating%20an%20Assembly.md).<br /><br /> \-Disabled login with randomly\-generated password.<br /><br /> \-Maps to dbo for the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.<br /><br /> \-For msdb, mds\_clr\_user maps to this login.|  
|**mds\_email\_login**|Enabled login used for notifications.<br /><br /> For msdb and the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database, mds\_email\_user maps to this login.|  
  
## msdb Users  
  
|User|Description|  
|----------|-----------------|  
|**mds\_clr\_user**|Not used. Maps to mds\_dlp\_login.|  
|**mds\_email\_user**|Used for notifications.<br /><br /> \-Maps to mds\_email\_login.<br /><br /> \-Is a member of the role: DatabaseMailUserRole.|  
  
## Master Data Services Database Users  
  
|User|Description|  
|----------|-----------------|  
|**mds\_email\_user**|Used for notifications.<br /><br /> \-Has SELECT permission for the mdm schema.<br /><br /> \-Has EXECUTE permission for the mdm.MemberGetCriteria user defined table type.<br /><br /> \-Has EXECUTE permission for the mdm.udpNotificationQueueActivate stored procedure.|  
|**mds\_schema\_user**|Owns the mdm and mdq schemas. The default schema is mdm.<br /><br /> Does not have a login mapped to it.|  
|**mds\_ssb\_user**|Used to execute Service Broker tasks.<br /><br /> \-Has DELETE, INSERT, REFERENCES, SELECT, and UPDATE permission all schemas.<br /><br /> \-Does not have a login mapped to it.|  
  
## Master Data Services Database Role  
  
|Role|Description|Permissions|  
|----------|-----------------|-----------------|  
|**mds\_exec**|This role contains the account you designate in [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] when you create a [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application and designate an account for the application pool.|EXECUTE permission on all schemas.<br /><br /> <br /><br /> ALTER, INSERT, and SELECT permission on these tables:<br /><br /> mdm.tblStgMember<br /><br /> mdm.tblStgMemberAttribute<br /><br /> mdm.tbleStgRelationship<br /><br /> <br /><br /> SELECT permission on these tables:<br /><br /> mdm.tblUser<br /><br /> mdm.tblUserGroup<br /><br /> mdm.tblUserPreference<br /><br /> <br /><br /> SELECT permission on these views:<br /><br /> mdm.viw\_SYSTEM\_SECURITY\_NAVIGATION<br /><br /> mdm.viw\_SYSTEM\_SECURITY\_ROLE\_ACCCESSCONTROL<br /><br /> mdm.viw\_SYSTEM\_SECURITY\_ROLE\_ACCCESSCONTROL\_MEMBER<br /><br /> mdm.viw\_SYSTEM\_SECURITY\_USER\_MODEL|  
  
## Schemas  
  
|Role|Description|  
|----------|-----------------|  
|**mdm**|Contains all [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database and Service Broker objects other than the functions contained in the mdq schema.|  
|**mdq**|Contains [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database functions related to filtering member results based on regular expressions or similarity, and for formatting notification emails.|  
|**stg**|Contains [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database tables, stored procedures, and views related to the staging process. Do not delete any of these objects. For more information about the staging process, see [Overview: Importing Data from Tables &#40;Master Data Services&#41;](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md).|  
  
## See Also  
 [Database Object Security &#40;Master Data Services&#41;](../Topic/Database%20Object%20Security%20\(Master%20Data%20Services\).md)  
  
  