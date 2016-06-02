---
title: Upgrade to a Different Edition of SQL Server 2016 (Setup)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 31d16820-d126-4c57-82cc-27701e4091bc
---
# Upgrade to a Different Edition of SQL Server 2016 (Setup)
  [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup supports edition upgrade among various editions of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. For information about supported edition upgrade paths, see [Supported Version and Edition Upgrades](../../Topics\TopicNameNotContainA/Supported-Version-and-Edition-Upgrades.md). Before you initiate the edition upgrade of an instance of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], review the following topics:  
  
-   [Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md)  
  
-   [Editions and Components of SQL Server 2016](../../Topics\TopicNameNotContainA/Editions-and-Components-of-SQL-Server-2016.md)  
  
-   [Compute Capacity Limits by Edition of SQL Server](../../Topics\TopicNameNotContainA/Compute-Capacity-Limits-by-Edition-of-SQL-Server.md)  
  
-   [Hardware and Software Requirements for Installing SQL Server 2016](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md)  
  
> [!NOTE]  
>  **[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in a clustered environment:** Running edition upgrade on one of the nodes of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] cluster is sufficient. This node can be either active or passive, and the engine does not bring the resources offline during the Edition Upgrade. After the edition upgrade it is required to either restart the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance or failover to a different node.  
  
## Prerequisites  
 For local installations, you must run Setup as an administrator. If you install [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] from a remote share, you must use a domain account that has read permissions on the remote share.  
  
> [!IMPORTANT]  
>  For the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] edition change to be activated, you must restart [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] services. This will result in application down time while services are offline.  
  
## Procedure  
  
#### To upgrade to a different edition of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]  
  
1.  Insert the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation media. From the root folder, double\-click setup.exe or launch the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Center from Configuration Tools. To install from a network share, locate the root folder on the share, and then double\-click Setup.exe.  
  
2.  To upgrade an existing instance of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] to a different edition, from the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Center click **Maintenance**, and then select **Edition Upgrade**.  
  
3.  If Setup support files are required, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup installs them. If you are instructed to restart your computer, restart before you continue.  
  
4.  The System Configuration Checker runs a discovery operation on your computer. To continue, click **OK**.  
  
5.  On the Product Key page, select a radio button to indicate whether you are upgrading to a free edition of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], or whether you have a PID key for a production version of the product. For more information, see [Editions and Components of SQL Server 2016](../../Topics\TopicNameNotContainA/Editions-and-Components-of-SQL-Server-2016.md) and [Supported Version and Edition Upgrades](../../Topics\TopicNameNotContainA/Supported-Version-and-Edition-Upgrades.md).  
  
6.  On the License Terms page, read the license agreement, and then select the check box to accept the licensing terms and conditions. To continue, click **Next**. To end Setup, click **Cancel**.  
  
7.  On the Select Instance page, specify the instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to upgrade.  
  
8.  The Edition Upgrade Rules page validates your computer configuration before the edition upgrade operation begins.  
  
9. The Ready to Upgrade Edition page shows a tree view of installation options that were specified during Setup. To continue, click **Upgrade**.  
  
10. During the edition upgrade process, the services need to be restarted to pick up the new setting. After edition upgrade, the Complete page provides a link to the summary log file for the edition upgrade. To close the wizard, click **Close**.  
  
11. The Complete page provides a link to the summary log file for the installation and other important notes.  
  
12. If you are instructed to restart the computer, do so now. It is important to read the message from the Installation Wizard when you are done with Setup. For information about Setup log files, see [View and Read SQL Server Setup Log Files](../../Topics\TopicNameNotContainA/View-and-Read-SQL-Server-Setup-Log-Files.md).  
  
13. If you upgraded from [!INCLUDE[ssExpress](../../Token\Other/ssExpress_md.md)], you must perform additional steps before you can use your upgraded instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]:  
  
    -   Enable the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service in Windows SCM.  
  
    -   Provision the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent service account by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Configuration Manager.  
  
 In addition to the steps above, you may need to do the following if you upgraded from [!INCLUDE[ssExpress](../../Token\Other/ssExpress_md.md)]:  
  
-   Users that were provisioned in [!INCLUDE[ssExpress](../../Token\Other/ssExpress_md.md)] remain provisioned after the upgrade. Specifically, the BUILTIN\\Users group remains provisioned. Disable, remove, or reprovision these accounts as needed. For more information, see [Configure Windows Service Accounts and Permissions](../../Topics\TopicNameNotContainA/Configure-Windows-Service-Accounts-and-Permissions.md).  
  
-   Sizes and recovery mode for the tempdb and model system databases remain unchanged after the upgrade. Reconfigure these settings as needed. For more information, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](../Topic/Back%20Up%20and%20Restore%20of%20System%20Databases%20\(SQL%20Server\).md).  
  
-   Template databases remain on the computer after the upgrade.  
  
## See Also  
 [Upgrade to SQL Server 2016](../../Topics\TopicNameNotContainA/Upgrade-to-SQL-Server-2016.md)   
 [Backward Compatibility_deleted](../Topic/Backward%20Compatibility_deleted.md)  
  
  