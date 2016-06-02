---
title: Convert CRI Dialog Box (Report Builder)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a3f2ac6-667e-4498-8b73-9c40beb993f5
---
# Convert CRI Dialog Box (Report Builder)
  This report contains custom report items \(CRIs\) with unsupported features. CRIs are extensions to the Report Definition Language \(RDL\) that support custom objects that display data in a report. CRIs include design\-time and run\-time components that are supplied by third\-party software vendors.  
  
> [!NOTE]  
>  Choosing to support custom report items on a report server is a decision made by the system administrator. To view CRIs in a report, the CRI components must be installed on the report authoring client to preview a report and on the report server to view a published or uploaded report.  
  
 Some CRIs can be converted to report items in the new report definition format. When you open the report, you are prompted whether to upgrade. Use the following information to decide whether to convert the CRIs in this report:  
  
-   **Yes** Choose **Yes** to convert all the CRIs in the report, where possible. Unsupported features in the CRIs cannot be upgraded and are removed from the report definition file. For the list of unsupported features, see [Upgrade Reports](../../Topics\TopicNameNotContainA/Upgrade-Reports.md). When you view the report, you might see differences in the way the CRI displays in the report.  
  
-   **No** Choose **No** when you do not want to convert the CRIs in the report. These CRIs cannot be displayed by the report processor in their current version. If your system administrator is planning to install a new version of the CRI from the third\-party software vendor that is compatible with the new report definition format, you should choose **No**. Until new versions are available, the CRIs display in the report as an empty text box with a red X.  
  
 In either case, the report is upgraded to the new report definition format and a backup copy of the original report is saved as *\<Report Name\>* `-` Backup.rdl. If you save the report in your report authoring tool, you are saving the upgraded report in the new report definition format. If you publish the report, the report is first saved on your computer, and then published to the report server. You are publishing the upgraded version of the report to the report server.  
  
 If you do not save the report, the original report remains unchanged. However, you cannot edit this report in a [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] later version of [!INCLUDE[ssBIDevStudio](../../Token\Other/ssBIDevStudio_md.md)] or a report authoring environment that uses this report definition format. You can continue to run the original version of the report by uploading it to a [!INCLUDE[ssKatmai](../../Token\Other/ssKatmai_md.md)] or later [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] report server by using Report Manager. For more information, see [Upload a File or Report &#40;Report Manager&#41;](../Topic/Upload%20a%20File%20or%20Report%20\(Report%20Manager\).md).  
  
 For reports that you upload instead of publish to a report server, the report processor determines whether the report can be upgraded on first use. Reports that cannot be upgraded are processed in backward\-compatibility mode, and continue to display as they did in the earlier version of [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]. For more information, see [Upgrade Reports](../../Topics\TopicNameNotContainA/Upgrade-Reports.md).  
  
 To identify the current report definition format for a report, for a report server, or for your report authoring environment, see [Find the Report Definition Schema Version &#40;SSRS&#41;](../Topic/Find%20the%20Report%20Definition%20Schema%20Version%20\(SSRS\).md).  
  
## See Also  
 [Report Builder Help for Dialog Boxes, Panes, and Wizards](assetId:///2da24891-0b6d-4d3c-8b18-81b98752642f)  
  
  