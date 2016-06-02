---
title: Upgrade Master Data Services
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - master-data-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9c3543f3-3eb9-455d-a9bf-f17e9506ad21
---
# Upgrade Master Data Services
  The following are the scenarios for upgrading to Microsoft [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)].  
  
-   [Upgrade without Database Engine Upgrade](../../Topics\TopicNameNotContainA/Upgrade-Master-Data-Services.md)  
  
-   [Upgrade with Database Engine Upgrade](../../Topics\TopicNameNotContainA/Upgrade-Master-Data-Services.md)  
  
-   [Upgrade in Two-Computer Scenario](../../Topics\TopicNameNotContainA/Upgrade-Master-Data-Services.md)  
  
-   [Upgrade with Restoring a Database from Backup](../../Topics\TopicNameNotContainA/Upgrade-Master-Data-Services.md)  
  
> [!IMPORTANT]  
>  -   Upgrading from the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] CTP1 release to the CTP2 release is not supported.  
> -   Back up your database before performing any upgrade.  
> -   The upgrade process recreates stored procedures and upgrades tables used by [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)]. Any customizations you have made to either of these components may be lost.  
> -   Model deployment packages can be used only in the edition of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] they were created in. You cannot deploy model deployment packages created in [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] to [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)].  
> -   After upgrading Data Quality Services and Master Data Services to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], any earlier version of the Master Data Services Add\-In for Excel will no longer work. You can download the [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] Master Data Services Add\-In for Excel from [Microsoft Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=47343) .  
  
##  <a name="fileLocation"></a> File Location  
  
-   In [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], by default, the files are installed at *drive*:\\Program Files\\Microsoft SQL Server\\130\\Master Data Services.  
  
-   In [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)], by default, the files are installed at *drive*:\\Program Files\\Microsoft SQL Server\\120\\Master Data Services.  
  
-   In [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], by default, the files are installed at *drive*:\\Program Files\\Microsoft SQL Server\\110\\Master Data Services.  
  
-   In [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], by default, the files are installed at *drive*:\\Program Files\\Microsoft SQL Server\\Master Data Services.  
  
##  <a name="noengine"></a> Upgrade without Database Engine Upgrade  
 In this scenario you continue to use [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] to host your MDS database. However, you must upgrade the schema of the MDS database, and then create a [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] web application to access the MDS database. The MDS database can no longer be accessed by the [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] web application.  
  
 You can install [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] and an earlier version of SQL Server \([!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)]\) on the same computer. The files are installed in different locations, as shown in [File Location](#fileLocation).  
  
 **To upgrade without Database Engine upgrade**  
  
1.  Install [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] and any other features you want.  
  
    1.  Open the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Setup wizard.  
  
    2.  In the left pane, click **Installation**.  
  
    3.  In the right pane, click **New SQL Server stand\-alone installation or add features to an existing installation**.  
  
    4.  On the **Feature Selection** page, select **[!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)]** and any other features you want to install.  
  
    5.  Complete the wizard.  
  
