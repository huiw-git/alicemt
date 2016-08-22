---
title: "Uninstall sites and hierarchies in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-22
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: d466edd2-97f0-44c1-a73e-d71abbdbf4a8
caps.latest.revision: 6
caps.handback.revision: 0
---
# Uninstall sites and hierarchies in System Center Configuration Manager
Use the following details as a guide when you must uninstall a [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] sites.  
  
 To decommission a hierarchy with multiple sites, the sequence of removal is important:  
  
-   Start by uninstalling the sites  at the bottom of the hierarchy and then move upward.  
  
-   First remove secondary sites attached to primary sites  
  
-   Then remove primary sites  
  
-   After all primary sites are removed, you can uninstall the central administrations site.  
  
 The following subjects are included in this topic:  
  
-   [Remove a secondary site from a hierarchy](#BKMK_RemoveSecondarysite)  
  
-   [Uninstall a primary site](#BKMK_UninstallPrimary)  
  
-   [Uninstall a primary site that is configured with distributed views](#BKMK_UninstallPrimaryDistViews)  
  
-   [Uninstall the central administration site](#BKMK_UninstallCAS)  
  
##  <a name="BKMK_RemoveSecondarysite"></a> Remove a secondary site from a hierarchy  
 You cannot move or reassign secondary sites to a new parent primary site. To remove a secondary site from a hierarchy, it must be deleted from its direct parent site. Use the Delete Secondary Site Wizard from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console to remove the secondary site. When you remove a secondary site, you must choose whether to delete or uninstall the secondary site:  
  
-   **Uninstall the secondary site**: Use this option to remove a functional secondary site that is accessible from the network. This option uninstalls [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] from the secondary site server, and then deletes all information about the site and its resources from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy. If [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installed SQL Server Express as part of the secondary site installation, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] will uninstall SQL Express when it uninstalls the secondary site. If SQL Server Express was installed before you installed the secondary site, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] will not uninstall SQL Server Express.  
  
-   **Delete the secondary site**: Use this option if one of the following is true:  
  
    -   A secondary site failed to install.  
  
    -   The secondary site continues to display in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console after you uninstall it.  
  
     This option deletes all information about the site and its resources from the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy, but leaves [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] installed on the secondary site server.  
  
    > [!NOTE]  
    >  You can also use the Hierarchy Maintenance Tool and the **/DELSITE** option to delete a secondary site. For more information, see [Hierarchy Maintenance Tool (Preinst.exe) for System Center Configuration Manager](../System Center Configuration Manager/Hierarchy-Maintenance-Tool--Preinst.exe--for-System-Center-Configuration-Manager.md).  
  
#### To uninstall or delete a secondary site  
  
1.  Verify the administrative user that runs Setup has the following security rights:  
  
    -   Administrative rights on the secondary site computer.  
  
    -   Local Administrator rights on the remote site database server for the primary site, if it is remote.  
  
    -   Infrastructure Administrator or Full Administrator security role on the parent primary site.  
  
    -   Sysadmin rights on the site database of the secondary site.  
  
2.  In the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console, click **Administration**.  
  
3.  In the **Administration** workspace, expand **Site Configuration**, and then click **Sites**.  
  
4.  Select the secondary site server to remove.  
  
5.  On the **Home** tab, in the **Site** group, click **Delete**.  
  
6.  On the **General** page, select whether to uninstall or delete the secondary site, and then click **Next**.  
  
7.  On the **Summary** page, verify the settings, and then click **Next**.  
  
8.  On the **Completion** page, click **Close** to exit the wizard.  
  
##  <a name="BKMK_UninstallPrimary"></a> Uninstall a primary site  
 You can run [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup to uninstall a primary site that does not have an associated secondary site. Before you uninstall a primary site, consider the following:  
  
-   When [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients are within the boundaries configured at the site, and the primary site is part of a [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy, consider adding the boundaries to a different primary site in the hierarchy before you uninstall the primary site.  
  
-   When the primary site server is no longer available, you must use the Hierarchy Maintenance Tool at the central administration site to delete the primary site from the site database. For more information, see [Hierarchy Maintenance Tool (Preinst.exe) for System Center Configuration Manager](../System Center Configuration Manager/Hierarchy-Maintenance-Tool--Preinst.exe--for-System-Center-Configuration-Manager.md).  
  
 Use the following procedure to uninstall a primary site.  
  
#### To uninstall a primary site  
  
1.  Verify the administrative user that runs Setup has the following security rights:  
  
    -   Local Administrator rights on the central administration site server.  
  
    -   Local Administrator rights on the remote site database server for the central administration site, if it is remote.  
  
    -   Sysadmin rights on the site database of the central administration site.  
  
    -   Local Administrator rights on the primary site computer.  
  
    -   Local Administrator rights on the remote site database server for the primary site, if it is remote.  
  
    -   User name associated with the Infrastructure Administrator or Full Administrator security role on the central administration site.  
  
2.  Start [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup on the primary site server by using one of the following methods:  
  
    -   On **Start**, click **Configuration Manager Setup**.  
  
    -   Open Setup.exe from <*ConfigMgrInstallationMedia*>\SMSSETUP\BIN\X64.  
  
    -   Open Setup.exe from <*ConfigMgrInstallationPath*>\BIN\X64.  
  
3.  On the **Before You Begin** page, click **Next**.  
  
4.  On the **Getting Started** page, select **Uninstall a Configuration Manager site**, and then click **Next**.  
  
5.  On the **Uninstall the Configuration Manager Site**, specify whether to remove the site database from the primary site server and whether to remove the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. By default, Setup removes both items.  
  
    > [!IMPORTANT]  
    >  When a secondary site is attached to the primary site, you must remove the secondary site before you can uninstall the primary site.  
  
6.  Click **Yes** to confirm to uninstall the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] primary site.  
  
##  <a name="BKMK_UninstallPrimaryDistViews"></a> Uninstall a primary site that is configured with distributed views  
 Before you uninstall a child primary site that has distributed views configured on its replication link to the central administration site, you must disable distributed views in your hierarchy. Use the following information to disable distributed views before you uninstall a primary site.  
  
#### To uninstall a primary site that is configured with distributed views  
  
1.  Before you uninstall any primary site, you must disable distributed views on each link in the hierarchy between the central administration site and a primary site.  
  
2.  After you disable distributed views on each link, confirm that the data from the primary site completes reinitialization at the central administration site. You can monitor the initialization of data when you view the link in the **Database Replication** node of the **Monitoring** workspace of the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console.  
  
3.  After the data successfully reinitializes with the central administration site, you can uninstall the primary site. To uninstall a primary site, see the [Uninstall a primary site](#BKMK_UninstallPrimary) section in this topic.  
  
4.  After the primary site is completely uninstalled, you can reconfigure distributed views on links to primary sites.  
  
    > [!IMPORTANT]  
    >  If you uninstall the primary site before you disable distributed views at each site, or before the data from the primary site successfully reinitializes at the central administration site, replication of data between primary sites and the central administration site can fail. In this scenario, you must disable distributed views for each link in your hierarchy, and then, after the data successfully reinitializes with the central administration site, you can reconfigure distributed views.  
  
##  <a name="BKMK_UninstallCAS"></a> Uninstall the central administration site  
 You can run [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup to uninstall a central administration site without child primary sites. Use the following procedure to uninstall the central administration site.  
  
#### To uninstall a central administration site  
  
1.  Verify that the administrative user who runs Setup has the following security rights:  
  
    -   Local Administrator rights on the central administration site server.  
  
    -   Local Administrator rights on the site database server for the central administration site, when the site database server is not installed on the site server.  
  
2.  Start [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] Setup on the central administration site server by using one of the following methods:  
  
    -   On **Start**, click **Configuration Manager Setup**.  
  
    -   Open Setup.exe from <*ConfigMgrInstallationMedia*>\SMSSETUP\BIN\X64.  
  
    -   Open Setup.exe from <*ConfigMgrInstallationPath*>\BIN\X64.  
  
3.  On the **Before You Begin** page, click **Next**.  
  
4.  On the **Getting Started** page, select **Uninstall a Configuration Manager site**, and then click **Next**.  
  
5.  On the **Uninstall the Configuration Manager Site**, specify whether to remove the site database from the central administration site server and whether to remove the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. By default, Setup removes both items.  
  
    > [!IMPORTANT]  
    >  When there is a primary site attached to the central administration site, you must uninstall the primary site before you can uninstall the central administration site.  
  
6.  Click **Yes** to confirm to uninstall the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] central administration site.  
  
## See Also  
[Installing System Center Configuration Manager sites](../System Center Configuration Manager/Installing-System-Center-Configuration-Manager-sites.md)  
 [Site installation technical reference for System Center Configuration Manager](../System Center Configuration Manager/Site-installation-technical-reference-for-System-Center-Configuration-Manager.md)