---
title: What&#39;s New in Reporting Services (SSRS)
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc909063-6b84-4b3a-80d2-e93fc04b4b9d
---
# What&#39;s New in Reporting Services (SSRS)
  This topic summarizes the changes and updates in the [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/includes/ssCurrent_md.md)] release of [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)]. For information on what's new in other areas of [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/includes/ssSQL15_md.md)], see [What's New in SQL Server 2016](assetId:///6a428023-e3cc-4626-a88a-4c13ccbd7db0).  
  
 **Download** ![download](../../Topics/TopicNameNotContainA/media/download.png "download")  
  
-   To download [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/includes/ssSQL15_md.md)], go to  **[Evaluation Center](https://www.microsoft.com/en-us/evalcenter/evaluate-sql-server-2016)**.  
  
-   Have an Azure account?  Then go **[Here](https://azure.microsoft.com/en-us/marketplace/partners/microsoft/sqlserver2016rtmenterprisewindowsserver2012r2/?wt.mc_id=sqL16_vm)** to spin up a Virtual Machine with [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/includes/ssCurrent_md.md)] already installed.  
  
 ![note](../../Topics/TopicNameNotContainA/media/ssrs_fyi_note.png "ssrs_fyi_note") For the current release notes, see [SQL Server 2016 Release Notes](../../Topics/TopicNameNotContainA/SQL-Server-2016-Release-Notes.md).  
  
## Reporting Services [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Topics/TopicNameNotContainA/includes/ssRSWebPortal-Non-Markdown_md.md)]  
 A new [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Topics/TopicNameNotContainA/includes/ssRSWebPortal-Non-Markdown_md.md)] is available. This is an updated, modern, portal which incorporates KPIs, Mobile Reports, Paginated Reports, Excel and Power BI Desktop files. The [!INCLUDE[ssRSWebPortal](../../Topics/TopicNameContainA/includes/ssRSWebPortal.md)] replaces Report Manager from previous releases. You can also download Mobile Report Publisher and Report Builder from the [!INCLUDE[ssRSWebPortal](../../Topics/TopicNameContainA/includes/ssRSWebPortal.md)] without the need of ClickOnce technology.
 
 To create Mobile Reports, you will need the [!INCLUDE[SS_MobileReptPub_Short](../../Topics/TopicNameNotContainA/includes/SS_MobileReptPub_Short_md.md)].  
  
 For more information about the [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Topics/TopicNameNotContainA/includes/ssRSWebPortal-Non-Markdown_md.md)], see [Web portal &#40;SSRS Native Mode&#41;](../../Topics/TopicNameNotContainA/Web-portal--SSRS-Native-Mode-.md).  
  
 ![ssRSPortal](../../Topics/TopicNameNotContainA/media/ssRSPortal.png "ssRSPortal")  
 
 ### Custom branding for the web portal
  You can customize the [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Topics/TopicNameNotContainA/includes/ssRSWebPortal-Non-Markdown_md.md)] with your organization's logo and colors by using a branding pack.  
  
  For more information custom branding, see [Branding the web portal](../../Topics/TopicNameNotContainA/Branding-the-web-portal.md)
 
 ### Key performance indicators (KPI) in the web portal

