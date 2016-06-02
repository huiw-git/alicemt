---
title: Create Web Application Dialog Box (Master Data Services Configuration Manager)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e045b41a-4836-47f6-8e78-2b09494b461f
---
# Create Web Application Dialog Box (Master Data Services Configuration Manager)
  Use the **Create Web Application** dialog box to create the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application. This web application is created in the site that you selected on the **Web Configuration** page.  
  
## Web Application  
 The web server serves the content for this web application from the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] **WebApplication** folder in the file system. This location is specified during Setup, and by default the path is *drive*:\\Program Files\\Microsoft SQL Server\\130\\Master Data Services\\WebApplication.  
  
|Control Name|Description|  
|------------------|-----------------|  
|Virtual path|Select the virtual path under which you want to create the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application. A virtual path is part of the URL that is used to access a web application.<br /><br /> This list is filtered to display only virtual paths of applications under which the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application can be created. You cannot create a [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application under another [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application.|  
|Alias|Type a name for the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application or use the default name. This name is used in a URL to access the web application from a web browser.|  
  
## Application Pool  
  
|Control Name|Description|  
|------------------|-----------------|  
|**Name**|Type a unique, friendly name for a new application pool, or use the default name. The [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application is added to this application pool.<br /><br /> Application pools provide boundaries that prevent applications in one application pool from affecting applications in another application pool.|  
|**User name**|Type a domain and user name from Active Directory. This account is the identity of the application pool that the web application runs in. This account should be the same account specified as the service account when the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database was created.<br /><br /> This account is added to the mds\_exec database role in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database for database access. For more information, see [Database Logins, Users, and Roles &#40;Master Data Services&#41;](../Topic/Database%20Logins,%20Users,%20and%20Roles%20\(Master%20Data%20Services\).md). It is also added to a [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] Windows group, **MDS\_ServiceAccounts**, which is granted permission to the temporary compilation directory, **MDSTempDir**, in the file system. For more information, see [Folder and File Permissions &#40;Master Data Services&#41;](../Topic/Folder%20and%20File%20Permissions%20\(Master%20Data%20Services\).md).|  
|**Password**|Type the password for the specified user account.|  
|**Confirm password**|Retype the password for the specified user account. The **Password** and **Confirm password** fields must contain the same password.|  
  
## See Also  
 [Web Configuration Page &#40;Master Data Services Configuration Manager&#41;](../Topic/Web%20Configuration%20Page%20\(Master%20Data%20Services%20Configuration%20Manager\).md)   
 [Get Started with Master Data Services &#40;SQL Server 2016&#41;](../Topic/Get%20Started%20with%20Master%20Data%20Services%20\(SQL%20Server%202016\).md)   
 [Web Application Requirements &#40;Master Data Services&#41;](../Topic/Web%20Application%20Requirements%20\(Master%20Data%20Services\).md)   
 [Create a Master Data Manager Web Application &#40;Master Data Services&#41;](../Topic/Create%20a%20Master%20Data%20Manager%20Web%20Application%20\(Master%20Data%20Services\).md)  
  
  