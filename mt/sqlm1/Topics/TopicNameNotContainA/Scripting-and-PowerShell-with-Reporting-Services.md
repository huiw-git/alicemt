---
title: Scripting and PowerShell with Reporting Services
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1ac2646d-ed5a-4436-b18f-2150c33f3d87
---
# Scripting and PowerShell with Reporting Services
  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] supports a wide range of development and management scenarios through script, including the rs.exe command line utility, PowerShell cmdlets for SharePoint mode report servers, and leveraging the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] object model from PowerShell for both Native and SharePoint mode.  
  
-   Administrators can write script in [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[vbprvb](../../Token\Other/vbprvb_md.md)] to automate how they deploy and manage a report server installation. Administrators can also generate and run [!INCLUDE[tsql](../../Token\Other/tsql_md.md)] scripts that create, configure, and update a report server database. Administrators can also use the record and playback script features in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] [!INCLUDE[ssManStudio](../../Token\Other/ssManStudio_md.md)] to automate routine maintenance tasks.  
  
-   Developers can create custom applications that include script. You can run script that makes calls to the Report Server Web service. Almost any operation that you can write in managed code can also be written in script.  
  
-   [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] supports [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[vbprvb](../../Token\Other/vbprvb_md.md)] .NET script as the script language that can be processed by the RS.exe utility, a script host that runs on the report server.  
  
## Reporting Services SharePoint mode PowerShell cmdlets and samples  
 ![PowerShell related content](../../Images\Image\ImageNotContaina/rs_PowerShellicon.jpg "rs_PowerShellicon")  
  
 [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] SharePoint mode includes [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] cmdlets for report server administration.  
  
-   [PowerShell cmdlets for Reporting Services SharePoint Mode](../../Topics\TopicNameNotContainA/PowerShell-cmdlets-for-Reporting-Services-SharePoint-Mode.md) Includes the following examples:  
  
    -   Create a service application and proxy  
  
    -   Review and update a delivery extension  
  
    -   Get and set Properties of the Reporting Service Application Database, for example database timeout  
  
    -   List Data Extensions  
  
## Reporting Services Object model and Powershell samples  
 ![PowerShell related content](../../Images\Image\ImageNotContaina/rs_PowerShellicon.jpg "rs_PowerShellicon")  
  
 PowerShell calling the core object model and for the most part valid for SharePoint and native mode, for example the migration work, subscription work, and more related samples for subscriptions work in SQL15.  
  
-   [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](../../Topics\TopicNameContainA/Use-PowerShell-to-Change-and-List-Reporting-Services-Subscription-Owners-and-Run-a-Subscription.md).  
  
-   [Use PowerShell to Create an Azure VM With a Native Mode Report Server](http://msdn.microsoft.com/library/azure/dn449661.aspx).  
  
-   See the section “Access the WMI classes using PowerShell” in [Access the Reporting Services WMI Provider](../../Topics\TopicNameNotContainA/Access-the-Reporting-Services-WMI-Provider.md).  
  
-   [How to Administer SSRS using PowerShell](http://curah.microsoft.com/13107/how-to-administer-ssrs-using-powershell).  
  
## RS.exe scripting samples  
  
-   [Sample Reporting Services rs.exe Script to Copy Content between Report Servers](../../Topics\TopicNameNotContainA/Sample-Reporting-Services-rs.exe-Script-to-Copy-Content-between-Report-Servers.md).  
  
-   For additional script, application, and extension examples, see [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889).  
  
## See Also  
 [RS.exe Utility &#40;SSRS&#41;](../Topic/RS.exe%20Utility%20\(SSRS\).md)   
 [Script Deployment and Administrative Tasks](../../Topics\TopicNameNotContainA/Script-Deployment-and-Administrative-Tasks.md)   
 [Script with the rs.exe Utility and the Web Service](../../Topics\TopicNameNotContainA/Script-with-the-rs.exe-Utility-and-the-Web-Service.md)  
  
  