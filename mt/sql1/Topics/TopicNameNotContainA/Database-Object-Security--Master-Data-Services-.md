---
title: "Database Object Security (Master Data Services)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dd5ba503-7607-45d9-ad0d-909faaade179
caps.latest.revision: 11
caps.handback.revision: 0
manager: jhubbard
---
# Database Object Security (Master Data Services)
In the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database, data is stored in multiple database tables and is visible in views. Information that you might have secured in the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] Web application is visible to users with access to the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database.  
  
 Specifically, employee salary information might be contained in an Employee model, or company financial information might be in an Account model. You can deny a user access to these models in the [!INCLUDE[ssMDSmdm](../../Topics/TopicNameContainA/tokens/ssMDSmdm_md.md)] user interface, but users with access to the database can view this data.  
  
 You can grant permissions to database objects to make specific data available to users. For more information on granting permissions, see [GRANT Object Permissions (Transact-SQL)](assetId:///c001c2e7-d092-43d4-8fa6-693b3ec4c3ea). For more information about securing SQL server, see [Securing SQL Server](../../Topics/TopicNameNotContainA/Securing-SQL-Server.md).  
  
 The following tasks require access to the [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)] database:  
  
-   [Staging Data](#Staging)  
  
-   [Validating Data Against Business Rules](#rules)  
  
-   [Deleting Versions](#Versions)  
  
-   [Immediately Applying Hierarchy Member Permissions](#Hierarchy)  
  
-   [Configuring System Settings](#SysSettings)  
  
##  <a name="Staging"></a> Staging Data  
 In the following table, each securable has “name” as part of the name. This indicates the name of the staging table that is specified when an entity is created. For more information, see [Overview: Importing Data from Tables (Master Data Services)](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md)  
  
|Action|Securables|Permissions|  
|------------|----------------|-----------------|  
|Create, update, and delete leaf members and their attributes.|stg.name_Leaf|Required: INSERT<br /><br /> Optional: SELECT and UPDATE|  
|Load the data from the Leaf staging table into the appropriate MDS database tables.|stg.udp_name_Leaf|EXECUTE|  
|Create, update, and delete consolidated members and their attributes.|stg.name_Consolidated|Required: INSERT<br /><br /> Optional: SELECT and UPDATE|  
|Load the data from the Consolidated staging table into the appropriate MDS database tables.|stg.udp_name_Consolidated|EXECUTE|  
|Move members in an explicit hierarchy.|stg.name_Relationship|Required: INSERT<br /><br /> Optional: SELECT and UPDATE|  
|Load the data from the Relationship staging table into the appropriate MDS tables.|stg.udp_name_Relationship|EXECUTE|  
|View errors that occurred when data from the staging tables was being inserted into the MDS database tables.|stg.udp_name_Relationship|SELECT|  
  
 For more information, see [Overview: Importing Data from Tables (Master Data Services)](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md).  
  
##  <a name="rules"></a> Validating Data Against Business Rules  
  
|Action|Securable|Permissions|  
|------------|---------------|-----------------|  
|Validate a version of data against business rules|mdm.udpValidateModel|EXECUTE|  
  
 For more information, see [Validation Stored Procedure (Master Data Services)](../../Topics/TopicNameNotContainA/Validation-Stored-Procedure--Master-Data-Services-.md).  
  
##  <a name="Versions"></a> Deleting Versions  
  
|Action|Securables|Permissions|  
|------------|----------------|-----------------|  
|Determine the ID of the version you want to delete|mdm.viw_SYSTEM_SCHEMA_VERSION|SELECT|  
|Delete a version of a model|mdm.udpVersionDelete|EXECUTE|  
  
 For more information, see [Delete a Version (Master Data Services)](../../Topics/TopicNameContainA/Delete-a-Version--Master-Data-Services-.md).  
  
##  <a name="Hierarchy"></a> Immediately Applying Hierarchy Member Permissions  
  
|Action|Securables|Permissions|  
|------------|----------------|-----------------|  
|Immediately apply member permissions|mdm.udpSecurityMemberProcessRebuildModel|EXECUTE|  
  
 For more information, see [Immediately Apply Member Permissions (Master Data Services)](../../Topics/TopicNameNotContainA/Immediately-Apply-Member-Permissions--Master-Data-Services-.md).  
  
##  <a name="SysSettings"></a> Configuring System Settings  
 There are system settings that you can configure to control behavior in [!INCLUDE[ssMDSshort](../../Topics/TopicNameContainA/tokens/ssMDSshort_md.md)]. You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../../Topics/TopicNameContainA/tokens/ssMDScfgmgr_md.md)] or if you have UPDATE access, you can adjust these settings directly in the mdm.tblSystemSetting database table. For more information, see [System Settings (Master Data Services)](../../Topics/TopicNameNotContainA/System-Settings--Master-Data-Services-.md).  
  
## See Also  
 [Security (Master Data Services)](../../Topics/TopicNameNotContainA/Security--Master-Data-Services-.md)