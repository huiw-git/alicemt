---
title: Upgrade Reports
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1a10c67-7462-4562-9b07-a8822188a161
---
# Upgrade Reports
  Report definition \(.rdl\) files are automatically upgraded in the following ways:  
  
-   When you open a report in Report Designer in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], the report definition is upgraded to the currently supported RDL schema. When you specify a [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] report server in the project properties, the report definition is saved in a schema that is compatible with the target server.  
  
-   When you upgrade a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] installation to a [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] installation, existing reports and snapshots that have been published to a report server are compiled and automatically upgraded to the new schema the first time they are processed. If a report cannot be automatically upgraded, the report is processed using the backward\-compatibility mode. The report definition remains in the original schema.  
  
 Reports are not upgraded when you upload a report definition file directly to the report server or SharePoint site. Upgrading a report definition in [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)] is the only way to upgrade the .rdl file.  
  
 After a report is upgraded locally or on the report server, you might notice additional errors, warnings, and messages. This is the result of changes to the internal report object model and processing components, which cause messages to appear when underlying problems in the report are detected. For more information, see [Reporting Services Backward Compatibility](../../Topics\TopicNameNotContainA/Reporting-Services-Backward-Compatibility.md).  
  
 For more information about new features for [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)], see [What's New in Reporting Services &#40;SSRS&#41;](../Topic/What's%20New%20in%20Reporting%20Services%20\(SSRS\).md).  
  
 In this topic:  
  
