---
title: "Configuring source hierarchies and source sites for migration to System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: ccce7cb5-e18f-4337-8adf-2018edca3c00
caps.latest.revision: 5
caps.handback.revision: 0
---
# Configuring source hierarchies and source sites for migration to System Center Configuration Manager
To enable migration of data to your [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] environment, you must configure a supported [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] source hierarchy and one or more source sites in that hierarchy that contain data that you want to migrate.  
  
> [!NOTE]  
>  Operations for migration are run at the top-level site in the destination hierarchy. If you configure migration when you use a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console that is connected to a primary child site, you must allow time for the configuration to replicate to the central administration site, to start, and to then replicate status back to the primary site to which you are connected.  
  
 Use the information and procedures in the following sections to specify the source hierarchy and to add additional source sites. After you complete these procedures, you can create migration jobs and start to migrate data from the source hierarchy to the destination hierarchy.  
  
-   [Specify a source hierarchy for migration](#BKBM_ConfigSrcHierarchy)  
  
-   [Identify additional source sites of the source hierarchy](#BKBM_ConfigSrcSites)  
  
##  <a name="BKBM_ConfigSrcHierarchy"></a> Specify a source hierarchy for migration  
 To migrate data to your destination hierarchy, you must specify a supported source hierarchy that contains the data that you want to migrate. By default, the top-level site of that hierarchy becomes a source site of the source hierarchy. If you migrate from a [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] hierarchy, after data is gathered from the initial source site, you can then configure additional source sites for migration. If you migrate from a [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] hierarchy, you do not have to configure additional source sites to migrate data from the source hierarchy. This is because the these versions of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] use a shared database which is available at the top-level site of the source hierarchy. The shared database contains all the information that you can migrate.  
  
 Use the following procedures to specify a source hierarchy for migration and to identify additional source sites in a [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] hierarchy.  
  
 Perform this procedure with a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console that is connected to the destination hierarchy.  
  
#### To configure a source hierarchy  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Migration**, and then click **Source Hierarchy**.  
  
3.  On the **Home** tab, in the **Migration** group, click **Specify Source Hierarchy**.  
  
4.  In the **Specify Source Hierarchy** dialog box, for **Source Hierarchy**, select **New source hierarchy**.  
  
5.  For **Top-level [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site server**, enter the name or IP address of the top-level site of a supported source hierarchy.  
  
6.  Specify source site access accounts that have the following permissions:  
  
    -   Source Site Account: **Read** permission to the SMS Provider for the specified top-level site in the source hierarchy.  
  
    -   Source Site Database Account: **Read** and **Execute** permission to the SQL Server database for the specified top-level site in the source hierarchy.  
  
     If you specify the use of the computer account, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] uses the computer account of the top-level site of the destination hierarchy. For this option ensure that this account is a member of the security group **Distributed COM Users** in the domain where the top-level site of the source hierarchy resides.  
  
7.  To share distribution points between the source and destination hierarchies, select the **Enable distribution point sharing for the source site server** check box. If you do not enable distribution point sharing at this time, you can do so after data gathering completes by editing the credentials of the source site.  
  
8.  Click **OK** to save the configuration. This opens the **Data Gathering Status** dialog box, and data gathering starts automatically.  
  
9. When data gathering finishes, click **Close** to close the **Data Gathering Status** dialog box and complete the configuration.  
  
##  <a name="BKBM_ConfigSrcSites"></a> Identify additional source sites of the source hierarchy  
 When you configure a supported source hierarchy, the top-level site of that hierarchy is automatically configured as a source site, and data is automatically gathered from that site. The next action that you take depends on the version of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] that is run by the source hierarchy:  
  
-   For a [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] source hierarchy, after the data gathering finishes for the initial source site, you can begin migration from only that initial source site, or you can configure additional source sites from the source hierarchy. You would configure additional source sites for a [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] hierarchy to migrate data that is only available from a child site. For example, you might configure additional source sites to gather data about content you want to migrate when that content was created at a child site in the source hierarchy and is not available at the top site of the source hierarchy.  
  
-   For a [!INCLUDE[cm5short](../System Center Configuration Manager/itokens/cm5short_md.md)] or [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] source hierarchy, you do not need to configure additional source sites. This is because these versions of [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] use a shared database which is available at the top-level site of the source hierarchy. The shared database contains all the information that you can migrate from all of the sites in that source hierarchy. This results in the data that you can migrate being available from the top-level site of the source hierarchy.  
  
 When you configure additional source sites for a [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] source hierarchy, you must configure the additional source sites from the top of the source hierarchy to the bottom. You must configure a parent site as a source site before you configure any of its child sites as source sites.  
  
 Use the following procedure to configure additional source sites for [!INCLUDE[cm4short](../System Center Configuration Manager/itokens/cm4short_md.md)] source hierarchies.  
  
#### To identify additional source sites in the source hierarchy  
  
1.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
2.  In the **Administration** workspace, expand **Migration**, and then click **Source Hierarchy**.  
  
3.  Click the site that you want to configure as a source site.  
  
4.  On the **Home** tab, in the **Source Site** group, click **Configure**  
  
5.  In the **Source Site Credentials** dialog box, for the source site access accounts, specify accounts that have the following permissions:  
  
    -   Source Site Account: **Read** permission to the SMS Provider for the specified top-level site in the source hierarchy.  
  
    -   Source Site Database Account: **Read** and **Execute** permission to the SQL Server database for the specified top-level site in the source hierarchy.  
  
     If you specify the use of the computer account, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] uses the computer account of the top-level site of the destination hierarchy. For this option ensure that this account is a member of the security group **Distributed COM Users** in the domain where the top-level site of the source hierarchy resides.  
  
6.  To share distribution points between the source and destination hierarchies, select the **Enable distribution point sharing for the source site server** check box. If you do not enable distribution point sharing at this time, you can do so after data gathering completes by editing the credentials for the source site.  
  
7.  Click **OK** to save the configuration. This opens the **Data Gathering Status** dialog box, and data gathering starts automatically.  
  
8.  When data gathering finishes, click **Close** to complete the configuration.  
  
## See Also  
 [Migrate data between hierarchies in System Center Configuration Manager](../System Center Configuration Manager/Migrate-data-between-hierarchies-in-System-Center-Configuration-Manager.md)