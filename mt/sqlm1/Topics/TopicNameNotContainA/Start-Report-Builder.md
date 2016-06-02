---
title: Start Report Builder
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
---
# Start Report Builder
  Microsoft [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)] [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] is a stand\-alone report authoring environment. With it, you can create paginated reports and publish them to [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] installed in native or SharePoint integrated mode.  
  
 The first time you start [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] from the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] web portal or [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] in SharePoint integrated mode, it installs automatically on your local computer. You or an administrator can also  install [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] on your computer from the Microsoft Download Center. [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] isn't installed when you install [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)]; you need to  download and install it separately.  
  
 [Download Report Builder](http://go.microsoft.com/fwlink/?LinkID=219138) from the Microsoft Download Center.  
  
 When you start [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] from the web portal or SharePoint site, if an earlier version of [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] opens, contact your administrator, who can update the version on the web portal or SharePoint site.  
  
## To start [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] from the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] web portal  
  
1.  In your Web browser, type the URL for your report server in the address bar. By default, the URL is http:\/\/\<*servername*\>\/reports.  
  
2.  In the top bar of the web portal, select **New** \> **Paginated Report**.  
  
     ![PBI_SSMRP_NewMenu](../../Images\Image\ImageNotContaina/PBI_SSMRP_NewMenu.png "PBI_SSMRP_NewMenu")  
  
     The first time, this launches the SQL Server [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] Wizard. See [Install Report Builder](../../Topics\TopicNameNotContainA/Install-Report-Builder.md) for more details.  
  
     [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] opens, and you can create a paginated report or open a report from the report server.  
  
## To start [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] in SharePoint integrated mode  
  
1.  Navigate to the SharePoint site that contains the library you want.  
  
2.  Open the library.  
  
3.  Click **Documents**.  
  
4.  On the **New Document** menu, click **Report Builder Report**.  
  
     The first time, this launches the SQL Server [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] Wizard. See [Install Report Builder](../../Topics\TopicNameNotContainA/Install-Report-Builder.md) for more details.  
  
     [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] opens, and you can create a paginated report or open a report on the report server.  
  
     **Note** If the **New Document** menu does not list **Report Builder Report**, **Report Builder Model**, or **Report Data Source**, their content types need to be added to the SharePoint library. For more information, see [Add Reporting Services Content Types to a SharePoint Library](../../Topics\TopicNameContainA/Add-Reporting-Services-Content-Types-to-a-SharePoint-Library.md).  
  
## See Also  
 [Report Builder in SQL Server 2016](../../Topics\TopicNameNotContainA/Report-Builder-in-SQL-Server-2016.md)   
 [Set default options for Report Builder](../../Topics\TopicNameNotContainA/Set-default-options-for-Report-Builder.md)  
  
  