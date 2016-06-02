---
title: Quick-Start Installation of SQL Server 2016
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 672afac9-364d-4946-ad5d-8a2d89cf8d81
robots: noindex,nofollow
---
# Quick-Start Installation of SQL Server 2016
    
## Introduction  
 The [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Wizard is based on Windows Installer. It provides a single feature tree for installation of the following [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] components:  
  
-   [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]  
  
-   [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)]  
  
-   [!INCLUDE[ssDQSnoversion](../../Token\Other/ssDQSnoversion_md.md)]  
  
-   Management tools  
  
-   Connectivity components  
  
 You can install each component individually or select a combination of the components listed above. To make the best choice among the editions and components available in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], see [Editions and Components of SQL Server 2016](../../Topics\TopicNameNotContainA/Editions-and-Components-of-SQL-Server-2016.md).  
  
 [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is available in 32\-bit and 64\-bit editions. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup supports the following installation options:  
  
-   **Installation Wizard**  
  
     See [Install SQL Server 2016 from the Installation Wizard &#40;Setup&#41;](../Topic/Install%20SQL%20Server%202016%20from%20the%20Installation%20Wizard%20\(Setup\).md) for procedural information about installing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by using the Installation Wizard.  
  
-   **Command Prompt**  
  
     See [Install SQL Server 2016 from the Command Prompt](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md) for sample syntax and installation parameters for running unattended Setup.  
  
-   **Configuration File**  
  
     See [Install SQL Server 2016 Using a Configuration File](../../Topics\TopicNameContainA/Install-SQL-Server-2016-Using-a-Configuration-File.md) for sample syntax and installation parameters for running Setup through a configuration file.  
  
-   **SysPrep**  
  
     See [Install SQL Server 2016 Using SysPrep](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-Using-SysPrep.md) for procedural information about installing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by using SysPrep.  
  
-   **Server Core Installation**  
  
     See [Install SQL Server 2016 on Server Core](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-on-Server-Core.md) for procedural information about installing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on Windows Server Core.  
  
-   **[!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] BI Feature Installation**  
  
     See [Install SQL Server 2016 Business Intelligence Features](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-Business-Intelligence-Features.md) for information about installing the features that are part of the Microsoft BI platform, that include [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)], [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], and several client applications used for creating or working with analytical data.  
  
-   **Failover Cluster Installation**  
  
     See [SQL Server Failover Cluster Installation](../../Topics\TopicNameNotContainA/SQL-Server-Failover-Cluster-Installation.md) for procedural information about installing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] on a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster.  
  
 By default, sample databases and sample code are not installed as part of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup. To install sample databases and sample code for non\-Express editions of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], see the [CodePlex Web site](http://go.microsoft.com/fwlink/?LinkId=87843). To read about support for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] sample databases and sample code for [!INCLUDE[ssExpress](../../Token\Other/ssExpress_md.md)], see [Databases and Samples Overview](http://go.microsoft.com/fwlink/?LinkId=110391).  
  
## [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation  
 Regardless of whether you use the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Wizard or the command prompt to install [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], setup involves one or more of the following steps:  
  
-   Review installation requirements, system configuration checks, and security considerations for a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation.  For more information, see [Planning a SQL Server Installation](../../Topics\TopicNameNotContainA/Quick-Start-Installation-of-SQL-Server-2016.md).  
  
-   Run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup to upgrade an existing version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. For more information, see [Upgrading to SQL Server 2016](#BKMK_Upgrading).  
  
-   Run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup to install a new instance of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. For more information, see [Installing SQL Server 2016](#BKMK_Install).  
  
-   After you are finished with [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation, the next major step is configuration of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and its components. Use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] utilities to configure [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For more information, see [Configuring SQL Server 2016](#BKMK_Configure).  
  
 You can find detailed explanations of these tasks in the next section.  
  
## Related Tasks  
  
###  <a name="BKMK_BeforeYouInstall"></a> Planning a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation  
 Before you install [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], you must review the hardware and software requirements, network and Internet considerations, and security considerations to install and run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. For more information, see [Planning a SQL Server Installation](../../Topics\TopicNameContainA/Planning-a-SQL-Server-Installation.md) and also the following topics:  
  
|Task Description|Topic|  
|----------------------|-----------|  
|Review the hardware and software requirements, operating system support, network and Internet considerations, and hard disk space requirements.|[Installation Prerequisites](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md)|  
|Review the security considerations for a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] installation.|[Security Considerations](../../Topics\TopicNameContainA/Security-Considerations-for-a-SQL-Server-Installation.md)|  
|Review the details of the features supported by the different editions of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].|[Features and Editions](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md)|  
|Determine the best choice among the editions and components available in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|[Editions and Components of SQL Server 2016](../../Topics\TopicNameNotContainA/Editions-and-Components-of-SQL-Server-2016.md)|  
|Review the hardware configuration, and learn to prepare for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster installation.|[Before Installing Failover Clustering](../../Topics\TopicNameNotContainA/Before-Installing-Failover-Clustering.md)|  
  
###  <a name="BKMK_Upgrading"></a> Upgrading to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]  
 You can upgrade existing instances of [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]. For more information, see [Upgrade to SQL Server 2016](../../Topics\TopicNameNotContainA/Upgrade-to-SQL-Server-2016.md). Before running [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup to upgrade to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)], review the following topics about the upgrade process:  
  
|Description|Topic|  
|-----------------|-----------|  
|Documents supported upgrade paths to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].|[Supported Upgrades](../../Topics\TopicNameNotContainA/Supported-Version-and-Edition-Upgrades.md)|  
|Describes the Distributed Replay Utility, a tool that can use multiple computers to replay trace data, simulating a mission\-critical workload. By performing a replay on a test server before and after a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] upgrade, you can measure performance differences and look for any incompatibilities your application may have with the upgrade.|[Use the Distributed Replay Utility to Prepare for Upgrades](../../Topics\TopicNameNotContainA/Use-the-Distributed-Replay-Utility-to-Prepare-for-Upgrades.md)|  
|Lists the significant changes that might affect your applications after you upgrade to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].|[Backward Compatibility_deleted](../Topic/Backward%20Compatibility_deleted.md)|  
|The procedural topic to upgrade a stand\-alone instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].|[Upgrade to SQL Server 2016 Using the Installation Wizard &#40;Setup&#41;](../Topic/Upgrade%20to%20SQL%20Server%202016%20Using%20the%20Installation%20Wizard%20\(Setup\).md)|  
|The procedural topic to upgrade an edition of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] to another edition. For information about supported edition upgrade paths, see [Supported Version and Edition Upgrades](../../Topics\TopicNameNotContainA/Supported-Version-and-Edition-Upgrades.md).|[Upgrade to a Different Edition of SQL Server 2016 &#40;Setup&#41;](../Topic/Upgrade%20to%20a%20Different%20Edition%20of%20SQL%20Server%202016%20\(Setup\).md)|  
|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] supports upgrade of the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)] and [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] from [!INCLUDE[ssVersion2005](../../Token\Other/ssVersion2005_md.md)], [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)][!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] to [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] failover clusters separately on all failover cluster nodes. Review this topic for more information.|[Upgrade a SQL Server Failover Cluster Instance](../../Topics\TopicNameContainA/Upgrade-a-SQL-Server-Failover-Cluster-Instance.md)|  
  
