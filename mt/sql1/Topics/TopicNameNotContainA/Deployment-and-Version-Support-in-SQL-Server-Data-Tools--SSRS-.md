---
title: "Deployment and Version Support in SQL Server Data Tools (SSRS)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 36f5686d-7e40-4f31-be81-bd197ca33a02
caps.latest.revision: 20
caps.handback.revision: 0
manager: mblythe
---
# Deployment and Version Support in SQL Server Data Tools (SSRS)
[!INCLUDE[ssBIDevStudio](../../Topics/TopicNameContainA/tokens/ssBIDevStudio_md.md)] supports the following scenarios:  
  
-   Open report definitions (*.rdl) and report server projects (\*.rptproj).  
  
-   Build report definitions.  
  
-   Preview reports in Report Designer.  
  
-   Deploy reports to report servers.  
  
##  <a name="bkmk_ConfigurationandDeploymentProperties"></a> Configuration and Deployment Properties  
 [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)] supports project configurations. A project configuration consists of a set of properties that specify locations and behaviors when a project is built either as a step in previewing or deploying reports. To learn more about project configurations, see the Visual Studio documentation.  
  
 Use project configurations to control the upgrade of report definitions to schema versions compatible with target report servers. The properties controlled by project configurations include the target report server, the folder where the build process temporarily stores report definitions for preview and deployment, and error levels.  
  
 Reports are built before they are rendered as previews in Report Designer or deployed to the report server.  
  
 You set the configuration properties in the [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)] **Project Property** dialog box.  
  
 The build and deployment properties include:  
  
-   **OutputPath** is a build property that identifies the path of folders to store the report definition used in build verification, deployment, and preview of reports.  
  
-   **ErrorLevel** is a build property that identifies the severity of the build issues that are reported as errors. Issues with severity levels less than or equal to the value of **ErrorLevel** are reported as errors; otherwise, the issues are reported as warnings. For more information, see The “Report Validation and Error Levels” section in [Design Reports with Report Designer (SSRS)](../../Topics/TopicNameNotContainA/Design-Reports-with-Report-Designer--SSRS-.md).  
  
-   **TargetServerVersion** is a deployment property that identifies the expected version of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] that is installed on the target report server specified in the **TargetServerURL** property.  
  
 When you specify the earlier version of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] in the **Project Property** dialog box, the reports are not reverted automatically to the earlier version. As such, a Report Server project can contain reports from the two different versions of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)]. When the Report Server project is deployed, all reports in the project are converted to the version specified in **TargetServerVersion**.  
  
 You can add more than one project configuration to a project; each one is used for a different scenario, such as deploying to different versions of report servers. For more information, see [Set Deployment Properties (Reporting Services)](../../Topics/TopicNameNotContainA/Set-Deployment-Properties--Reporting-Services-.md) and [Project Property Pages Dialog Box](../../Topics/TopicNameNotContainA/Project-Property-Pages-Dialog-Box.md).  
  
##  <a name="bkmk_SupportedVersions"></a> Supported Versions  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], the 32-bit development environment for Report Server projects, is not designed to run on [!INCLUDE[vcpritanium](../../Topics/TopicNameContainA/tokens/vcpritanium_md.md)]-based computers and is not installed on [!INCLUDE[vcpritanium](../../Topics/TopicNameContainA/tokens/vcpritanium_md.md)]-based servers. However, support for [!INCLUDE[ssBIDevStudio](../../Topics/TopicNameContainA/tokens/ssBIDevStudio_md.md)] is available for x64-based computers.  
  
 The following table describes the supported versions for authoring and publishing reports in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)].  
  
> [!NOTE]  
>  The schema has not changed since [!INCLUDE[ssKatmai](../../Topics/TopicNameContainA/tokens/ssKatmai_md.md)].  
  
|Project or File type|Version|Author Reports|Publish Reports|Notes|  
|--------------------------|-------------|--------------------|---------------------|-----------|  
|Report Server Project<br /><br /> or<br /><br /> Report Server Wizard Project|[!INCLUDE[ssRSCurrent](../../Topics/TopicNameContainA/tokens/ssRSCurrent_md.md)]|2016 RDL schema|[!INCLUDE[ssRSCurrent](../../Topics/TopicNameContainA/tokens/ssRSCurrent_md.md)]||  
|Report Server Project<br /><br /> or<br /><br /> Report Server Wizard Project|[!INCLUDE[ssSQL14](../../Topics/TopicNameContainA/tokens/ssSQL14_md.md)]|2014 RDL schema|[!INCLUDE[ssSQL14](../../Topics/TopicNameContainA/tokens/ssSQL14_md.md)] [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)]||  
|Report Server Project<br /><br /> or<br /><br /> Report Server Wizard Project|[!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)]|2012 RDL schema|[!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)] [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)]||  
|Report Server Project<br /><br /> or<br /><br /> Report Server Wizard Project|[!INCLUDE[ssKilimanjaro](../../Topics/TopicNameContainA/tokens/ssKilimanjaro_md.md)]|2008 R2 RDL schema|[!INCLUDE[ssKilimanjaro](../../Topics/TopicNameContainA/tokens/ssKilimanjaro_md.md)] [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)]||  
|Report Server Project<br /><br /> or<br /><br /> Report Server Wizard Project|[!INCLUDE[ssKatmai](../../Topics/TopicNameContainA/tokens/ssKatmai_md.md)]|2008 RDL schema|[!INCLUDE[ssKatmai](../../Topics/TopicNameContainA/tokens/ssKatmai_md.md)] [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] report server only|Upgrades 2003 RDL and 2005 RDL to the 2008 RDL schema locally.|  
  
 For more information about opening reports in a previous version of the report definition schema, see [Upgrade Reports](../../Topics/TopicNameNotContainA/Upgrade-Reports.md). For more information about specific report definition schemas, see [Report Definition Language Specification](http://go.microsoft.com/fwlink/?linkid=116865).  
  
## See Also  
 [Publishing Data Sources and Reports](../../Topics/TopicNameNotContainA/Publishing-Data-Sources-and-Reports.md)