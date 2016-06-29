---
title: Data Source Properties Dialog Box, Credentials (Report Builder)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4531f09f-d653-4c05-a120-d7788838bc99
---
# Data Source Properties Dialog Box, Credentials (Report Builder)
  Select **Credentials** on the **Data Source Properties** dialog box to display and modify credentials to connect to an embedded data source in the report. The credentials that you provide are used to access the data source for previewing reports. For more information about credentials, see [Specify Credentials in Report Builder](../../Topics/TopicNameNotContainA/Specify-Credentials-in-Report-Builder.md).  
  
## Options  
 **Use Windows Authentication (integrated security)**  
 Select this option to use Windows Authentication.  
  
 **Use this user name and password**  
 Select this option to provide a specific user name and password. For embedded data sources: when you publish the report server project to the target server, the user name and password are saved as the stored credentials for the database. If you want to use the user name and password as Windows credentials, you can change the properties for the published shared data source on the target server. For more information, see [Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../../Topics/TopicNameContainA/Create--Delete--or-Modify-a-Shared-Data-Source--Report-Manager-.md) in the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] documentation in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] [Books Online](http://go.microsoft.com/fwlink/?linkid=121312).  
  
 **User name**  
 Type a user name to log on to the data source.  
  
 **Password**  
 Type a password to log on to the data source.  
  
 **Prompt for credentials**  
 Select this option to prompt for credentials when the report runs.  
  
 **Enter prompt string**  
 Type a sentence to instruct the user to provide login credentials for the data source.  
  
 **No credentials**  
 Select this option to provide no credentials for the data source. This option only works if the data source does not accept credentials or if you are passing credentials some other way.  
  
 From some data extensions, the unattended execution account must be configured on the report server.  
  
 For more information, see the topic for the corresponding data source type in [Add Data from External Data Sources &#40;SSRS&#41;](../../Topics/TopicNameNotContainA/Add-Data-from-External-Data-Sources--SSRS-.md) and [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](../../Topics/TopicNameNotContainA/Configure-the-Unattended-Execution-Account--SSRS-Configuration-Manager-.md) in the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] documentation in [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] [Books Online](http://go.microsoft.com/fwlink/?linkid=121312).  
  
## See Also  
 [Report Builder Help for Dialog Boxes, Panes, and Wizards](assetId:///2da24891-0b6d-4d3c-8b18-81b98752642f)   
 [Data Source Properties Dialog Box, General &#40;Report Builder&#41;](../../Topics/TopicNameNotContainA/Data-Source-Properties-Dialog-Box--General--Report-Builder-.md)   
 [Add and Verify a Data Connection &#40;Report Builder and SSRS&#41;](../../Topics/TopicNameContainA/Add-and-Verify-a-Data-Connection--Report-Builder-and-SSRS-.md)   
 [Report Datasets &#40;SSRS&#41;](../../Topics/TopicNameNotContainA/Report-Datasets--SSRS-.md)  
  
  