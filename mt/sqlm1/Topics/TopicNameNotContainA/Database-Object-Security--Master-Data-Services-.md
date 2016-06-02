---
title: Database Object Security (Master Data Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dd5ba503-7607-45d9-ad0d-909faaade179
---
# Database Object Security (Master Data Services)
  In the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database, data is stored in multiple database tables and is visible in views. Information that you might have secured in the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] Web application is visible to users with access to the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.  
  
 Specifically, employee salary information might be contained in an Employee model, or company financial information might be in an Account model. You can deny a user access to these models in the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] user interface, but users with access to the database can view this data.  
  
 You can grant permissions to database objects to make specific data available to users. For more information on granting permissions, see [GRANT Object Permissions &#40;Transact-SQL&#41;](../Topic/GRANT%20Object%20Permissions%20\(Transact-SQL\).md). For more information about securing SQL server, see [Securing SQL Server](../../Topics\TopicNameNotContainA/Securing-SQL-Server.md).  
  
 The following tasks require access to the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database:  
  
-   [Staging Data](#Staging)  
  
-   [Validating Data Against Business Rules](#rules)  
  
-   [Deleting Versions](#Versions)  
  
-   [Immediately Applying Hierarchy Member Permissions](#Hierarchy)  
  
-   [Configuring System Settings](#SysSettings)  
  
##  <a name="Staging"></a> Staging Data  
 In the following table, each securable has “name” as part of the name. This indicates the name of the staging table that is specified when an entity is created. For more information, see [Overview: Importing Data from Tables &#40;Master Data Services&#41;](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md)  
  
|Action|Securables|Permissions|  
|------------|----------------|-----------------|  
|Create, update, and delete leaf members and their attributes.|stg.name\_Leaf|Required: INSERT<br /><br /> Optional: SELECT and UPDATE|  
|Load the data from the Leaf staging table into the appropriate MDS database tables.|stg.udp\_name\_Leaf|EXECUTE|  
|Create, update, and delete consolidated members and their attributes.|stg.name\_Consolidated|Required: INSERT<br /><br /> Optional: SELECT and UPDATE|  
|Load the data from the Consolidated staging table into the appropriate MDS database tables.|stg.udp\_name\_Consolidated|EXECUTE|  
|Move members in an explicit hierarchy.|stg.name\_Relationship|Required: INSERT<br /><br /> Optional: SELECT and UPDATE|  
|Load the data from the Relationship staging table into the appropriate MDS tables.|stg.udp\_name\_Relationship|EXECUTE|  
|View errors that occurred when data from the staging tables was being inserted into the MDS database tables.|stg.udp\_name\_Relationship|SELECT|  
  
 For more information, see [Overview: Importing Data from Tables &#40;Master Data Services&#41;](../Topic/Overview:%20Importing%20Data%20from%20Tables%20\(Master%20Data%20Services\).md).  
  
##  <a name="rules"></a> Validating Data Against Business Rules  
  
|Action|Securable|Permissions|  
|------------|---------------|-----------------|  
|Validate a version of data against business rules|mdm.udpValidateModel|EXECUTE|  
  
 For more information, see [Validation Stored Procedure &#40;Master Data Services&#41;](../Topic/Validation%20Stored%20Procedure%20\(Master%20Data%20Services\).md).  
  
##  <a name="Versions"></a> Deleting Versions  
  
|Action|Securables|Permissions|  
|------------|----------------|-----------------|  
|Determine the ID of the version you want to delete|mdm.viw\_SYSTEM\_SCHEMA\_VERSION|SELECT|  
|Delete a version of a model|mdm.udpVersionDelete|EXECUTE|  
  
 For more information, see [Delete a Version &#40;Master Data Services&#41;](../Topic/Delete%20a%20Version%20\(Master%20Data%20Services\).md).  
  
##  <a name="Hierarchy"></a> Immediately Applying Hierarchy Member Permissions  
  
|Action|Securables|Permissions|  
|------------|----------------|-----------------|  
|Immediately apply member permissions|mdm.udpSecurityMemberProcessRebuildModel|EXECUTE|  
  
 For more information, see [Immediately Apply Member Permissions &#40;Master Data Services&#41;](../Topic/Immediately%20Apply%20Member%20Permissions%20\(Master%20Data%20Services\).md).  
  
##  <a name="SysSettings"></a> Configuring System Settings  
 There are system settings that you can configure to control behavior in [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)]. You can adjust these settings in [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] or if you have UPDATE access, you can adjust these settings directly in the mdm.tblSystemSetting database table. For more information, see [System Settings &#40;Master Data Services&#41;](../Topic/System%20Settings%20\(Master%20Data%20Services\).md).  
  
## See Also  
 [Security &#40;Master Data Services&#41;](../Topic/Security%20\(Master%20Data%20Services\).md)  
  
  