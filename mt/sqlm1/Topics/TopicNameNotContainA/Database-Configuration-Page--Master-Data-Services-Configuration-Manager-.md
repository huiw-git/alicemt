---
title: Database Configuration Page (Master Data Services Configuration Manager)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dd72220e-a599-465d-8b84-9bb6a7433216
---
# Database Configuration Page (Master Data Services Configuration Manager)
  Use the **Database Configuration** page to edit system settings of a [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. System settings affect all web applications and web services associated with the selected [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. You must select or create a [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database before system settings are enabled and available for configuration.  
  
## Current Database  
 Select an existing [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database or create a new database for which to edit system settings. The new database will be selected after it is created.  
  
|Control Name|Description|  
|------------------|-----------------|  
|**SQL Server instance**|Displays the name of the selected [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance. This is blank until you connect to an instance, and then select or create a [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.|  
|**Master Data Services database**|Displays the name of the selected [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. This is blank until you connect to an instance, and then select or create a [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.|  
|**Master Data Services database version**|The version of the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database schema.|  
|**Create Database**|Opens the **Create Database** wizard from which you connect to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance and create a [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database for that instance.|  
|**Select Database**|Opens the **Connect to Database** dialog box from which you connect to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance and select a [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.|  
|**Upgrade Database**|Opens a wizard from which you can upgrade a specified [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database. This button is enabled only when the specified database requires upgrade.|  
|**Repair Database**|Click this button to ensure the MDS database is installed correctly. This can be useful if you backup and restore an MDS database to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance that has never hosted an MDS database.|  
  
## System Settings  
 Edit system settings for all the web applications and web services associated with the selected [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.  
  
 These settings are available in [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] and are stored in the database in the System Settings table \(mdm.tblSystemSetting\). For a list of all settings, see [System Settings &#40;Master Data Services&#41;](../Topic/System%20Settings%20\(Master%20Data%20Services\).md).  
  
## See Also  
 [Get Started with Master Data Services &#40;SQL Server 2016&#41;](../Topic/Get%20Started%20with%20Master%20Data%20Services%20\(SQL%20Server%202016\).md)   
 [Database Requirements &#40;Master Data Services&#41;](../Topic/Database%20Requirements%20\(Master%20Data%20Services\).md)  
  
  