2.  Upgrade the MDS database schema.  
  
    1.  Open the [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] version of [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)].  
  
        > [!IMPORTANT]  
        >  To upgrade the MDS database schema, you must be logged in as the Administrator Account that was specified when the MDS database was created. In the MDS database, in mdm.tblUser, this user has the **ID** value of **1**.  
  
    2.  In the left pane, click **Database Configuration**.  
  
    3.  In the right pane, click **Select Database** and specify the information for your [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] database instance.  
  
    4.  Click **Upgrade Database** to start the **Upgrade Database Wizard**. For more information, see [Upgrade Database Wizard &#40;Master Data Services Configuration Manager&#41;](../Topic/Upgrade%20Database%20Wizard%20\(Master%20Data%20Services%20Configuration%20Manager\).md).  
  
3.  Create a web application.  
  
    1.  Open the [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] version of [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)].  
  
    2.  In the left pane, click **Web Configuration**.  
  
    3.  In the right pane, from the **Website** list, select one of the following options:  
  
        -   **Default Web Site**, then click **Create Application**.  
  
        -   **Create new site**. A new web application is automatically created when the website is created.  
  
        > [!IMPORTANT]  
        >  Your existing MDS web application from an earlier version of SQL Server \([!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)]\) is available for selection in the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] version of Master Data Services Configuration Manager. You must not select the existing web application, and instead must create a [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] web application for MDS. Otherwise, you will receive an error when you try to associate the web application with the upgraded MDS database stating that the requested page cannot be accessed because the related configuration data for the page is invalid.  
        >   
        >  If you want to use the same name \(alias\) for MDS web application as your existing \([!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)]\) web application, you must first delete the web application and the associated application pool from IIS, and then create a web application with the same name using [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] version of Master Data Services Configuration Manager. For information about removing web application and application pools from IIS, see [Remove an Application \(IIS\)](http://go.microsoft.com/fwlink/?LinkId=323537) and [Remove an Application Pool \(IIS\)](http://go.microsoft.com/fwlink/?LinkId=323538).  
  
4.  Associate the new web application with the upgraded MDS database.  
  
    1.  In the **Associate Application with Database** section, click **Select**.  
  
    2.  Select the MDS database.  
  
    3.  Click **Apply**.  
  
##  <a name="engine"></a> Upgrade with Database Engine Upgrade  
 In this scenario you will upgrade both the database engine and [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] application from [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] to [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)].  
  
 **To upgrade with Database Engine upgrade**  
  
1.  **For [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] only**: Open **Control Panel** \> **Programs and Features** and uninstall Microsoft [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)][!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)].  
  
2.  Upgrade the database engine to [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)]. For more information, see [Choose a Database Engine Upgrade Method](../../Topics\TopicNameContainA/Choose-a-Database-Engine-Upgrade-Method.md).  
  
3.  Complete all the steps in [Upgrade without Database Engine Upgrade](#noengine) .  
  
##  <a name="twocomputer"></a> Upgrade in Two\-Computer Scenario  
 In this scenario you upgrade a system in which SQL Server is installed on two computers: one with [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)], and the other with [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)].  
  
 If [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] is installed, you continue to use [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] respectively to host your MDS database on one computer. However, you must upgrade the schema of the MDS database, and then use the [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] web application to access the MDS database. The MDS database can no longer be accessed by the [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] web application.  
  
 **To upgrade in two\-computer scenario**  
  
-   Complete all the steps in [Upgrade without Database Engine Upgrade](#noengine).  
  
##  <a name="restore"></a> Upgrade with Restoring a Database from Backup  
 In this scenario, [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] is installed along with [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] on the same computer or two different computers. A  database was backed up on a version earlier than the [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] release, prior to upgrade, and the database has to be restored.  
  
 **To upgrade with restoring a database from backup**  
  
1.  Install [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] and any other features you want.  
  
    1.  Open the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] Setup wizard.  
  
    2.  In the left pane, click **Installation**.  
  
    3.  In the right pane, click **New SQL Server stand\-alone installation or add features to an existing installation**.  
  
    4.  On the **Feature Selection** page, select **[!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)]** and any other features you want to install.  
  
    5.  Complete the wizard.  
  
2.  Restore the database that was backed up.  
  
3.  Upgrade the MDS database schema, create a web application, and associate the new web application with the upgraded MDS database. For the instructions, see steps 2 \- 4 in [Upgrade without Database Engine Upgrade](#noengine)  
  
## Troubleshooting  
 **Issue:** When you open the [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)][!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application, a “client version is not compatible with the database version” error message is displayed.  
  
 **Solution:** This issue occurs when a [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] Master Data Manager web application tries to access a database that has been upgraded to [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] Master Data Services. You must use a [!INCLUDE[ssSQL15](../../Token\Other/ssSQL15_md.md)] web application instead.  
  
 This issue may also occur if you did not stop and restart the **MDS Application Pool** in IIS when upgrading the MDS database schema. Restart the **MDS Application Pool** to correct the issue.  
  
## See Also  
 [Install Master Data Services](../../Topics\TopicNameNotContainA/Install-Master-Data-Services.md)  
  
  