You can create KPIs direct in the web portal that are contextual to the folder you are in. When creating KPIs, you can choose dataset fields and summarize those values. You can also select related content to drill-through to more details.
  
 ![ssrs-webportal-kpi](../../Topics/TopicNameNotContainA/media/ssrs-webportal-kpi.png)
 
 For more information, see [Working with KPIs in the web portal](assetId:///a28cf500-6d47-4268-a248-04837e7a09eb)
  
 
 ## Mobile Reports
 
Reporting Services mobile reports are dedicated reports optimized for a wide variety of form factors and provide an optimal experience for users accessing reports on mobile devices. Mobile reports feature a assortment of visualizations, from time, category, and comparison charts, to treemaps and custom maps. Connect your mobile reports to a range of data sources, including on-premises SQL Server Analysis Services multidimensional and tabular data. Lay out your mobile reports on a design surface with adjusting grid rows and columns, and flexible mobile report elements that scale well to any screen size. Then save these mobile reports to a Reporting Service server, and view and interact with them in a browser or in the Power BI mobile app on iPads, iPhones, Android phones and Windows 10 devices.
  
### Mobile Report Publisher  
 The [!INCLUDE[SS_MobileReptPub_Long](../../Topics/TopicNameContainA/includes/SS_MobileReptPub_Long_md.md)]allows you to create and publish SQL Server mobile reports to your [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] [!INCLUDE[ssRSWebPortal-Non-Markdown](../../Topics/TopicNameNotContainA/includes/ssRSWebPortal-Non-Markdown_md.md)].  
  
 ![SS_MRP_LayoutTabSmall](../../Topics/TopicNameNotContainA/media/SS_MRP_LayoutTabSm.png "SS_MRP_LayoutTabSm")  
  
 For more information, see [Create mobile reports with SQL Server Mobile Report Publisher](../../Topics/TopicNameNotContainA/Create-mobile-reports-with-SQL-Server-Mobile-Report-Publisher.md).  
  
### SQL Server mobile reports hosted in Reporting Services available in Power BI Mobile app  
 The Power BI Mobile app for iOS on iPad and iPhone can now display SQL Server mobile reports hosted on your local report server.  
  
 ![SS_MRP_iPad_HomeSm](../../Topics/TopicNameNotContainA/media/SS_MRP_iPad_HomeSm.png "SS_MRP_iPad_HomeSm")  
  
 You can't connect by default without some configuration changes. For more information on how to allow the Power BI Mobile app to connect to your report server, see [Enable a report server for Power BI Mobile access](../../Topics/TopicNameContainA/Enable-a-report-server-for-Power-BI-Mobile-access.md).
  
## Support of SharePoint mode and SharePoint 2016  
 [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/includes/ssSQL15_md.md)] [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] supports integration with SharePoint 2013 and SharePoint 2016.
 
For more information, see:  
  
