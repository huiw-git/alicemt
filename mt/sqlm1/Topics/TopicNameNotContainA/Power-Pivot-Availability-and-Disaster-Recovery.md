---
title: Power Pivot Availability and Disaster Recovery
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4aaf008c-3bcb-4dbf-862c-65747d1a668c
---
# Power Pivot Availability and Disaster Recovery
  Availability and disaster recovery plans for [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] depend primarily on the design of your SharePoint farm, the amount of downtime acceptable for different components, and the tools and best practices you implement for SharePoint availability. This topic summarizes technologies and includes example topology diagrams to consider when planning availability and disaster recovery for a [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] deployment.  
  
||  
|-|  
|**[!INCLUDE[applies](../../Token\Other/applies_md.md)]**  SharePoint 2013 &#124; SharePoint 2010|  
  
 **In this topic:**  
  
-   [Example SharePoint 2013 topology for Power Pivot high availability](#bkmk_sharepoint2013)  
  
-   [Example SharePoint 2010 topology for Power Pivot high availability](#bkmk_sharepoint2010)  
  
-   [PowerPivot service application database and SQL Server availability and recovery technologies](#bkmk_sql_server_technologies)  
  
-   [Links to more information](#bkmk_more_resources)  
  
##  <a name="bkmk_sharepoint2013"></a> Example SharePoint 2013 topology for Power Pivot high availability  
 In a [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] 2013 deployment there is more flexibility in how you design [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] availability. In SharePoint 2013, the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance deployed in SharePoint mode, also referred to as the [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] server, runs outside the SharePoint farm and can be installed on separate servers. Each instance of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] in SharePoint mode is registered with Excel Services. The [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] shared service and service application run on SharePoint application servers.  
  
 The following diagram illustrates an example [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] 2013 deployment. This example supports good availability of the [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] services and assumes the databases are backed up on a regular basis.  
  
 ![powerpivot availability in 2013](../../Images\Image\ImageNotContaina/ssas_powerpivot_services_2013.png "ssas_powerpivot_services_2013")  
  
-   **\(1\)** The Web front\-end servers. Use the [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] 2013 Add\-in to install the data providers on each server. For more information, see [Install or Uninstall the Power Pivot for SharePoint Add-in &#40;SharePoint 2013&#41;](../Topic/Install%20or%20Uninstall%20the%20Power%20Pivot%20for%20SharePoint%20Add-in%20\(SharePoint%202013\).md).  
  
-   **\(2\)** The [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] shared service runs **on each** application server and allows the service application to run **across** application servers. Therefore if a single application server goes offline, the [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] application will still be available.  
  
-   **\(3\)** Excel Calculation Services runs one each application server and allows the service application to run across application servers. Therefore if a single application server goes offline, Excel Calculation Services will still be available.  
  
-   **\(4\)** and **\(6\)** Instances of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] ins SharePoint mode run on servers outside the SharePoint farm, this includes the Windows Service **SQL Server Analysis Services \([!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)]\)**. Each of these instances is registered with Excel Services **\(3\)**. Excel Services manages load balancing of requests to the [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] servers. The [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] 2013 architecture enables you to have multiple servers for [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] so you can easily add more instances as needed. For more information, see [Manage Excel Services data model settings \(SharePoint Server 2013\)](http://technet.microsoft.com/library/jj219780\(v=office.15\).aspx).  
  
-   **\(5\)** The SQL Server databases used for content, configuration, and application databases. This includes the [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] service application database. Your DR plan should include the database layer. In this design the databases run on the same server as **\(4\)** one of the [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] instances. **\(4\)** and **\(5\)** could also be on different servers.  
  
-   **\(7\)** Some form of SQL Server database backup or redundancy.  
  
##  <a name="bkmk_sharepoint2010"></a> Example SharePoint 2010 topology for Power Pivot high availability  
 The [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] 2010 architecture requires all [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] components run on the same SharePoint application servers. This includes the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance deployed in SharePoint mode and two shared services compared to only one in a SharePoint 2013 deployment.  
  
 The following diagram illustrates an example [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] 2010 deployment. This example supports good availability of the [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] services and assumes the databases are backed up on a regular basis.  
  
 ![powerpivot availability in sharepoint 2010](../../Images\Image\ImageNotContaina/ssas_powerpivot_services_2010.png "ssas_powerpivot_services_2010")  
  
-   **\(1\)** The Web front\-end servers. Install the data providers on each server. For more information, see [Install the Analysis Services OLE DB Provider on SharePoint Servers](assetId:///2c62daf9-1f2d-4508-a497-af62360ee859).  
  
-   **\(2\)** The two [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] shared services and **\(4\)** the Windows Service **SQL Server Analysis Services \([!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)]\)** are installed on the SharePoint application servers.  
  
     The [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] System Service runs **on each** application server and allows the service application to run **across** application servers. If a single application server goes offline, the [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] service application will still be available.  
  
     To increase [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] capacity in a SharePoint 2010, deploy more SharePoint application servers running the [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] System Service.  
  
-   **\(3\)** Excel Calculation Services runs on each application server and allows the service application to run across application servers. Therefore if a single application server goes offline, Excel Calculation Services will still be available.  
  
-   **\(5\)** The SQL Server databases used for content, configuration, and application databases. This includes the [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] service application database. Your DR plan should include the database layer.  
  
-   **\(6\)** Some form of SQL Server database backup or redundancy.  
  
##  <a name="bkmk_sql_server_technologies"></a> PowerPivot service application database and SQL Server availability and recovery technologies  
 Include the [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] service application database in you SharePoint high availability planning. The default name of the database is `DefaultPowerPivotServiceApplicationDB-<GUID>`. The following is a summary of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] availability technologies and recommendations when used with the [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] database. For more information, see [Supported high availability and disaster recovery options for SharePoint databases \(SharePoint 2013\)](http://technet.microsoft.com/library/jj841106.aspx).  
  
||Comments|  
|-|--------------|  
|[!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] and [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] synchronous mirroring in a farm for availability.|Supported but not recommended. The recommendation is to use Always On in Synchronous – commit mode.|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] in Synchronous\-Commit mode|Supported and recommended.|  
|[!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)] asynchronous mirroring or log\-shipping to another farm for disaster recovery.|Supported.|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)] with asynchronous\-commit for disaster recovery|Supported|  
  
