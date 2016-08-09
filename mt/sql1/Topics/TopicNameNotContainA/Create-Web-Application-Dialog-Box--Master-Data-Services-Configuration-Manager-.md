---
title: "Create Web Application Dialog Box (Master Data Services Configuration Manager)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e045b41a-4836-47f6-8e78-2b09494b461f
caps.latest.revision: 10
caps.handback.revision: 0
manager: jhubbard
---
# Create Web Application Dialog Box (Master Data Services Configuration Manager)
Use the **Create Web Application** dialog box to create the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] web application. This web application is created in the site that you selected on the **Web Configuration** page.  
  
## Web Application  
 The web server serves the content for this web application from the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] **WebApplication** folder in the file system. This location is specified during Setup, and by default the path is *drive*:\Program Files\Microsoft SQL Server\130\Master Data Services\WebApplication.  
  
|Control Name|Description|  
|------------------|-----------------|  
|Virtual path|Select the virtual path under which you want to create the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] web application. A virtual path is part of the URL that is used to access a web application.<br /><br /> This list is filtered to display only virtual paths of applications under which the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] web application can be created. You cannot create a [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] web application under another [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] web application.|  
|Alias|Type a name for the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] web application or use the default name. This name is used in a URL to access the web application from a web browser.|  
  
## Application Pool  
  
|Control Name|Description|  
|------------------|-----------------|  
|**Name**|Type a unique, friendly name for a new application pool, or use the default name. The [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] web application is added to this application pool.<br /><br /> Application pools provide boundaries that prevent applications in one application pool from affecting applications in another application pool.|  
|**User name**|Type a domain and user name from Active Directory. This account is the identity of the application pool that the web application runs in. This account should be the same account specified as the service account when the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database was created.<br /><br /> This account is added to the mds_exec database role in the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database for database access. For more information, see [Database Logins, Users, and Roles (Master Data Services)](../../Topics/TopicNameNotContainA/Database-Logins--Users--and-Roles--Master-Data-Services-.md). It is also added to a [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] Windows group, **MDS_ServiceAccounts**, which is granted permission to the temporary compilation directory, **MDSTempDir**, in the file system. For more information, see [Folder and File Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Folder-and-File-Permissions--Master-Data-Services-.md).|  
|**Password**|Type the password for the specified user account.|  
|**Confirm password**|Retype the password for the specified user account. The **Password** and **Confirm password** fields must contain the same password.|  
  
## See Also  
 [Web Configuration Page (Master Data Services Configuration Manager)](../../Topics/TopicNameNotContainA/Web-Configuration-Page--Master-Data-Services-Configuration-Manager-.md)   
 [Get Started with Master Data Services (SQL Server 2016)](../../Topics/TopicNameNotContainA/Get-Started-with-Master-Data-Services--SQL-Server-2016-.md)   
 [Web Application Requirements (Master Data Services)](../../Topics/TopicNameNotContainA/Web-Application-Requirements--Master-Data-Services-.md)   
 [Create a Master Data Manager Web Application (Master Data Services)](../../Topics/TopicNameContainA/Create-a-Master-Data-Manager-Web-Application--Master-Data-Services-.md)