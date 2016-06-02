---
title: Install Master Data Services
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bb7aa3e7-8807-42c8-884f-0e41d7a20837
---
# Install Master Data Services
  The following workflow provides an overview of how to install and configure [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)]. [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] installation is a three\-part process:  
  
-   [Pre\-Installation Tasks](#preinstall): Verify system requirements before you install [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)].  
  
-   [Installation Operations](#install): Install [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] by using [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup or the command prompt.  
  
-   [Post\-Installation Tasks](#postinstall): Open [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] to complete post\-installation operations. Create and configure the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database, [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application, and web services, and deploy a sample model.  
  
##  <a name="preinstall"></a> Pre\-Installation Tasks  
  
|Action|Details|Related Topics|  
|------------|-------------|--------------------|  
|Verify installation requirements|The computer where you run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup must meet minimum requirements for:<br /><br /> [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup.<br /><br /> The [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application and web services.<br /><br /> The [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database, if you host the database on the same computer as the web application.<br /><br /> <br /><br /> You can separate the web server computer and database server computer by running Setup on only the web server computer and creating the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database on a remote computer that runs a supported version and edition of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].|[Features Supported by the Editions of SQL Server 2016](../../Topics\TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md)<br /><br /> [Hardware and Software Requirements for Installing SQL Server 2016](../../Topics\TopicNameNotContainA/Hardware-and-Software-Requirements-for-Installing-SQL-Server-2016.md)<br /><br /> [Web Application Requirements &#40;Master Data Services&#41;](../Topic/Web%20Application%20Requirements%20\(Master%20Data%20Services\).md)<br /><br /> [Database Requirements &#40;Master Data Services&#41;](../Topic/Database%20Requirements%20\(Master%20Data%20Services\).md)|  
|Configure the required roles, role services, and features|Before you run Setup, configure the computer with the required Windows roles, role services, and features.<br /><br /> Note: Although you can perform this step later in the workflow, it is helpful to configure this prior to running Setup so that you can perform web configuration tasks immediately following the installation.|[Web Application Requirements &#40;Master Data Services&#41;](../Topic/Web%20Application%20Requirements%20\(Master%20Data%20Services\).md)|  
|Review language support considerations|Determine the language that you want to install and run [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] in.|[Multi-Lingual and Global Deployments &#40;Master Data Services&#41;](../Topic/Multi-Lingual%20and%20Global%20Deployments%20\(Master%20Data%20Services\).md)|  
  
##  <a name="install"></a> Installation Operations  
  
|Action|Details|Related Topics|  
|------------|-------------|--------------------|  
|Run [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup|On the computer that will host the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application and [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] web services, use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup or a command prompt to install [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)]. When you use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup, [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] is available on the **Feature Selection** page under **Shared Features**. When you use a command prompt, [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] is available as a feature parameter. Note that the command\-line setup process installs [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)], but does not configure it. You must configure it using the Master Data Services Configuration Manager.<br /><br /> The installation process:<br /><br /> Installs [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] folders and files at the location you specify for shared features, and assigns permissions to these objects.<br /><br /> Registers [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] assemblies in the Global Assembly Cache \(GAC\).<br /><br /> Installs [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)].|[Install SQL Server 2016 from the Installation Wizard &#40;Setup&#41;](../Topic/Install%20SQL%20Server%202016%20from%20the%20Installation%20Wizard%20\(Setup\).md)<br /><br /> [Folder and File Permissions &#40;Master Data Services&#41;](../Topic/Folder%20and%20File%20Permissions%20\(Master%20Data%20Services\).md)|  
  
##  <a name="postinstall"></a> Post\-Installation Tasks  
  
|Action|Details|Related Topics|  
|------------|-------------|--------------------|  
|Open [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] to complete post\-installation operations|After Setup completes, open [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)]. [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] performs the following post\-installation operations on the local computer:<br /><br /> Creates a Windows group, **MDS\_ServiceAccounts**, to contain [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] service accounts for application pools.<br /><br /> Under the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] installation path, creates the MDSTempDir folder and assigns permissions for **MDS\_ServiceAccounts**. This folder is where temporary compilation files are compiled for the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application.<br /><br /> In the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] Web.config file, configures the **tempDirectory** attribute of the **\<compilation\>** element with the path to the MDSTempDir folder.|[Folder and File Permissions &#40;Master Data Services&#41;](../Topic/Folder%20and%20File%20Permissions%20\(Master%20Data%20Services\).md)<br /><br /> [Web Configuration Reference &#40;Master Data Services&#41;](../Topic/Web%20Configuration%20Reference%20\(Master%20Data%20Services\).md)|  
|Create a [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database|Use [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] to create a [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database for your master data.|[Create a Master Data Services Database](../../Topics\TopicNameContainA/Create-a-Master-Data-Services-Database.md)|  
|Create a [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application|Use [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] to create and configure a web application to host [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)].|[Create a Master Data Manager Web Application &#40;Master Data Services&#41;](../Topic/Create%20a%20Master%20Data%20Manager%20Web%20Application%20\(Master%20Data%20Services\).md)|  
|Associate a [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database with a web application|Use [!INCLUDE[ssMDScfgmgr](../../Token\Other/ssMDScfgmgr_md.md)] to associate your [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] web application with your [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] database.|[Associate a Master Data Services Database and Web Application](../../Topics\TopicNameContainA/Associate-a-Master-Data-Services-Database-and-Web-Application.md)|  
|Configure Internet Explorer Enhanced Security|When you install [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] on a Windows Server 2008 or Windows Server 2008 R2 computer, you might have to configure Internet Explorer Enhanced Security to allow scripting for the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] application site. Otherwise, browsing to the [!INCLUDE[ssMDSmdm](../../Token\Other/ssMDSmdm_md.md)] application site on the server computer will fail.|[Internet Explorer: Enhanced Security Configuration](http://go.microsoft.com/fwlink/p/?LinkId=223869)|  
|Install the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)]|Users who will work with master data can install the [!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)].|[http:\/\/go.microsoft.com\/fwlink\/?LinkId\=219530](http://go.microsoft.com/fwlink/?LinkId=219530)|  
|Enable Data Quality Services \(DQS\) integration|For users of the [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)][!INCLUDE[ssMDSXLS](../../Token\Other/ssMDSXLS_md.md)], enable integration with the DQS feature, which can be used to match similar data.|[Enable Data Quality Services Integration with Master Data Services](../../Topics\TopicNameNotContainA/Enable-Data-Quality-Services-Integration-with-Master-Data-Services.md)|  
|Deploy a sample model|Sample model packages are installed with Master Data Services, and can be deployed using MDSModelDeploy.exe.|[Deploying MDS Samples in SQL Server](http://go.microsoft.com/fwlink/?LinkId=251486&clcid=0x409)|  
  
 If you encounter issues during the installation process or initial configuration, see [Troubleshooting Installation and Configuration Issues](http://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-installation-and-configuration-issues-master-data-services.aspx) on TechNet Wiki.  
  
 If you no longer need [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] on a computer, you can uninstall [!INCLUDE[ssMDSshort](../../Token\Other/ssMDSshort_md.md)] and determine whether to remove items that are not affected by the uninstall process. For more information, see [Uninstall and Remove Master Data Services](../../Topics\TopicNameNotContainA/Uninstall-and-Remove-Master-Data-Services.md).  
  
## See Also  
 [Install SQL Server 2016](../../Topics\TopicNameNotContainA/Install-SQL-Server-2016.md)  
  
  