-   [Supported Combinations of SharePoint and Reporting Services Server and Add-in &#40;SQL Server 2016&#41;](../../Topics/TopicNameNotContainA/Supported-Combinations-of-SharePoint-and-Reporting-Services-Server-and-Add-in--SQL-Server-2016-.md)  
  
-   [Where to find the Reporting Services add-in for SharePoint Products](../../Topics/TopicNameNotContainA/Where-to-find-the-Reporting-Services-add-in-for-SharePoint-Products.md)  
  
-   [Install Reporting Services SharePoint Mode](../../Topics/TopicNameNotContainA/Install-Reporting-Services-SharePoint-Mode.md)  

## Microsoft .NET Framework 4 Support  
 [!INCLUDE[ssRSCurrent](../../Topics/TopicNameContainA/includes/ssRSCurrent_md.md)] supports the current versions of Microsoft .NET Framework 4. This includes version 4.0 and 4.5.1. If no version of .Net Framework 4.x is installed, [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] setup installs .NET 4.0 during the feature installation step.  

## Report improvements

**HTML 5 Rendering Engine:** A new  HTML5 rendering engine that targets modern web "full" standards mode and modern browsers.  The new rendering engine no longer relies on quirks mode used by a few older browsers.
  
 For more information on browser support, see [Browser Support for Reporting Services and Power View](../../Topics/TopicNameNotContainA/Browser-Support-for-Reporting-Services-and-Power-View.md).  

**Modern paginated reports:** Design beautifully modern paginated reports with new, modern styles for charts, gauges, maps and other data visualizations.
  
**Tree Map and Sunburst Charts:** Enhance your reports with Tree Map ![ssrs_treemap_icon](../../Topics/TopicNameNotContainA/media/ssrs_treemap_icon.png "ssrs_treemap_icon") and Sunburst ![ssrs_sunburst_icon](../../Topics/TopicNameNotContainA/media/ssrs_sunburst_icon.png "ssrs_sunburst_icon") charts, great ways to display hierarchal data. For more information, see [Tree Map and Sunburst Charts in Reporting Services](../../Topics/TopicNameNotContainA/Tree-Map-and-Sunburst-Charts-in-Reporting-Services.md).  

**Report embedding:** You can now embed mobile and paginated reports in other web pages, and applications, by using an iframe along with URL parameters.  

**Pin Report Items to a Power BI Dashboard:** While viewing a report in the [!INCLUDE[ssRSWebPortal](../../Topics/TopicNameContainA/includes/ssRSWebPortal.md)], you can select report items and pin them to a [!INCLUDE[sspowerbi](../../Topics/TopicNameNotContainA/includes/sspowerbi_md.md)] dashboard.   The items you can pin are charts, gauge panels, maps, and images. You can **\(1\)** select the group that contains the dashboard you want to pin to, **\(2\)** select the dashboard you want to pin the item too and **\(3\)** select how frequently you want the tile updated in the dashboard.   ![note](../../Topics/TopicNameNotContainA/media/ssrs_fyi_note.png "ssrs_fyi_note") The refresh is managed by  [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] subscriptions and after the item is pinned, you can edit the subscription and configure a different  refresh schedule.  
  
 ![ssRS_Pin_to_PowerBI](../../Topics/TopicNameNotContainA/media/ssRS_Pin_to_PowerBI.png) 
  
 For more information, see [Power BI Report Server Integration &#40;Configuration Manager&#41;](../../Topics/TopicNameNotContainA/Power-BI-Report-Server-Integration--Configuration-Manager-.md) and [Pin Reporting Services items to Power BI Dashboards](../../Topics/TopicNameNotContainA/Pin-Reporting-Services-items-to-Power-BI-Dashboards.md).  
 
 **PowerPoint Rendering and Export:** The Microsoft PowerPoint (PPTX) format is a new [!INCLUDE[ssRSCurrent](../../Topics/TopicNameContainA/includes/ssRSCurrent_md.md)] rendering extension. You can export reports in the PPTX format from the usual applications; Report Builder, Report Designer (in SSDT), and the [!INCLUDE[ssRSWebPortal](../../Topics/TopicNameContainA/includes/ssRSWebPortal.md)]. For the example the following image shows the export menu from the [!INCLUDE[ssRSWebPortal](../../Topics/TopicNameContainA/includes/ssRSWebPortal.md)]. 
  
 ![ssrs-export-powerpoint](../../Topics/TopicNameNotContainA/media/ssrs-export-powerpoint.png) 
  
 You can also select the PPTX format for subscription output and use Report Server URL access to render and export a report. For example the following  URL command in your browser exports a report from a named instance of the report server.  
  
```  
http://servername/ReportServer_THESQLINSTANCE/Pages/ReportViewer.aspx?%2freportfolder%2freport+name+with+spaces&rs:Format=pptx  
```  
  
 For more information, see [Export a Report Using URL Access](../../Topics/TopicNameContainA/Export-a-Report-Using-URL-Access.md).  
 
 **PDF Replaces ActiveX for Remote Printing:** The report viewer toolbar ActiveX print experience has been replaced with a modern PDF based experience that works across the matrix of supported browsers, including Microsoft Edge. No more ActiveX controls to download! Depending on the browser you use and the PDF viewing applications and services you have installed, [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] will either open  a print dialog to print your report or prompt you to download a .PDF file of your report.  As an administrator, you can still disable client side printing from [!INCLUDE[ssManStudio](../../Topics/TopicNameContainA/includes/ssManStudio_md.md)]. For more information, see [Enable and Disable Client-Side Printing for Reporting Services](../../Topics/TopicNameNotContainA/Enable-and-Disable-Client-Side-Printing-for-Reporting-Services.md).

![ssrs-pdf-printing](../../Topics/TopicNameNotContainA/media/ssrs-pdf-printing.png)

## Subscription Improvements  
 
|Feature|Supported server mode|  
|-------------|---------------------------|  
|**Enable and disable subscriptions**. New user interface options to quickly disable and enable subscriptions. The disabled subscriptions maintain their other configuration properties such as schedule and can be easily enabled.<br /><br /> ![ssrs-enable-disable-subscriptions](../../Topics/TopicNameNotContainA/media/ssrs-enable-disable-subscriptions.png)<br /><br /> For more information, see [Disable or Pause Report and Subscription Processing](../../Topics/TopicNameNotContainA/Disable-or-Pause-Report-and-Subscription-Processing.md).|Native mode|  
|**Subscription description**. When you create a new subscription, you can now include a description of the report as part of the subscription properties. The description is included on the subscription summary page.|SharePoint and Native mode|  
|**Change subscription owner**. Enhanced user interface to quickly change the owner of a subscription. Previous versions of [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] allow administrators to change subscription owners using script. Starting with the [!INCLUDE[ssSQL15](../../Topics/TopicNameContainA/includes/ssSQL15_md.md)] release, you can change subscription owners using the user interface or script. Changing the subscription owner is a common administrative task when users leave or change roles in your organization.|SharePoint and Native mode|  
|**Shared credential for file share subscriptions**. Two workflows now exist with [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] file share subscriptions:<br /><br /> New in this release, your [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] administrator can configure a single file share account, that is used for one to many subscriptions. The file share account is configured in the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/includes/ssRSnoversion_md.md)] native mode configuration manager **Specify a file share account**, and then on the subscription configuration page, users select **Use file share account**.<br /><br /> Configure individual subscriptions with specific credentials for the destination file share.<br /><br /> You can also mix the two approaches and have some file share subscriptions use the central file share account while other subscriptions use specific credentials.|Native mode|  

