---
title: Reporting Services Site Settings and Site Features(SharePoint Mode)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e0040fec-e2b7-4099-ae01-3b9bb9128bbd
---
# Reporting Services Site Settings and Site Features(SharePoint Mode)
  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode has several site level custom features and site feature that can be managed from the SharePoint Site Settings page. The settings are site wide and affect all [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] service applications. You must have Content Manager and System Administrator permissions to view this page.  
  
|Site Setting|Description|  
|------------------|-----------------|  
|[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Site Settings|Site wide settings described in this topic.|  
|Manage Data Alerts|Management of the Data Alerting feature.|  
|Report Server File Sync|A Site level feature that is deactivated by default.<br /><br /> Synchronizes Report Server files \(.rdl, .rsds, .smdl, .rsd, .rsc, .rdlx\) from a SharePoint document library to the report server when files are added or updated in the directly within the document library.<br /><br /> For more information, see [Activate the Report Server File Sync Feature in SharePoint Central Administration](../../Topics\TopicNameNotContainA/Activate-the-Report-Server-File-Sync-Feature-in-SharePoint-Central-Administration.md)|  
  
## To open the Reporting Services Site Settings page  
  
1.  From the SharePoint site’s **Site Actions** menu click **Site Settings**.  
  
2.  In the **Reporting Services** section, click **Reporting Services Site Settings**.  
  
## Options for Reporting Services Site Settings  
  
|Option|Description|  
|------------|-----------------|  
|**Enable RSClientPrint ActiveX control download**|The control displays a custom print dialog box that supports features common to other print dialog boxes, including print preview, page selections for specifying specific pages and ranges, page margins, and orientation. For more information on the control, see [Using the RSClientPrint Control in Custom Applications](../Topic/Using%20the%20RSClientPrint%20Control%20in%20Custom%20Applications.md)|  
|**Enable remote errors in local mode**|Show or hide detailed error messages on remote computers when running in local mode. If you see an error message similar to the following, then enabling remote errors may be useful:<br /><br /> `For more information about this error navigate to the report server on the local server machine or enable remote errors`|  
|**Enable accessibility metadata for reports**|Turn on accessibility metadata in the HTML output for reports|  
|**Enable Exact Data Visualization Fit Sizing for Reports**|Configure data visualization fit behavior when inside a tablix, to fix exactly. This includes chart, gauge, and map. When disabled the behavior is for data visualizations to fit approximately, which may leave some white space. This setting only applies to rendering in the report viewer web part. To manage this behavior for server side rendering you need to modify the **rsreportserver.config** file. For more information, see the following:<br /><br /> [RsReportServer.config Configuration File](../../Topics\TopicNameNotContainA/RsReportServer.config-Configuration-File.md).<br /><br /> [Customize Rendering Extension Parameters in RSReportServer.Config](../../Topics\TopicNameNotContainA/Customize-Rendering-Extension-Parameters-in-RSReportServer.Config.md).<br /><br /> [HTML Device Information Settings](../../Topics\TopicNameNotContainA/HTML-Device-Information-Settings.md).<br /><br /> Enabling Exact may have performance impact because the processing to determine the exact size may take longer than an approximate fit.|  
  
## See Also  
 [Manage a Reporting Services SharePoint Service Application](../../Topics\TopicNameContainA/Manage-a-Reporting-Services-SharePoint-Service-Application.md)  
  
  