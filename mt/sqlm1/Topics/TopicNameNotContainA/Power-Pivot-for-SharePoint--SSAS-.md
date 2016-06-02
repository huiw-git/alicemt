---
title: Power Pivot for SharePoint (SSAS)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
  - analysis-services/multidimensional-tabular
  - analysis-services/data-mining
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c4c393d3-4856-47ac-ab5f-15da2f240d1d
---
# Power Pivot for SharePoint (SSAS)
  An [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] server in [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] mode provides server hosting of [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] data in a SharePoint farm. [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] data is an analytical data model that you build using one of the following:  
  
-   The [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for Excel 2010 add\-in  
  
-   Excel 2013  
  
-   Excel 2016  
  
 **[!INCLUDE[applies](../../Token\Other/applies_md.md)]**  [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] 2016 | [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] 2013  
  
 Server hosting of that data requires SharePoint, Excel Services, and an installation of [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint. Data is loaded on [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint instances where it can be refreshed at scheduled intervals using the [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] data refresh capability that the server provides for Excel 2010 workbooks, that the [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] provides for Excel 2013 and 2016 workbooks.  
  
## Power Pivot for SharePoint 2016  
 [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] supports [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] SharePoint 2016 and [!INCLUDE[offOnlineServer](../../Token\Other/offOnlineServer_md.md)] usage of Excel workbooks containing data models and [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Power View reports.  
  
 Excel, within [!INCLUDE[offOnlineServer](../../Token\Other/offOnlineServer_md.md)] includes data model functionality to enable interaction with a [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] workbook in the browser. You do not need to deploy the [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint 2016 add\-in into the farm. You only need to install an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] server in [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] mode and register the server with [!INCLUDE[offOnlineServer](../../Token\Other/offOnlineServer_md.md)].  
  
 Deploying the [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint 2016 add\-in enables additional functionality and features in your SharePoint farm. The additional features include [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] Gallery and Schedule Data Refresh.  
  
 ![SSAS Power Pivot Mode 3 Server with Office Online Server](../../Images\Image\ImageNotContaina/AS_PowerPivot_Mode_3Server_OOS_Deploy.png "AS_PowerPivot_Mode_3Server_OOS_Deploy")  
  
## Power Pivot for SharePoint 2013  
 [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] [!INCLUDE[ssGeminiShort](../../Token\Other/ssGeminiShort_md.md)] supports [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] SharePoint 2013 Excel Services usage of Excel workbooks containing data models and [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Power View reports.  
  
 Excel Services in SharePoint 2013 includes data model functionality to enable interaction with a [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] workbook in the browser. You do not need to deploy the [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint 2013 add\-in into the farm. You only need to install an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] server in SharePoint mode and register the server within the Excel Services **Data Model** settings.  
  
 Deploying the [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint 2013 add\-in enables additional functionality and features in your SharePoint farm. The additional features include [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] Gallery, Schedule Data Refresh, and the [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] Management Dashboard.  
  
 ![SSAS PowerPivot Mode 2 Server Deployment](../../Images\Image\ImageNotContaina/AS_PowerPivot_Mode_2server_Deployment.gif "AS_PowerPivot_Mode_2server_Deployment")  
  
##  <a name="bkmk_RelatedContent"></a> In This Section  
 [Power Pivot Server Administration and Configuration in Central Administration](../../Topics\TopicNameNotContainA/Power-Pivot-Server-Administration-and-Configuration-in-Central-Administration.md)  
  
 [Power Pivot Configuration using Windows PowerShell](../../Topics\TopicNameNotContainA/Power-Pivot-Configuration-using-Windows-PowerShell.md)  
  
 [Power Pivot Configuration Tools](../../Topics\TopicNameNotContainA/Power-Pivot-Configuration-Tools.md)  
  
 [Power Pivot Authentication and Authorization](../../Topics\TopicNameNotContainA/Power-Pivot-Authentication-and-Authorization.md)  
  
 [Configure Power Pivot Health Rules](../../Topics\TopicNameNotContainA/Configure-Power-Pivot-Health-Rules.md)  
  
 [Power Pivot Management Dashboard and Usage Data](../../Topics\TopicNameNotContainA/Power-Pivot-Management-Dashboard-and-Usage-Data.md)  
  
 [Power Pivot Gallery](../../Topics\TopicNameNotContainA/Power-Pivot-Gallery.md)  
  
 [Power Pivot Data Access](../../Topics\TopicNameNotContainA/Power-Pivot-Data-Access.md)  
  
 [Power Pivot Data Refresh](../../Topics\TopicNameNotContainA/Power-Pivot-Data-Refresh.md)  
  
 [Power Pivot Data Feeds](../../Topics\TopicNameNotContainA/Power-Pivot-Data-Feeds.md)  
  
 [Power Pivot BI Semantic Model Connection &#40;.bism&#41;](../Topic/Power%20Pivot%20BI%20Semantic%20Model%20Connection%20\(.bism\).md)  
  
 **In other sections**  
  
## Additional topics  
 [Upgrade Power Pivot for SharePoint](../../Topics\TopicNameNotContainA/Upgrade-Power-Pivot-for-SharePoint.md)  
  
 [Install Analysis Services in Power Pivot Mode](../../Topics\TopicNameNotContainA/Install-Analysis-Services-in-Power-Pivot-Mode.md)  
  
 [PowerShell Reference for Power Pivot for SharePoint](../../Topics\TopicNameNotContainA/PowerShell-Reference-for-Power-Pivot-for-SharePoint.md)  
  
 [Example License Topologies and Costs  for SQL Server 2016 Business Intelligence](../../Topics\TopicNameNotContainA/Example-License-Topologies-and-Costs--for-SQL-Server-2016-Business-Intelligence.md)  
  
## See Also  
 [Power Pivot Planning and Deployment](http://go.microsoft.com/fwlink/?linkID=220972)   
 [Disaster Recovery for Power Pivot for SharePoint](http://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  