## SQL Server Data Tools (SSDT)  
 The new release of SSDT includes the project templates for [!INCLUDE[ssRSCurrent](../../Topics/TopicNameContainA/includes/ssRSCurrent_md.md)]: Report Server Project Wizard and Report Server Project. For information about downloading SSDT, see [SQL Server Data Tools for Visual Studio 2015](http://go.microsoft.com/fwlink/?LinkId=627574).  

## Report Builder improvements

**New Report Builder User Interface:** The core [!INCLUDE[ssRBnoversion](../../Topics/TopicNameContainA/includes/ssRBnoversion_md.md)] user interface is now a modern look and feel with streamlined UI elements.  
  
|||  
|-|-|  
|New|Previous|  
|![ssrs_rbfacelift_new](../../Topics/TopicNameNotContainA/media/ssrs_rbfacelift_new.png "ssrs_rbfacelift_new")|![ssrs_rbfacelift_old](../../Topics/TopicNameNotContainA/media/ssrs_rbfacelift_old.png "ssrs_rbfacelift_old")|  

**Custom Parameters Pane:** You can now customize the parameters pane. Using the design surface in Report Builder, you can drag a parameter to a specific column and row in the parameters pane. You can add and remove columns to change the layout of the pane.   For more information, see [Customize the Parameters Pane in a Report &#40;Report Builder&#41;](../../Topics/TopicNameContainA/Customize-the-Parameters-Pane-in-a-Report--Report-Builder-.md).  
  
 ![Parameter list in Report Data pane and in parameters pane](../../Topics/TopicNameNotContainA/media/ssrs_CustomizeParameter_ParameterList_ReportDataPane.png "ssrs_CustomizeParameter_ParameterList_ReportDataPane")  

  
**High DPI Support:** [!INCLUDE[ssRBnoversion](../../Topics/TopicNameContainA/includes/ssRBnoversion_md.md)] for [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/includes/ssCurrent_md.md)] supports High DPI (Dots Per Inch) scaling and devices.  For more information on High DPI, see the following:  
  
-   [Windows 8.1 DPI Scaling Enhancements](http://blogs.windows.com/bloggingwindows/2013/07/15/windows-8-1-dpi-scaling-enhancements/)  
  
-   [High DPI and Windows 8.1](http://technet.microsoft.com/library/dn528848.aspx)  
  
## See Also  
 [What's New in Analysis Services](assetId:///aa69c299-b8f4-4969-86d8-b3292fe13f08)  
 [SQL Server 2016 Release Notes](../../Topics/TopicNameNotContainA/SQL-Server-2016-Release-Notes.md)   
 [Reporting Services Backward Compatibility](../../Topics/TopicNameNotContainA/Reporting-Services-Backward-Compatibility.md)   
 [Features Supported by the Editions of SQL Server 2016](../../Topics/TopicNameNotContainA/Features-Supported-by-the-Editions-of-SQL-Server-2016.md)   
 [Upgrade and Migrate Reporting Services](../../Topics/TopicNameNotContainA/Upgrade-and-Migrate-Reporting-Services.md)   
 [Reporting Services &#40;SSRS&#41;](../../Topics/TopicNameNotContainA/Reporting-Services--SSRS-.md)  
  
  