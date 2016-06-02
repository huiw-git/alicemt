---
title: Publishing Reports to a Report Server
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bd7aa5e0-61ce-43fd-8f74-5d1aeed078bb
---
# Publishing Reports to a Report Server
  After you have designed and tested a report or set of reports, you can use the built\-in deployment features in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] to publish the reports to a report server. You can publish individual reports or a Report Server project. Publishing a Report Server project is the easiest way to publish multiple reports. [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] uses the term *deploy*, instead ofthe term *publish*. The two terms are interchangeable.  
  
 Before you can publish a report, you must have permission to do so. Permission is determined through role\-based security that is defined by your report server administrator. Publishing operations are typically granted through the Publisher role.  
  
 [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] provides project configurations for managing report publication. The configuration specifies the location of the report server, the version of SQL Server Reporting Services installed on the report server, whether the data sources published to the report server are overwritten and so forth. In addition to using the configurations that [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] provides, you can create additional configurations.  
  
## Project Configurations  
 Reports are built before they are published to ensure that only valid report definitions are published to the report server. Project configurations include properties for building reports, such as the folder in which to temporarily store the built reports, and how to handle build issues. The configurations also have properties that you use to specify the location and version of the report server, the folders on the report server.  
  
 By default, [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] provides three project configurations: DebugLocal, Debug, and Release. The default configuration is DebugLocal. You typically use the DebugLocal configuration to view reports in a local preview window, the Debug configuration to publish reports to a test server, and the Release configuration to publish reports to a production server. The solution configurations drop\-down list on the Standard toolbar shows the active configuration. To use a different configuration, select it from the list.  
  
 Your reporting environment might have multiple report servers and different versions of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] installed. You can create multiple configurations and then use a different one depending the deployment scenario. For more information, see [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](../Topic/Deployment%20and%20Version%20Support%20in%20SQL%20Server%20Data%20Tools%20\(SSRS\).md) and [Set Deployment Properties &#40;Reporting Services&#41;](../Topic/Set%20Deployment%20Properties%20\(Reporting%20Services\).md).  
  
## Publishing Reports  
 You can publish a single report or a Report Server project that contains multiple reports. For instructions about publishing reports, see [Publish Reports](../../Topics\TopicNameNotContainA/Publish-Reports.md).  
  
### Publishing a Single Report  
 If you do not want to publish all reports in a project, you can chose to publish only a single report. To do this, select a configuration that deploys the report \(for example, the Release configuration\), right\-click the report, and then click **Deploy**.  
  
 If a report uses a shared data source, you need to also deploy the shared data source or the deployed report will not run. Right\-click the shared data source and then click **Deploy**.  
  
 The target server URL of the report server must be specified and you might want to change the default folders to which reports and shared data sources deploy.  
  
### Publishing Multiple Reports  
 When you publish a Report Server project, you publish all reports in that project. All reports are deployed using the same project configuration: to the same report server, the same folder on the server, and so on. To publish reports to different servers, either publish them one by one or include only reports you want to in the Report Server project. A solution can include multiple Report Server projects, and using multiple project might make it easier to manage the deployment of reports because you can use a different configuration to deploy different projects.  
  
## See Also  
 [Project Property Pages Dialog Box](../../Topics\TopicNameNotContainA/Project-Property-Pages-Dialog-Box.md)   
 [Report Server Content Management &#40;SSRS Native Mode&#41;](../Topic/Report%20Server%20Content%20Management%20\(SSRS%20Native%20Mode\).md)   
 [Upgrade Reports](../../Topics\TopicNameNotContainA/Upgrade-Reports.md)  
  
  