###  <a name="BKMK_Install"></a> Installing [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]  
 Review the following topics for information about various installation scenarios for [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
|Description|Topic|  
|-----------------|-----------|  
|Provides links to the topics for installing various components of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] and procedural topics for installing [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].|[Install SQL Server 2016](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016.md)|  
|Review this topic to install [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] on Windows Server Core.|[Install SQL Server 2016 on Server Core](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016-on-Server-Core.md)|  
|Review this topic to add individual features to an existing instance of [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].|[Add Features to an Instance of SQL Server 2016 &#40;Setup&#41;](../Topic/Add%20Features%20to%20an%20Instance%20of%20SQL%20Server%202016%20\(Setup\).md)|  
|Review this topic to create a new [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster instance.|[Create a New SQL Server Failover Cluster &#40;Setup&#41;](../Topic/Create%20a%20New%20SQL%20Server%20Failover%20Cluster%20\(Setup\).md)|  
|Use this topic to manage nodes in an existing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover cluster instance.|[Add or Remove Nodes in a SQL Server Failover Cluster &#40;Setup&#41;](../Topic/Add%20or%20Remove%20Nodes%20in%20a%20SQL%20Server%20Failover%20Cluster%20\(Setup\).md)|  
|Use this topic to install [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] client tools on a failover cluster.|[Install Client Tools on a SQL Server Failover Cluster](../../Topics\TopicNameContainA/Install-Client-Tools-on-a-SQL-Server-Failover-Cluster.md)|  
|Review the use of the SQL Discovery report to verify the version of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] features installed on the computer.|[Validate a SQL Server Installation](../../Topics\TopicNameContainA/Validate-a-SQL-Server-Installation.md)|  
|Provides links to procedural topics for installing [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] from the installation wizard, from the command prompt, by using configuration files, and by using SysPrep.|[Installation How-to Topics](../../Topics\TopicNameNotContainA/Installation-How-to-Topics.md)|  
  
## Related Content  
 This section provides information about configuring and uninstalling [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
###  <a name="BKMK_Configure"></a> Configuring [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]  
 After you have installed [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)], you can further configure [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] by using graphical and command\-prompt utilities. See the following topics to configure [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] for the first time:  
  
|Description|Topic|  
|-----------------|-----------|  
|Use the information in this topic to determine whether you need to unblock ports in a firewall to allow access to [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] or [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint. You can follow the steps provided in this topic to configure both port and firewall settings.|[Configure the Windows Firewall to Allow Analysis Services Access](../../Topics\TopicNameNotContainA/Configure-the-Windows-Firewall-to-Allow-Analysis-Services-Access.md)|  
|This topic provides an overview of firewall configuration and summarizes information of interest to a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] administrator.|[Configure the Windows Firewall to Allow SQL Server Access](../../Topics\TopicNameNotContainA/Configure-the-Windows-Firewall-to-Allow-SQL-Server-Access.md)|  
|This topic describes how to configure [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and Windows Firewall with Advanced Security to provide for network connections to an instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] in a multi\-homed environment.|[Configure a Multi-Homed Computer for SQL Server Access](../../Topics\TopicNameContainA/Configure-a-Multi-Homed-Computer-for-SQL-Server-Access.md)|  
  
###  <a name="BKMK_Uninstalling"></a> Uninstalling [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]  
 The following topics describe how to manually uninstall a stand\-alone instance and a failover\-clustered instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]:  
  
|Description|Topic|  
|-----------------|-----------|  
|This topic describes how to manually uninstall a stand\-alone instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|[Uninstall SQL Server 2016](../../Topics\TopicNameNotContainA/Uninstall-SQL-Server-2016.md)|  
|This topic describes how to uninstall a [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] failover\-clustered instance.|[Remove a SQL Server Failover Cluster Instance &#40;Setup&#41;](../Topic/Remove%20a%20SQL%20Server%20Failover%20Cluster%20Instance%20\(Setup\).md)|  
|This topic provides information about manually removing [!INCLUDE[ssDQSnoversion](../../Token\Other/ssDQSnoversion_md.md)] \(DQS\) objects after uninstalling [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] or just DQS server.|[Remove Data Quality Server Objects](../../Topics\TopicNameNotContainA/Remove-Data-Quality-Server-Objects.md)|  
  
## See Also  
 [Product Specifications for SQL Server 2016](../../Topics\TopicNameNotContainA/Product-Specifications-for-SQL-Server-2016.md)   
 [Get Started with Product Documentation for SQL Server](../Topic/Get%20Started%20with%20Product%20Documentation%20for%20SQL%20Server.md)   
 [Backward Compatibility_deleted](../Topic/Backward%20Compatibility_deleted.md)  
  
  