-   [!INCLUDE[ssHADR](../../Token\Other/ssHADR_md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Log Shipping  
  
 For more information on how to plan a cold standby scenario with [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)], see [PowerPivot Disaster Recovery](http://social.technet.microsoft.com/wiki/contents/articles/22137.sharepoint-powerpivot-disaster-recovery.aspx).  
  
## Verification  
 For guidance and scripts to help you verify a [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] deployment before and after a disaster recovery cycle, see [CheckList: Use PowerShell to Verify Power Pivot for SharePoint](../Topic/CheckList:%20Use%20PowerShell%20to%20Verify%20Power%20Pivot%20for%20SharePoint.md).  
  
##  <a name="bkmk_more_resources"></a> Links to more information  
  
-   [Supported high availability and disaster recovery options for SharePoint databases \(SharePoint 2013\)](http://technet.microsoft.com/library/jj841106.aspx)  
  
-   [Plan for disaster recovery \(SharePoint Server 2010\)](http://technet.microsoft.com/library/ff628971\(v=office.14\).aspx)  
  
-   [SQL Server Cloud backup and recovery white paper](http://www.microsoft.com/server-cloud/solutions/cloud-backup-recovery.aspx?WT.srch=1&WT.mc_ID=SEM_BING_USEvergreenSearch_Unassigned&CR_CC=Unassigned#fbid=RjU2Nbzu2dT)  
  
-   [Microsoft® SQL Server Backup to Microsoft Windows® Azure®Tool](http://www.microsoft.com/download/details.aspx?id=40740)  
  
 **Community content**  
  
-   [Managing Service Instances on SharePoint 2013](http://www.petri.co.il/manage-service-instances-sharepoint-2013.htm)  
  
-   [Backup Database SQL Server Script](http://megaupl0ad.net/free/backup%20database%20sql%20server%20script)  
  
  