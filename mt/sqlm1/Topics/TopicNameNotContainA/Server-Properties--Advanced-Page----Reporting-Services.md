---
title: Server Properties (Advanced Page) - Reporting Services
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 07b78a84-a6aa-4502-861d-349720ef790e
---
# Server Properties (Advanced Page) - Reporting Services
  Use this page to set system properties on the report server. There are a number of ways to set system properties. This tool provides a graphical user interface so that you can set properties without having to write code.  
  
 To open this page, start [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)], connect to a report server instance, right\-click the report server name, and select **Properties**. Click **Advanced** to open this page.  
  
## Options  
 **EnableMyReports**  
 Indicates whether the My Reports feature is enabled. A value of **true** indicates that the feature is enabled.  
  
 **MyReportsRole**  
 The name of the role used when creating security policies on user's My Reports folders. The default value is **My Reports Role**.  
  
 **EnableClientPrinting**  
 Determines whether the RSClientPrint ActiveX control is available for download from the report server. The valid values are **true** and **false**. The default value is **true**. For more information about additional settings that are required for this control, see [Enable and Disable Client-Side Printing for Reporting Services](../../Topics\TopicNameNotContainA/Enable-and-Disable-Client-Side-Printing-for-Reporting-Services.md).  
  
 **EnableExecutionLogging**  
 Indicates whether report execution logging is enabled. The default value is **true**. For more information about the report server execution log, see [Report Server ExecutionLog and the ExecutionLog3 View](../../Topics\TopicNameNotContainA/Report-Server-ExecutionLog-and-the-ExecutionLog3-View.md).  
  
 **ExecutionLogDaysKept**  
 The number of days to keep report execution information in the execution log. Valid values for this property include **0** through **2**,**147**,**483**,**647**. If the value is **0** entries are not deleted from the Execution Log table. The default value is **60**.  
  
 **SessionTimeout**  
 The length of time, in seconds, that a session remains active. The default value is **600**.  
  
 **SharePointIntegratedMode**  
 This is a read\-only property that indicates the server mode. If this value is False, the report server runs in native mode.  
  
 **SiteName**  
 The name of the report server site displayed in the page title of Report Manager. The default value is [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]. This property can be an empty string. The maximum length is 8,000 characters.  
  
 **StoredParametersLifetime**  
 Specifies the maximum number of days that a stored parameter can be stored. Valid values are **\-1**, **\+1** through **2,147,483,647**. The default value is **180** days.  
  
 **StoredParametersThreshold**  
 Specifies the maximum number of parameter values that that can be stored by the report server. Valid values are **\-1**, **\+1** through **2,147,483,647**. The default value is **1500**.  
  
 **UseSessionCookies**  
 Indicates whether the report server should use session cookies when communicating with client browsers. The default value is **true**.  
  
 **ExternalImagesTimeout**  
 Determines the length of time within which an external image file must be retrieved before the connection is timed out. The default is **600** seconds.  
  
 **SnapshotCompression**  
 Defines how snapshots are compressed. The default value is **SQL**. The valid values are as follows:  
  
 **SQL \=** Snapshots are compressed when stored in the report server database. This is the current behavior.  
  
 **None** \= Snapshots are not compressed.  
  
 **All \=** Snapshots are compressed for all storage options, which include the report server database or the file system.  
  
 **SystemReportTimeout**  
 The default report processing timeout value, in seconds, for all reports managed in the report server namespace. This value can be overridden at the report level. If this property is set, the report server attempts to stop the processing of a report when the specified time has expired. Valid values are **\-1** through **2**,**147**,**483**,**647**. If the value is **\-1**, reports in the namespace do not time out during processing. The default value is **1800**.  
  
 **SystemSnapshotLimit**  
 The maximum number of snapshots that are stored for a report. Valid values are **\-1** through **2**,**147**,**483**,**647**. If the value is **\-1**, there is no snapshot limit.  
  
 **EnableIntegratedSecurity**  
 Determines whether Windows integrated security is supported for report data source connections. The default is **True**. The valid values are as follows:  
  
 **True** \= Windows integrated security is enabled.  
  
 **False** \= Windows integrated security is not enabled. Report data sources that are configured to use Windows integrated security will not run.  
  
 **EnableLoadReportDefinition**  
 Select this option to specify whether users can perform ad hoc report execution from a Report Builder report. Setting this option determines the value of the **EnableLoadReportDefinition** property on the report server.  
  
 If you clear this option, the property will be set to False and report server will not generate clickthrough reports for reports that use a report model as a data source. Any calls to the LoadReportDefinition method will be blocked.  
  
 Turning off this option mitigates a threat whereby a malicious user launches a denial of service attack by overloading the report server with LoadReportDefinition requests.  
  
 **EnableRemoteErrors**  
 Includes external error information \(for example, error information about report data sources\) with the error messages that are returned for users who request reports from remote computers. Valid values are **true** and **false**. The default value is **false**. For more information, see [Enable Remote Errors &#40;Reporting Services&#41;](../Topic/Enable%20Remote%20Errors%20\(Reporting%20Services\).md).  
  
 **EnableReportDesignClientDownload**  
 Specifies whether Report Builder installation package can be downloaded from the report server. If you clear this setting, the URL to Report Builder will not work. For more information, see [Configure Report Builder Access](../../Topics\TopicNameNotContainA/Configure-Report-Builder-Access.md).  
  
 **EditSessionCacheLimit**  
 Specifies the number of data cache entries that can be active in a report edit session. The default number is 5.  
  
 **EditSessionTimeout**  
 Specifies the number of seconds until a report edit session times out. The default value is 7200 seconds \(2 hours\).  
  
 **EnableTestConnectionDetailedErrors**  
 Indicates whether detailed error messages are sent to the client computer when users test data source connections using the report server. The default value is **true**. If the option is set to **false**, only generic error messages are sent.  
  
## See Also  
 [Set Report Server Properties &#40;Management Studio&#41;](../Topic/Set%20Report%20Server%20Properties%20\(Management%20Studio\).md)   
 [Connect to a Report Server in Management Studio](../../Topics\TopicNameContainA/Connect-to-a-Report-Server-in-Management-Studio.md)   
 [Reporting Services Properties](../Topic/Reporting%20Services%20Properties.md)   
 [Report Server in Management Studio F1 Help](../../Topics\TopicNameNotContainA/Report-Server-in-Management-Studio-F1-Help.md)   
 [Report Server System Properties](../Topic/Report%20Server%20System%20Properties.md)   
 [Script Deployment and Administrative Tasks](../../Topics\TopicNameNotContainA/Script-Deployment-and-Administrative-Tasks.md)   
 [Enable and Disable My Reports](../../Topics\TopicNameNotContainA/Enable-and-Disable-My-Reports.md)  
  
  