---
title: Security (Master Data Services)
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 56bc41ea-de28-4184-aa7e-99111ae55af5
---
# Security (Master Data Services)
  In [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/includes/ssMDSshort_md.md)], use security to ensure that users have access to the specific master data necessary to do their jobs, and to prevent them from accessing data that should not be available to them.  
  
 You can also use security to make someone an administrator of a specific model and functional area (for example, to allow someone to create versions of the Customer model or to give someone the ability to set security permissions).  
  
 [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/includes/ssMDSshort_md.md)] security is based on local or Active Directory domain users and groups. MDS security allows you to use a granular level of detail when determining the data a user can access. Because of the granularity, security can easily become complicated and you should use caution when using overlapping users and groups. For more information, see [Overlapping User and Group Permissions &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Overlapping-User-and-Group-Permissions--Master-Data-Services-.md).  
  
 You can assign security access in the **User and Group Permissions** functional area of the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/includes/ssMDSmdm_md.md)] web application or by using the web service.  
  
## Types of Users  
 There are two types of users in [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/includes/ssMDSshort_md.md)]:  
  
-   Those who access data in the **Explorer** functional area.  
  
-   Those who have the ability to perform administrative tasks in areas other than **Explorer**. These users are called [Administrators &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md).  
  
## How to Set Security  
 To give a user or group permission to access data or functionality in MDS, you must assign:  
  
-   [Functional area access](../../Topics/TopicNameNotContainA/Functional-Area-Permissions--Master-Data-Services-.md), which determines which of the five functional areas of the user interface a user can access.  
  
-   [Model object permissions](../../Topics/TopicNameNotContainA/Model-Object-Permissions--Master-Data-Services-.md), which determine the attributes a user can access, and the type of access (Read, Create, and Update) that the user has to those attributes. The user can also assign Admin permissions at the Model level.  
  
-   Optionally, [hierarchy member permissions](../../Topics/TopicNameNotContainA/Hierarchy-Member-Permissions--Master-Data-Services-.md), which determine the members a user can access, and the type of access (Read, Update, and Delete) the user has to those members.  
  
 When you assign permissions to attributes and members, the permissions intersect and rules determine which permission takes precedence. For more information, see [How Permissions Are Determined &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/How-Permissions-Are-Determined--Master-Data-Services-.md).  
  
## Security in the Add-in for Excel  
 Security set in the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/includes/ssMDSmdm_md.md)] web application is also applied to the [!INCLUDE[ssMDSXLS](../../Topics/TopicNameContainA/includes/ssMDSXLS_md.md)]. Users are only able to view and work with data they have permission to. Administrators can perform administrative tasks.  
  
 The only caveat is that all security assigned in [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/includes/ssMDSmdm_md.md)] does not take effect in Excel until a 20 minute interval passes. The interval is defined by the *MdsMaximumUserInformationCacheInterval* setting in the web.config file. To change the interval, you can change the setting and restart IIS.  
  
## Related Tasks  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Create a user who has full permission to a model.|[Create a Model Administrator &#40;Master Data Services&#41;](../../Topics/TopicNameContainA/Create-a-Model-Administrator--Master-Data-Services-.md)|  
|Add an Active Directory group to [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/includes/ssMDSshort_md.md)]; this is the first step in giving a group permission to access data in the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/includes/ssMDSshort_md.md)] web application.|[Add a Group &#40;Master Data Services&#41;](../../Topics/TopicNameContainA/Add-a-Group--Master-Data-Services-.md)|  
|Assign permission to a functional area of the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/includes/ssMDSshort_md.md)] web application.|[Assign Functional Area Permissions &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Assign-Functional-Area-Permissions--Master-Data-Services-.md)|  
|Assign permission to attribute values by assigning permission to model objects.|[Assign Model Object Permissions &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Assign-Model-Object-Permissions--Master-Data-Services-.md)|  
|Assign permission to member values by assigning permission to hierarchy nodes.|[Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Assign-Hierarchy-Member-Permissions--Master-Data-Services-.md)|  
  
## See Also  
 [Administrators &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Administrators--Master-Data-Services-.md)   
 [Users and Groups &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Users-and-Groups--Master-Data-Services-.md)   
 [Functional Area Permissions &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Functional-Area-Permissions--Master-Data-Services-.md)   
 [Model Object Permissions &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Model-Object-Permissions--Master-Data-Services-.md)   
 [Hierarchy Member Permissions &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/Hierarchy-Member-Permissions--Master-Data-Services-.md)   
 [How Permissions Are Determined &#40;Master Data Services&#41;](../../Topics/TopicNameNotContainA/How-Permissions-Are-Determined--Master-Data-Services-.md)  
  
  