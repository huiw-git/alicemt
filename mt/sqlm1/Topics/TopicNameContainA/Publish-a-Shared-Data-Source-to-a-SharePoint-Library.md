---
title: Publish a Shared Data Source to a SharePoint Library
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 966ed425-3ce2-4e76-8237-3c1c977954ae
---
# Publish a Shared Data Source to a SharePoint Library
  To publish a shared data source to a report server that is running in SharePoint integrated mode, you must set the report project properties in Report Designer. In the project properties, all references to servers, reports, and shared data sources must be fully qualified URLs.  
  
 You must have **Member** or **Owner** permission on the SharePoint site. For more information, see [URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../Topic/URL%20Examples%20for%20Published%20Report%20Items%20on%20a%20Report%20Server%20in%20SharePoint%20Mode%20\(SSRS\).md).  
  
### To publish a shared data source to a SharePoint site  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)], open your existing or new Report Server project.  
  
2.  On the **Project** menu, click **Properties**. The *\<project\>***Property Pages** dialog box opens.  
  
3.  Choose the **Configuration** you use to publish to a SharePoint site.  
  
4.  If you want to publish the shared data sources in your project and overwrite previously published shared data sources, set **OverwriteDataSources** to **True**.  
  
5.  \(Optional\) For **TargetDataSourceFolder**, type a URL to a SharePoint library or library folder. For example, *http:\/\/TestServer\/TestSite\/Documents\/DataSources*.  
  
     If you do not specify a value, the **TargetReportFolder** value is used.  
  
6.  For **TargetReportFolder**, type a URL to a library or library folder. For example, http:*\/\/TestServer\/TestSite\/Documents\/Reports*.  
  
7.  For **TargetServerURL**, type a URL to a SharePoint top\-level site or subsite. If you do not specify a site, the default top\-level site is used. For example, http:\/\/*servername*, http:\/\/*servername*\/*site*, or http:\/\/*servername*\/*site*\/*subsite*.  
  
8.  [!INCLUDE[clickOK](../../Token\Other/clickOK_md.md)]  
  
9. In Solution Explorer, right\-click the shared data source you want to publish, and click **Deploy**. The data source is published to the location specified in **TargetDataSourceFolder**. Deployment errors appear in the Output window.  
  
    > [!NOTE]  
    >  After you publish a shared data source to a SharePoint site, the file name extension is changed to .rsds. You can edit and manage a shared data source directly on the SharePoint site. For more information, see [Create and Manage Shared Data Sources &#40;Reporting Services in SharePoint Integrated Mode&#41;](../Topic/Create%20and%20Manage%20Shared%20Data%20Sources%20\(Reporting%20Services%20in%20SharePoint%20Integrated%20Mode\).md).  
  
## See Also  
 [Publish a Report to a SharePoint Library](../../Topics\TopicNameContainA/Publish-a-Report-to-a-SharePoint-Library.md)   
 [URL Examples for Published Report Items on a Report Server in SharePoint Mode &#40;SSRS&#41;](../Topic/URL%20Examples%20for%20Published%20Report%20Items%20on%20a%20Report%20Server%20in%20SharePoint%20Mode%20\(SSRS\).md)   
 [Project Property Pages Dialog Box](../../Topics\TopicNameNotContainA/Project-Property-Pages-Dialog-Box.md)   
 [Set Deployment Properties &#40;Reporting Services&#41;](../Topic/Set%20Deployment%20Properties%20\(Reporting%20Services\).md)   
 [Publishing Reports to a Report Server](../../Topics\TopicNameContainA/Publishing-Reports-to-a-Report-Server.md)   
 [Use an Office Data Connection &#40;.odc&#41; with Reports &#40;Reporting Services in SharePoint Integrated Mode&#41;](../Topic/Use%20an%20Office%20Data%20Connection%20\(.odc\)%20with%20Reports%20\(Reporting%20Services%20in%20SharePoint%20Integrated%20Mode\).md)  
  
  