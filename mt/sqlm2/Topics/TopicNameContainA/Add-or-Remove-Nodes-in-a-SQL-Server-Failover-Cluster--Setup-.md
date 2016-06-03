---
title: Add or Remove Nodes in a SQL Server Failover Cluster (Setup)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe20dca9-a4c1-4d32-813d-42f1782dfdd3
---
# Add or Remove Nodes in a SQL Server Failover Cluster (Setup)
  Use this procedure to manage nodes to an existing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster instance.  
  
 To update or remove a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster, you must be a local administrator with permission to log in as a service on all nodes of the failover cluster. For local installations, you must run Setup as an administrator. If you install [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] from a remote share, you must use a domain account that has read and execute permissions on the remote share.  
  
 To add a node to an existing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster, you must run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup on the node that is to be added to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster instance. Do not run Setup on the active node.  
  
 To remove a node from an existing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster, you must run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup on the node that is to be removed from the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster instance.  
  
 To view procedural steps to add or remove nodes, select one of the following operations:  
  
-   [Add a node to an existing SQL Server failover cluster](#Add)  
  
-   [Remove a node from an existing SQL Server failover cluster](#Remove)  
  
> [!IMPORTANT]  
>  The operating system drive letter for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] install locations must match on all the nodes added to the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster.  
  
##  <a name="Add"></a> Add Node  
  
#### To add a node to an existing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster  
  
1.  Insert the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation media, and from the root folder, double\-click Setup.exe. To install from a network share, navigate to the root folder on the share, and then double\-click Setup.exe.  
  
2.  The Installation Wizard will launch the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Center. To add a node to an existing failover cluster instance, click **Installation** in the left\-hand pane. Then, select **Add node to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster**.  
  
3.  The System Configuration Checker will run a discovery operation on your computer. To continue, [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)].  
  
4.  On the Language Selection page, you can specify the language for your instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] if you are installing on a localized operating system and the installation media includes language packs for both English and the language corresponding to the operating system. For more information about cross\-language support and installation considerations, see [Local Language Versions in SQL Server](../../Topics\TopicNameNotContainA/Local-Language-Versions-in-SQL-Server.md).  
  
     To continue, click **Next**.  
  
5.  On the Product key page, specify the PID key for a production version of the product. Note that the product key you enter for this installation must be for the same [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] edition as that which is installed on the active node.  
  
6.  On the License Terms page, read the license agreement, and then select the check box to accept the licensing terms and conditions. To help improve [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you can also enable the feature usage option and send reports to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)]. To continue, click **Next**. To end Setup, click **Cancel**.  
  
7.  The System Configuration Checker will verify the system state of your computer before Setup continues. After the check is complete, click **Next** to continue.  
  
8.  On the Cluster Node Configuration page, use the drop\-down box to specify the name of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster instance that will be modified during this Setup operation.  
  
9. On the Server Configuration — Service Accounts page, specify login accounts for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] services. The actual services that are configured on this page depend on the features you selected to install. For failover cluster installations, account name and startup type information will be pre\-populated on this page based on settings provided for the active node. You must provide passwords for each account. For more information, see [Server Configuration - Service Accounts](../../Topics\TopicNameNotContainA/Server-Configuration---Service-Accounts.md) and [Configure Windows Service Accounts and Permissions](../../Topics\TopicNameNotContainA/Configure-Windows-Service-Accounts-and-Permissions.md).  
  
     **Security Note** [!INCLUDE[ssNoteStrongPass](../../Token\Other/ssNoteStrongPass_md.md)]  
  
     When you are finished specifying login information for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] services, click **Next**.  
  
10. On the Reporting page, specify the information you would like to send to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] to improve [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. By default, option for error reporting is enabled.  
  
11. The System Configuration Checker will run one more set of rules to validate your computer configuration with the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] features you have specified.  
  
12. The Ready to Add Node page displays a tree view of installation options that were specified during Setup.  
  
13. Add Node Progress page provides status so you can monitor installation progress as Setup proceeds.  
  
14. After installation, the Complete page provides a link to the summary log file for the installation and other important notes. To complete the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation process, click **Close**.  
  
15. If you are instructed to restart the computer, do so now. It is important to read the message from the Installation Wizard when you are done with Setup. For more information about Setup log files, see [View and Read SQL Server Setup Log Files](../../Topics\TopicNameNotContainA/View-and-Read-SQL-Server-Setup-Log-Files.md).  
  
##  <a name="Remove"></a> Remove Node  
  
#### To remove a node from an existing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster  
  
1.  Insert the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation media. From the root folder, double\-click setup.exe. To install from a network share, navigate to the root folder on the share, and then double\-click Setup.exe.  
  
2.  The Installation Wizard launches the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Center. To remove a node to an existing failover cluster instance, click **Maintenance** in the left\-hand pane, and then select **Remove node from a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster**.  
  
3.  The System Configuration Checker will run a discovery operation on your computer. To continue, [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)].  
  
4.  After you click install on the Setup Support Files page, the System Configuration Checker verifies the system state of your computer before Setup continues. After the check is complete, click **Next** to continue.  
  
5.  On the Cluster Node Configuration page, use the drop\-down box to specify the name of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster instance to be modified during this Setup operation. The node to be removed is listed in the **Name of this node** field.  
  
6.  The Ready to Remove Node page displays a tree view of options that were specified during Setup. To continue, click **Remove**.  
  
7.  During the remove operation, the Remove Node Progress page provides status.  
  
8.  The Complete page provides a link to the summary log file for the remove node operation and other important notes. To complete the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] remove node, click **Close**. For more information about Setup log files, see [View and Read SQL Server Setup Log Files](../../Topics\TopicNameNotContainA/View-and-Read-SQL-Server-Setup-Log-Files.md).  
  
## See Also  
 [View and Read SQL Server Setup Log Files](../../Topics\TopicNameNotContainA/View-and-Read-SQL-Server-Setup-Log-Files.md)  
  
  