-   [Versions Supported by Upgrade](#bkmk_versionsupported)  
  
-   [Report Definition (.rdl) Files and Report Designer](#bkmk_rdlfiles)  
  
-   [Published Reports and Report Snapshots](#bkmk_publishedreports_and_snapshots)  
  
-   [Backward-Compatibility Mode](#bkmk_backcompat)  
  
-   [Upgrading a Report with Subreports](#bkmk_subreports)  
  
-   [Upgrading a Report with Custom Report Items](#bkmk_CRIs)  
  
-   [Convert CRI Dialog Box](#bkmk_convertCRIdialog)  
  
##  <a name="bkmk_versionsupported"></a> Versions Supported by Upgrade  
 Reports that were created in any previous version of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] can be upgraded. This includes the following versions:  
  
-   [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)]  
  
-   [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)]  
  
-   [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)]  
  
##  <a name="bkmk_rdlfiles"></a> Report Definition \(.rdl\) Files and Report Designer  
 A report definition file includes a reference to the RDL namespace that specifies the version of the report definition schema that is used to validate the .rdl file.  
  
 When you open an .rdl file in Report Designer in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], if the report was created for a previous namespace, Report Designer automatically creates a backup file and upgrades the report to the current namespace. This is the only way you can upgrade a report definition file.  
  
 Deployment properties that you set can affect which schema the report definition file is saved in. For more information, see [Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;](../Topic/Deployment%20and%20Version%20Support%20in%20SQL%20Server%20Data%20Tools%20\(SSRS\).md).  
  
 You can upload an .rdl file created in an earlier version of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] to a [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] report server and it is automatically upgraded on first use. The report server stores the report definition file in the original format. The report is automatically upgraded the first time it is viewed, but the stored report definition file remains unchanged.  
  
 To identify the current RDL schema for a report, for a report server, or for Report Designer, see [Find the Report Definition Schema Version &#40;SSRS&#41;](../Topic/Find%20the%20Report%20Definition%20Schema%20Version%20\(SSRS\).md).  
  
##  <a name="bkmk_publishedreports_and_snapshots"></a> Published Reports and Report Snapshots  
 On first use, the report server tries to upgrade existing published reports and report snapshots to the new report definition schema, requiring no specific action on your part. When a user views a report or a report snapshot, or when the report server processes a subscription, the upgrading attempt occurs. The report definition is not replaced but continues to be stored on the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] report server in its original schema. If a report cannot be upgraded, the report runs in backward\-compatibility mode.  
  
##  <a name="bkmk_backcompat"></a> Backward\-Compatibility Mode  
 A report that is successfully upgraded is processed by the [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] report processor. A report that cannot be upgraded is processed by the [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report processor in backward\-compatibility mode. A report cannot be processed by both report processors. On first use, a report is either successfully upgraded or marked for backward compatibility.  
  
 Only the [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] report processor supports new features. If a report cannot be upgraded, you can still view the rendered report but new features are not available. To take advantage of the new features, a report must be successfully upgraded.  
  
##  <a name="bkmk_subreports"></a> Upgrading a Report with Subreports  
 When a report contains subreports, one of four possible states can occur during upgrade:  
  
-   The main report and all subreports can be successfully upgraded. They are processed by the [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] report processor.  
  
-   The main report and all subreports cannot be upgraded. They are processed by the [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)][!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report processor.  
  
-   The main report can be upgraded but one or more subreports cannot be upgraded. The main report is processed by the [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] report processor, but the rendered report shows the message "Error: Subreport could not be processed" in the location where the subreport that could not be upgraded would appear.  
  
-   The main report cannot be upgraded but one or more subreports can be upgraded. The main report is processed by the [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] report processor, but the rendered report shows the message "Error: Subreport could not be processed" in the location where the subreport would appear.  
  
 If you see the error "Error: Subreport could not be processed", you must change the definition of the main report or the subreport so that the reports can be processed by the same version of the report processor.  
  
 Drillthrough reports do not have this limitation because they are processed as independent reports.  
  
##  <a name="bkmk_CRIs"></a> Upgrading a Report with Custom Report Items  
 [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)][!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] reports might contain custom report items \(CRIs\) provided by third\-party software vendors and installed by the system administrator on the report authoring computer and the report server. Reports that contain CRIs can be upgraded in the following ways:  
  
-   A [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)][!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report server is upgraded to a [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] report server. Published reports on the report server are automatically upgraded on first use.  
  
-   A [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)][!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report is uploaded to a [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] report server. The report is automatically upgraded on first use.  
  
-   A [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)][!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report is opened in Report Designer in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. A backup copy of the original report is created. One of the following two cases occurs:  
  
    1.  All CRIs in the report have no unsupported features. The CRIs are converted to report items in the new report definition schema, so the entire report is upgraded. If you save the file, it is saved in the current RDL namespace.  
  
    2.  One or more CRIs in the report have unsupported features. A dialog box prompts the user whether to convert the CRIs are leave them unchanged.  
  
     For more information, see [Opening a Report in Report Designer](#OpeningaReport) later in this topic.  
  
 For information about identifying the current RDL namespace for a report server, [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)], or a report, see [Find the Report Definition Schema Version &#40;SSRS&#41;](../Topic/Find%20the%20Report%20Definition%20Schema%20Version%20\(SSRS\).md).  
  
### Upgrading Reports on a Report Server  
 The first time a [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)][!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report runs on a report server that has been upgraded to a [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] report server, the report is automatically upgraded to the current report definition namespace supported by the report server. The report could have existed on the report server before the upgrade, or the report could have been uploaded via Report Manager or published to the report server from Report Designer in [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)] [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)].  
  
 The following table lists the upgrade action that is performed by the report server for specific types of CRIs in a report.  
  
|CRI type|Report Server upgrade action|  
|--------------|----------------------------------|  
|Third\-party CRIs|Upgrade not performed.<br /><br /> Processed by the [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)][!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report processor.|  
  
###  <a name="OpeningaReport"></a> Opening a Report with CRIs in Report Designer  
 When you open a [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)], [!INCLUDE[ssKilimanjaro](../../Token\Other/ssKilimanjaro_md.md)], [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], or [!INCLUDE[ssSQL14](../../Token\Other/ssSQL14_md.md)][!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report with CRIs in Report Designer in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], the report will be upgraded to the new report definition schema. Depending on the CRIs contained in the report, one of the following actions will take place:  
  
