---
title: Files-Only Installation (Reporting Services)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bdc74a8f-046c-4aa0-bfbd-4f1711dfb9ce
---
# Files-Only Installation (Reporting Services)
  *Files-only installation* refers to a [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] installation where Setup creates the folder structure for [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] program files, copies the files to disk, registers the Report Server service on the local computer, configures the service account, grants files permissions to the service account, and registers the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] WMI provider.  
  
 A files-only installation includes the following [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] features: Report Server service (which hosts the Report Server Web service, background processing application, and Report Manager), Report Builder, the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] Configuration tool, and the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] command line utilities (rsconfig.exe, rskeymgmt.exe and rs.exe). It does not apply to shared features such as [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/includes/ssManStudio_md.md)] or [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/includes/ssBIDevStudioFull_md.md)], which must be specified as separate items if you want to install them.  
  
 In contrast with other installation modes, a report server that is installed in files-only mode is not operational when Setup is finished. Additional configuration will be required to bring the report server online by using the [Reporting Services Configuration Manager &#40;Native Mode&#41;](../../Topics/TopicNameNotContainA/Reporting-Services-Configuration-Manager--Native-Mode-.md).  
  
## When to Select Files-Only Installation Mode  
 A files-only installation must be performed when:  
  
-   You want to connect the report server to a remote report server database.  
  
-   You want to install the report server as a named instance.  
  
-   You have deployment requirements that include using custom settings or functionality, and you want full control over when and how the server is configured.  
  
-   Installing a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] failover cluster that includes [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)].  
  
## How to Perform a Files-Only Installation  
 Files-only installation is the default for [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)].  
  
 You can specify a files-only installation through the command line or in the Installation wizard. The following topics provide step-by-step instructions:  
  
-   [Install SQL Server 2016 from the Installation Wizard &#40;Setup&#41;](../../Topics/TopicNameNotContainA/Install-SQL-Server-2016-from-the-Installation-Wizard--Setup-.md).  
  
-   [Install SQL Server 2016 from the Command Prompt](../../Topics/TopicNameNotContainA/Install-SQL-Server-2016-from-the-Command-Prompt.md).  
  
#### Example Command Line Script  
 For clarity, the example includes /RSINSTALLMODE="FilesOnlyMode". However, because files-only mode is the default, you can omit this and still get a files-only mode installation.  
  
```  
setup /q /ACTION=install /FEATURES=RS /InstanceName=MSSQLSERVER /RSSVCACCOUNT="NT AUTHORITY\NETWORK SERVICE" /RSINSTALLMODE="FilesOnlyMode"  
```  
  
#### Installation Wizard  
 When you select [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] in the Feature Selection page, Setup provides a [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] Configuration page that enables you to specify the installation mode. To specify a files-only installation, select **Install but do not configure the report server** on the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] Configuration page.  
  
## See Also  
 [Verify a Reporting Services Installation](../../Topics/TopicNameContainA/Verify-a-Reporting-Services-Installation.md)   
 [Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../../Topics/TopicNameNotContainA/Configure-the-Report-Server-Service-Account--SSRS-Configuration-Manager-.md)   
 [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](../../Topics/TopicNameNotContainA/Configure-Report-Server-URLs---SSRS-Configuration-Manager-.md)   
 [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../Topics/TopicNameContainA/Configure-a-Report-Server-Database-Connection---SSRS-Configuration-Manager-.md)   
 [Install Reporting Services SharePoint Mode](../../Topics/TopicNameNotContainA/Install-Reporting-Services-SharePoint-Mode.md)   
 [Install Reporting Services Native Mode Report Server](../../Topics/TopicNameNotContainA/Install-Reporting-Services-Native-Mode-Report-Server.md)   
 [Reporting Services Tools](../../Topics/TopicNameNotContainA/Reporting-Services-Tools.md)  
  
  