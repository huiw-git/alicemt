---
title: Accept License Terms
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 08dd739d-5817-4418-bcff-74ab7f8bbd33
---
# Accept License Terms
  Use the **Accept License Terms** page of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Wizard to accept the license terms for this release of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
 You can print the license agreement or copy it to the Clipboard. To continue, accept the license terms, and then click **Next**. To close the installation, click **Cancel**.  
  
## Customer Experience Improvement Program \(CEIP\)  
 If you enable CEIP reporting, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is configured to periodically send a report to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)]. Reports include information about your hardware configuration and how you use [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and components. [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] will use feature usage data to improve [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] components monitored by this feature include the following:  
  
-   The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]  
  
-   Replication  
  
-   [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Setup  
  
 Information about feature use is sent to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)], where it is stored with limited access.  
  
 To disable CEIP reporting after Setup completes, use the **[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Error and Usage Reporting** tool on the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]**Configuration Tools** menu.  
  
 For Setup actions like installation, upgrade, repair, and so on, information is collected and uploaded only during the Setup program execution  
  
 For all other [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] components, information is collected one time per day for all enabled instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]. By default, the time of collection is midnight to minimize the load on the server. If you want to change the time of collection, you can manually edit the registry key that controls the collection time. Each instance of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] has its own registry key:  
  
 HKLM\\Software\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)]\\[!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)][!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]\\MSSQL13.\<INSTANCEID\>\\CPE\\TimeofReporting  
  
 The value of this registry key contains the time for the collection as the number of minutes from 00:00 \(midnight\) to run. For example, a value of 60 would run the collection at 1:00 a.m., a value of 1200 would run the collection at 8:00 p.m., and so on.  
  
## Error Reporting  
 Use the **Error and Usage Report Settings** page of the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Installation Wizard to enable feature error and usage reporting functionality for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)].  
  
### Options  
 By default, the Feature Usage data collection and Error Reporting features are disabled for [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and its components in [!INCLUDE[ssCurrent](../../Token\Other/ssCurrent_md.md)].  
  
 Error Reporting  
 If you enable the Error Reporting feature, [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] is configured to send a report to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] automatically if a fatal error occurs in any of the following [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] components:  
  
-   The [!INCLUDE[ssDE](../../Token\Other/ssDE_md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] Agent  
  
-   [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)]  
  
-   Replication  
  
 [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] uses error reports to improve [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] functionality and treats all information as confidential.  
  
 Information about errors is sent over a secure \(https\) connection to [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)], where it is stored with limited access. Alternatively, error reports can be sent to your own Corporate Error Reporting server.  
  
 Error reports contain the following information:  
  
-   The condition of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] when the problem occurred.  
  
-   The operating system version and computer hardware information.  
  
-   Your Digital Product ID, which is not used to identify your license.  
  
-   The network IP address of your computer or proxy server.  
  
-   Information from memory or file\(s\) of the process that caused the error.  
  
 [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] does not intentionally collect your files, name, address, e\-mail address, or any other form of personal information. The error report can, however, contain personal information from the memory or files of the process that caused the error. Although this information can potentially be used to determine your identity, [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] does not use this information for that purpose.  
  
 For more information about the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] privacy and data collection policy, see [Microsoft SQL Server Privacy Statement](../../Topics\TopicNameNotContainA/Microsoft-SQL-Server-Privacy-Statement.md).  
  
 If you enable Error Reporting and a fatal error occurs, you might see a response from [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] in the Windows Event log that points to a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Knowledge Base article on a particular error.  
  
 To disable Error or Feature Usage reporting for all instances of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] and its components after Setup completes, go to the **Error and Usage Report Settings** dialog and clear the check boxes for **Feature Usage**. If **Error Reporting** is enabled for multiple components of [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] \(the [!INCLUDE[ssDEnoversion](../../Token\Other/ssDEnoversion_md.md)], [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)], [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)], and shared components\) you can disable Error Reporting for each instance of an individual component as well as shared components, listed as **Others**.  
  
## See Also  
 [About the SQL Server License Terms](../../Topics\TopicNameNotContainA/About-the-SQL-Server-License-Terms.md)  
  
  