-   Third\-party CRIs detected. If the version of the CRI that is installed on the report authoring computer is not compatible with the new RDL schema, the design surface shows a text box with a red X. You must contact your system administrator to install new versions of the CRI from third\-party vendors that are compatible with the new RDL schema.  
  
 Saving a report after it is upgraded in the report authoring environment is the only way to upgrade an existing report to the new report definition schema.  
  
###  <a name="bkmk_convertCRIdialog"></a> Convert CRI Dialog Box  
 This report contains custom report items \(CRIs\) with unsupported features. CRIs are extensions to the Report Definition Language \(RDL\) that support custom objects that display data in a report. CRIs include design\-time and run\-time components that are supplied by third\-party software vendors.  
  
> [!NOTE]  
>  Choosing to support custom report items on a report server is a decision made by the system administrator. To view CRIs in a report, the CRI components must be installed on the report authoring client to preview a report and on the report server to view a published or uploaded report. For more information, see [Custom Report Items](../Topic/Custom%20Report%20Items.md) and documentation from the third\-party software vendor.  
  
 Some CRIs can be converted to report items in the new report definition format. Use the following list to decide whether to convert the CRIs in this report:  
  
-   **Yes** Choose **Yes** to convert all the CRIs in the report, where possible. Unsupported features in the CRIs cannot be upgraded and are removed from the report definition file. When you view the report, you might see differences in the way the CRI displays in the report.  
  
-   **No** Choose **No** when you do not want to convert the CRIs in the report. These CRIs cannot be displayed by the report processor in their current version. If your system administrator is planning to install a new version of the CRI from the third\-party software vendor that is compatible with the new report definition format, you should choose **No**. Until new versions are available, the CRIs display in the report as an empty text box with a red X.  
  
 In either case, the report is upgraded to the new report definition format and a backup copy of the original report is saved as *\<Report Name\>* `-` Backup.rdl. If you save the report in your report authoring tool, you are saving the upgraded report in the new report definition format. If you publish the report, the report is first saved on your computer, and then published to the report server. You are publishing the upgraded version of the report to the report server.  
  
 If you do not save the report, the original report remains unchanged. However, you cannot edit this report in the [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] version of [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)] or a report authoring environment that uses a newer report definition format. You can continue to run the original version of the report by uploading it to a [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] report server by using Report Manager. For more information, see [Upload a File or Report &#40;Report Manager&#41;](../Topic/Upload%20a%20File%20or%20Report%20\(Report%20Manager\).md).  
  
 For reports that you upload instead of publish to a report server, the report processor determines whether the report can be upgraded on first use. Reports that cannot be upgraded are processed in backward\-compatibility mode, and continue to display as they did in the earlier version of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)].  
  
## See Also  
 [Upgrade and Migrate Reporting Services](../../Topics\TopicNameNotContainA/Upgrade-and-Migrate-Reporting-Services.md)   
 [Breaking Changes in SQL Server Reporting Services in SQL Server 2016](../../Topics\TopicNameNotContainA/Breaking-Changes-in-SQL-Server-Reporting-Services-in-SQL-Server-2016.md)   
 [Behavior Changes to SQL Server Reporting Services  in SQL Server 2016](../../Topics\TopicNameNotContainA/Behavior-Changes-to-SQL-Server-Reporting-Services--in-SQL-Server-2016.md)   
 [Discontinued Functionality to SQL Server Reporting Services in SQL Server 2016](../../Topics\TopicNameNotContainA/Discontinued-Functionality-to-SQL-Server-Reporting-Services-in-SQL-Server-2016.md)   
 [Custom Report Items](../Topic/Custom%20Report%20Items.md)   
 [Upgrade a Report Server Database](../../Topics\TopicNameContainA/Upgrade-a-Report-Server-Database.md)  
  
  