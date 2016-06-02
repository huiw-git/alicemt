---
title: Install Report Builder
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6b2291bb-1d20-4d08-81cb-a16dd8e01faf
---
# Install Report Builder
  [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] is a stand\-alone app, installed on your computer by you or an administrator. You can install it from the Microsoft Download Center, from a [!INCLUDE[ssRSCurrent](../../Token\Other/ssRSCurrent_md.md)] report server, or from a SharePoint site integrated with [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)].  
  
 An administrator typically installs and configures [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], grants permission to download [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] from the web portal, and manages folders and permissions to reports, report parts, and shared datasets saved to the report server. For more information about [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] administration, see [Reporting Services Report Server &#40;Native Mode&#41;](../Topic/Reporting%20Services%20Report%20Server%20\(Native%20Mode\).md).  
  
 **Install [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] from  a  web portal or SharePoint library**  
  
 You can start [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] from a [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] web portal or a SharePoint site integrated with [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]. For information, see [Start Report Builder](../../Topics\TopicNameNotContainA/Start-Report-Builder.md).  
  
 **SharePoint site integrated with [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]**  
  
 On a SharePoint site integrated with [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], if the **New Document** menu does not list **Report Builder Report**, **Report Builder Model**, and **Report Data Source**, their content types need to be added to the SharePoint library. For more information, see [Add Reporting Services Content Types to a SharePoint Library](../../Topics\TopicNameContainA/Add-Reporting-Services-Content-Types-to-a-SharePoint-Library.md).  
  
 **Command\-line installation**  
  
 You can also perform a command line installation of [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] and provide arguments to customize the installation. In addition to the standard MSI intrinsic parameters, you can use the custom parameters that [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] provides: RBINSTALLDIR and REPORTSERVERURL. RBINSTALLDIR specifies the root installation folder for [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)]. REPORTSERVERURL specifies the default report server that [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] uses to save reports on the server.  
  
 If you want a completely silent installation, with no user interface interaction at all, specify the **\/quiet** option. By design, the quiet option flag suppresses installation errors. It is therefore recommended that you include the **\/l** option, which specifies logging, when you use the quiet option.  
  
 **Installation with Systems Manager Server**  
  
 An administrator can also use software such as Microsoft Systems Manager Server \(SMS\) to push the program to your computer. To learn how to use specific software to install [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)], consult the documentation for the software. For more about SMS, see the [Microsoft Systems Manager Server \(SMS\) site](http://www.Microsoft.com/SMSServer).  
  
> [!IMPORTANT]  
>  Windows Vista and Windows 7 security features require elevated permissions to run command line operations and will prompt for permission to run the command line. The installation is not silent. To make the installation silent, you need to run the command line as an administrator.  
  
 **System Requirements**  
  
 See the **System Requirements** section of the [Report Builder download page](http://go.microsoft.com/fwlink/?LinkID=219138) on the Microsoft Download Center.  
  
##  <a name="download"></a> To install [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] from the download site  
  
1.  On  the [Report Builder page of the Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=219138) , click **Download**.  
  
2.  After [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] has finished downloading, click  **Run**.  
  
     This launches the SQL Server [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] Wizard.  
  
3.  Accept the terms in the license agreement and click **Next**.  
  
4.  On the **Default Target Server** page, optionally provide the URL to the target report server if it is different from the default. Click **Next**.  
  
    > [!NOTE]  
    >  If you plan to work with [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] when it is connected to a report server, it is convenient to provide the URL to the server at this time. You can also do this from the **Options** dialog box in [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)].  
  
5.  Click **Install** to complete the installation of [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)].  
  
### To install [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] from a share  
  
1.  Contact your administrator for the location of ReportBuilder3.msi that you run to install [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] on your local computer.  
  
2.  Browse to locate ReportBuilder3.msi, the Windows Installer Package \(MSI\) for [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)], and click it.  
  
     This launches the SQL Server [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] Wizard.  
  
3.  Complete rest of the steps in [To install Report Builder from the download site](#download).  
  
### To install [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] from the command line  
  
1.  On  the [Report Builder page of the Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=219138), click **Download**.  
  
2.  After [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] has finished downloading, click  **Save**.  
  
3.  On the **Start** menu, click **Run**.  
  
4.  In the **Open** box, type **cmd.**  
  
5.  In the Command Prompt window, navigate to the folder where you saved ReportBuilder3.msi.  
  
6.  Type a command with the following format:  
  
     `msiexec/i ReportBuilder3.msi /option [value] [/option [value]]`  
  
     The two options specific to installing [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] are: RBINSTALLDIR and REPORTSERVERURL. You don't have to include these arguments in the command line. The following is the baseline command:  
  
     `msiexec /i ReportBuilder3_x86.msi /quiet`  
  
7.  To run the command, press ENTER.  
  
### Set [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] defaults  
  
-   After you install [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)], you can set some default options. Click **File** \> **Options**.  
  
     Setting the default [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] web portal or SharePoint site is the most useful. For more information, see [Set default options for Report Builder](../../Topics\TopicNameNotContainA/Set-default-options-for-Report-Builder.md).  
  
-   Click **Report Builder** .  
  
     If you don’t see the report server in the list of existing servers, close the **Open Report** dialog box and then click **Connect** at the bottom of [!INCLUDE[ssRBnoversion](../../Token\Other/ssRBnoversion_md.md)] to connect to the server.  
  
## See Also  
 [Start Report Builder](../../Topics\TopicNameNotContainA/Start-Report-Builder.md)   
 [Uninstall Report Builder](../../Topics\TopicNameNotContainA/Uninstall-Report-Builder.md)  
  
  