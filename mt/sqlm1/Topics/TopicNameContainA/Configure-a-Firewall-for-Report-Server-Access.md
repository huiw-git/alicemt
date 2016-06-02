---
title: Configure a Firewall for Report Server Access
ms.custom: 
  - SQL2016_New_Updated
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 04dae07a-a3a4-424c-9bcb-a8000e20dc93
---
# Configure a Firewall for Report Server Access
  [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] Report server applications and published reports are accessed through URLs that specify an IP address, port, and virtual directory. If Windows Firewall is turned on, the port that the report server is configured to use is most likely closed. Indications that a port might be closed are the a blank page when you attempt to open **Report Manager** from a remote client computer or a blank Web page after requesting a report.  
  
 To open a port, you must use the Windows Firewall utility on the report server computer. Reporting Services will not open ports for you; you must perform this step manually.  
  
 By default, the report server listens for HTTP requests on port 80. As such, the following instructions include steps that specify that port. If you configured the report server URLs to use a different port, you must specify that port number when following the instructions below.  
  
 If you are accessing [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] relational databases on external computers, or if the report server database is on an external [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] instance, you must open port 1433 and 1434 on the external computer. For more information, see [Configure a Windows Firewall for Database Engine Access](../../Topics\TopicNameContainA/Configure-a-Windows-Firewall-for-Database-Engine-Access.md) in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online. For more information about the default Windows firewall settings, and a description of the TCP ports that affect the [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)], [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], and [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)], see [Configure the Windows Firewall to Allow SQL Server Access](../../Topics\TopicNameNotContainA/Configure-the-Windows-Firewall-to-Allow-SQL-Server-Access.md) in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.  
  
## Prerequisites  
 These instructions assume that you already configured the service account, created the report server database, and configured URLs for the Report Server Web service and Report Manager. For more information, see [Manage a Reporting Services Native Mode Report Server](../../Topics\TopicNameContainA/Manage-a-Reporting-Services-Native-Mode-Report-Server.md).  
  
 You should also have verified that the report server is accessible over a local Web browser connection to the local report server instance. This step establishes that you have a working installation. You should verify that the installation is configured correctly before you begin opening ports. To complete this step on  Windows Server, you must have also added the report server site to Trusted Sites. For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../Topic/Configure%20a%20Native%20Mode%20Report%20Server%20for%20Local%20Administration%20\(SSRS\).md).  
  
## Opening Ports in Windows Firewall  
  
#### To open port 80  
  
1.  From the **Start** menu, click **Control Panel**, click **System and Security**, and then click **Windows Firewall**. Control Panel is not configured for 'Category' view, you only need to select **Windows Firewall.**  
  
2.  Click **Advanced Settings**.  
  
3.  Click **Inbound Rules.**  
  
4.  Click **New Rule** in the **Actions** window**.**  
  
5.  Click **Rule Type** of **Port.**  
  
6.  Click **Next**.  
  
7.  On the **Protocol and Ports** page click **TCP**.  
  
8.  Select **Specific Local Ports** and type a value of **80**.  
  
9. Click **Next**.  
  
10. On the **Action** page click **Allow the connection**.  
  
11. Click **Next**.  
  
12. On the **Profile** page click the appropriate options for your environment.  
  
13. Click **Next**.  
  
14. On the **Name** page enter a name of**ReportServer \(TCP on port 80\)**  
  
15. Click **Finish**.  
  
16. Restart the computer.  
  
## Next Steps  
 After you open the port and before you confirm whether remote users can access the report server on the port that you open, you must grant user access to the report server through role assignments on Home and at the site level. You can open a port correctly and still have report server connections fail if users do not have sufficient permissions. For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](../Topic/Grant%20User%20Access%20to%20a%20Report%20Server%20\(Report%20Manager\).md) in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.  
  
 You can also verify that the port is opened correctly by starting Report Manager on a different computer. For more information, see [Report Manager  &#40;SSRS Native Mode&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md) in [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Books Online.  
  
## See Also  
 [Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20the%20Report%20Server%20Service%20Account%20\(SSRS%20Configuration%20Manager\).md)   
 [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20Report%20Server%20URLs%20%20\(SSRS%20Configuration%20Manager\).md)   
 [Create a Report Server Database  &#40;SSRS Configuration Manager&#41;](../Topic/Create%20a%20Report%20Server%20Database%20%20\(SSRS%20Configuration%20Manager\).md)   
 [Configure the Report Server Service Account &#40;SSRS Configuration Manager&#41;](../Topic/Configure%20the%20Report%20Server%20Service%20Account%20\(SSRS%20Configuration%20Manager\).md)   
 [Manage a Reporting Services Native Mode Report Server](../../Topics\TopicNameContainA/Manage-a-Reporting-Services-Native-Mode-Report-Server.md)  
  
  