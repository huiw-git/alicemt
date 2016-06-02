---
title: Uninstall Reporting Services
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5c764a00-d4bc-465d-b32e-e4efce052ce4
---
# Uninstall Reporting Services
  Uninstalling [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] does not remove the content you have created or configuration you have modified. However, if there is content you need after the uninstall is complete, it is recommended you make copies of content before you begin the uninstallation process.  
  
## Uninstall SharePoint Mode  
 When you uninstall [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode, the following are removed:  
  
-   [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service and service proxy.  
  
-   Files used for the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] installation.  
  
 The [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service applications are not removed. If you no longer want the service applications, delete them by using Windows PowerShell or SharePoint Central Administration.  
  
 The report items and related meta data are not removed. This information is contained in the content and configuration databases related to the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service applications. The databases are not removed and you can manually migrate the databases to another installation of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] in SharePoint mode. If you no longer want the information, delete the databases. For more information, see [Upgrade and Migrate Reporting Services](../../Topics\TopicNameNotContainA/Upgrade-and-Migrate-Reporting-Services.md).  
  
 The following are example names of the three [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] databases that are not removed.  
  
-   **Report server database:** ReportingService\_7f616e2d253040e8ab5653b3c09a065e  
  
-   **Report server temp database:** ReportingService\_7f616e2d253040e8ab5653b3c09a065eTempDB  
  
-   **Report server alerting database:** ReportingService\_7f616e2d253040e8ab5653b3c09a065e\_Alerting  
  
### Uninstall the Add\-in for SharePoint Products.  
 When you uninstall the add\-in from a computer, you can choose to only uninstall the files or to also remove the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] feature from the farm. For information on uninstalling the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] add\-in for SharePoint products, see [Install or Uninstall the Reporting Services Add-in for SharePoint](../../Topics\TopicNameNotContainA/Install-or-Uninstall-the-Reporting-Services-Add-in-for-SharePoint.md).  
  
## Uninstall Native Mode  
 When you uninstall [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] native mode, anything that was **created** or **modified** after the installation is left in place. For example database files, log files, [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] configuration files, and content items such as reports and datasource files.  
  
 [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] is an instance feature and therefore is not listed in Windows Control Panel, Programs and Features. To uninstall [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Native mode:  
  
1.  In Windows Control Panel, click **Programs and Features**.  
  
2.  In **Programs and Features** select **Microsoft SQL Server 2012**.  
  
3.  In the uninstall wizard, select the instance that includes the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] instance feature **RS**.  
  
     ![rs_nativemode_uninstall_selectinstance](../../Images\Image\ImageNotContaina/rs_nativemode_uninstall_selectinstance.gif "rs_nativemode_uninstall_selectinstance")  
  
4.  After you select the instance, select the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] feature.  
  
     ![rs_nativemode_uninstall_selectfeatures](../../Images\Image\ImageNotContaina/rs_nativemode_uninstall_selectfeatures.gif "rs_nativemode_uninstall_selectfeatures")  
  
5.  Complete the wizard.  
  
## See Also  
 [Uninstall an Existing Instance of SQL Server &#40;Setup&#41;](../Topic/Uninstall%20an%20Existing%20Instance%20of%20SQL%20Server%20\(Setup\).md)   
 [Install or Uninstall the Power Pivot for SharePoint Add-in &#40;SharePoint 2013&#41;](../Topic/Install%20or%20Uninstall%20the%20Power%20Pivot%20for%20SharePoint%20Add-in%20\(SharePoint%202013\).md)   
 [Install or Uninstall the Reporting Services Add-in for SharePoint](../../Topics\TopicNameNotContainA/Install-or-Uninstall-the-Reporting-Services-Add-in-for-SharePoint.md)  
  
  