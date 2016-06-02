---
title: Power Pivot Server Administration and Configuration in Central Administration
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
ms.assetid: 2cdbfdc5-45a9-4000-a03d-318cc7ac8fe9
---
# Power Pivot Server Administration and Configuration in Central Administration
  [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] server administration and configuration is performed by SharePoint service application administrators, using SharePoint Central Administration.  
  
 [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint must be configured before it can be used. After you install [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint using SQL Server Setup, you can configure it using any of the following approaches:  
  
-   [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] Configuration Tool or [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint 2013 Configuration tool  
  
-   SharePoint Central Administration  
  
-   PowerShell cmdlets  
  
 All three approaches deliver a fully configured server.  
  
 This section includes tasks for configuring the software using Central Administration. At a minimum, you must perform all three of the required configuration tasks noted in the list below.  
  
> [!IMPORTANT]  
>  For SharePoint 2010, SharePoint 2010 Service Pack 1 \(SP1\) must be installed before you can configure either [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint, or a SharePoint farm that uses a [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)] database server. If you have not yet installed the service pack, do so now before you begin configuring the server.  
  
## Benefits of Configuring Power Pivot for SharePoint Using Central Administration  
 SharePoint Central Administration is the administrative application of a SharePoint farm. If you are farm administrator, you might prefer to use a familiar tool when adding a [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] for SharePoint instance to your farm.  
  
 In contrast with the [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] Configuration Tools or PowerShell cmdlets, Central Administration provides pages that fully specify all of the options you might set when configuring an application or server. Other approaches either condense the configuration workflow into a fewer number of steps, or require prior knowledge of how to configure a SharePoint server using PowerShell.  
  
## Related Content  
 [Power Pivot Configuration using Windows PowerShell](../../Topics\TopicNameNotContainA/Power-Pivot-Configuration-using-Windows-PowerShell.md)  
  
 [Power Pivot Configuration Tools](../../Topics\TopicNameNotContainA/Power-Pivot-Configuration-Tools.md)  
  
## Related Tasks  
  
|Link|Type|Task Description|  
|----------|----------|----------------------|  
|[Deploy Power Pivot Solutions to SharePoint](../../Topics\TopicNameNotContainA/Deploy-Power-Pivot-Solutions-to-SharePoint.md)|Required|This step installs the solution files that add program files and application pages to the farm and to site collections.|  
|[Create and Configure a Power Pivot Service Application in Central Administration](../../Topics\TopicNameContainA/Create-and-Configure-a-Power-Pivot-Service-Application-in-Central-Administration.md)|Required|This step provisions the [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] System Service.|  
|[Activate Power Pivot Feature Integration for Site Collections in Central Administration](../../Topics\TopicNameNotContainA/Activate-Power-Pivot-Feature-Integration-for-Site-Collections-in-Central-Administration.md)|Required|This step turns on [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] features at the site collection level.|  
|[Add MSOLAP.5 as a Trusted Data Provider in Excel Services](../../Topics\TopicNameContainA/Add-MSOLAP.5-as-a-Trusted-Data-Provider-in-Excel-Services.md)|Required|This step adds the Analysis Services OLE DB provider as a trusted provider in Excel Services.|  
|[Power Pivot Data Refresh with SharePoint 2010](assetId:///01b54e6f-66e5-485c-acaa-3f9aa53119c9)|Recommended|Data refresh is optional but recommended. It allows you to schedule unattended updates to the [!INCLUDE[ssGemini](../../Token\Other/ssGemini_md.md)] data in published Excel workbooks.|  
|[Configure the Power Pivot Unattended Data Refresh Account \(Power Pivot for SharePoint\)](assetId:///81401eac-c619-4fad-ad3e-599e7a6f8493)|Recommended|This step provisions a special\-purpose account that can be used to run data refresh jobs on the server.|  
|[Configure Usage Data Collection for &#40;Power Pivot for SharePoint](../Topic/Configure%20Usage%20Data%20Collection%20for%20\(Power%20Pivot%20for%20SharePoint.md)|Optional|Usage data collection is configured by default. You can use these steps to modify the default settings.|  
|[Configure Dedicated Data Refresh or Query\-Only Processing \(Power Pivot for SharePoint\)](assetId:///5e027605-1086-4941-bb01-f315df8f829b)|Optional|A [!INCLUDE[ssGemini](../Token/ssGemini_md.md)] instance can be dedicated to just data refresh jobs or queries. In addition, you can modify default settings for parallel data refresh jobs.|  
|[Configure Power Pivot Service Accounts](../Topic/Configure%20Power%20Pivot%20Service%20Accounts.md)|Optional|Explains how to update passwords or change service accounts.|  
|[Connect a Power Pivot Service Application to a SharePoint Web Application in Central Administration](../Topic/Connect%20a%20Power%20Pivot%20Service%20Application%20to%20a%20SharePoint%20Web%20Application%20in%20Central%20Administration.md)|Optional|Explains how to modify service associations.|  
|[Create a trusted location for Power Pivot sites in Central Administration](../Topic/Create%20a%20trusted%20location%20for%20Power%20Pivot%20sites%20in%20Central%20Administration.md)|Optional|Explains how to add the [!INCLUDE[ssGemini](../Token/ssGemini_md.md)] Gallery as a trusted location.|  
|[Configure and View SharePoint Log Files  and Diagnostic Logging &#40;Power Pivot for SharePoint&#41;](../Topic/Configure%20and%20View%20SharePoint%20Log%20Files%20%20and%20Diagnostic%20Logging%20\(Power%20Pivot%20for%20SharePoint\).md)|Optional|Event logging is configured by default. You can use these steps to modify the default settings.|  
|[Configure Power Pivot Health Rules](../Topic/Configure%20Power%20Pivot%20Health%20Rules.md)|Optional|Server health rules are configured by default. You can use these steps to modify some of the default settings.|  
|[Create and Customize Power Pivot Gallery](../Topic/Create%20and%20Customize%20Power%20Pivot%20Gallery.md)|Optional|For installations that you are configuring manually, this procedure explains how to create a [!INCLUDE[ssGemini](../Token/ssGemini_md.md)] Gallery library that shows image thumbnails of the [!INCLUDE[ssGemini](../Token/ssGemini_md.md)] workbooks it contains.|  
|[Add a BI Semantic Model Connection Content Type to a Library &#40;Power Pivot for SharePoint&#41;](../Topic/Add%20a%20BI%20Semantic%20Model%20Connection%20Content%20Type%20to%20a%20Library%20\(Power%20Pivot%20for%20SharePoint\).md)|Optional|Explains how to extend a document library to support the creation of BI semantic model connection files.|  
  
## See Also  
 [Power Pivot for SharePoint 2010 Installation](assetId:///8d47dde7-c941-4280-a934-e2fe3f9a938f)   
 [Configuration Setting Reference &#40;Power Pivot for SharePoint&#41;](../Topic/Configuration%20Setting%20Reference%20\(Power%20Pivot%20for%20SharePoint\).md)   
 [Disaster Recovery for Power Pivot for SharePoint](http://go.microsoft.com/fwlink/p/?LinkId=389570)  
  
  