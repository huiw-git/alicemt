---
title: Administrators (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d330aa4e-6ade-4b09-b376-1b15d6c78f7d
---
# Administrators (Master Data Services)
  This article describes the types of administrators in [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)]: model administrators, entity administrators, and super user.  
  
## Model Administrators  
 In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], a model administrator is a user who has **Admin** permission assigned to the top\-level model object on the **Model Objects** tab. When a user has Admin permission on a particular model, any other permissions on the model’s child objects \(both model object and member permissions\) are trumped by the model **Admin** permission and effectively ignored.  
  
-   If the user has access to the **Explorer** functional area, the user can add, delete, and update all master data in this area.  
  
-   If the user has access to other functional areas, the user can perform all administrative tasks available in the functional area.  
  
 Each model can have multiple administrators. Each user can be a model administrator for one, several, or all models in the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] deployment.  
  
 A user can be configured as a model administrator either in [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] or programmatically. For more information, see [Create a Model Administrator &#40;Master Data Services&#41;](../Topic/Create%20a%20Model%20Administrator%20\(Master%20Data%20Services\).md).  
  
## Entity Administrators  
 In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], an entity administrator is a user who has administrator permissions assigned to the entity object on the Model Objects tab. When a user has administrator permissions for an entity, any other permissions on the entity’s child objects \(both model object and member permissions\) are superseded by the administrator permissions and are ignored.  
  
-   If the user has access to the **Explorer** functional area, the user can add, delete, and update all master data in this area.  
  
-   If the entity changes require administrator approval, an entity administrator can review and then approve or reject change sets.  
  
 Each entity can have multiple administrators. Each user can be a entity administrator for one, several, or all entities.  
  
 A user can be configured as an entity administrator either in [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] or programmatically. For more information, see [Create an Entity Administrator &#40;Master Data Services&#41;](../Topic/Create%20an%20Entity%20Administrator%20\(Master%20Data%20Services\).md).  
  
## Master Data Services Super User  
 In [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], you can assign a user permissions to the Super User functional area. A user with permissions to the Super User functional area effectively has Admin permission on all models and has permissions for all the other functional areas. For information on the permissions for the functional areas, see [Functional Area Permissions &#40;Master Data Services&#41;](../Topic/Functional%20Area%20Permissions%20\(Master%20Data%20Services\).md).  
  
 The default super user is specified for the **Administrator Account** when you create the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database by using the [Create Database Wizard &#40;Master Data Services Configuration Manager&#41;](../Topic/Create%20Database%20Wizard%20\(Master%20Data%20Services%20Configuration%20Manager\).md).  
  
 The super user can do the following:  
  
-   Access all functional areas.  
  
-   Add, delete, and update all master data for all models in the **Explorer** functional area.  
  
 You can assign Super User permissions to multiple users and\/or user groups.  
  
## Comparing Administrator Types  
  
|Administrator Type|Description|  
|------------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] Super User|Permissions assigned in [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] have no effect on the administrator’s access.<br /><br /> Can be a super user based on functional area permissions assigned explicitly or permissions inherited from a group.<br /><br /> Automatically has all permissions to all models.<br /><br /> Automatically has access to all functional areas.|  
|Model administrator|Can be a model administrator based on admin permissions assigned explicitly or permissions inherited from a group.<br /><br /> Has access only to functional areas that access is granted to.<br /><br /> Automatically has all permissions to all objects and members in the specific model.|  
|Entity administrator|Can be an entity administrator based on administrator permissions assigned explicitly or permissions inherited from a group.<br /><br /> Has access only to functional areas that access is granted to.<br /><br /> Automatically has all permissions to all objects and members in the specific entity.<br /><br /> Can approve the pending change sets if the entity changes require approval.|  
  
## External Resources  
 Blog post, [Security Improvements](http://go.microsoft.com/fwlink/p/?LinkId=615376), on msdn.com.  
  
## See Also  
 [Create a Model Administrator &#40;Master Data Services&#41;](../Topic/Create%20a%20Model%20Administrator%20\(Master%20Data%20Services\).md)   
 [Create a Master Data Services Database](../../Topics\TopicNameContainA/Create-a-Master-Data-Services-Database.md)   
 [Notifications &#40;Master Data Services&#41;](../Topic/Notifications%20\(Master%20Data%20Services\).md)  
  
  