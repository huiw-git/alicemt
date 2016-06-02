---
title: rsServerConfigurationError - Reporting Services Error
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0913afc2-34b4-4713-b570-cfd5718975ac
---
# rsServerConfigurationError - Reporting Services Error
    
## Details  
  
|||  
|-|-|  
|Product Name|[!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)]|  
|Event ID|rsServerConfiguration|  
|Event Source|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Component|[!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)]|  
|Message Text|The report server has encountered a configuration error.|  
  
## Explanation  
 This is a general purpose error that occurs when either the report server or a report authoring tool has invalid configuration settings. The error is usually accompanied by a second message that states the actual cause of the error.  
  
 The following list summarizes possible causes:  
  
-   The RSReportServer.config or RSReportDesigner.config file cannot be found or read.  
  
-   XML elements in either configuration file are missing or invalid.  
  
-   Values for one or more XML elements are missing or invalid.  
  
-   Registry settings are invalid.  
  
## User Action  
 If this error began to occur after you manually edited a configuration file, remove your changes and enter the previous value, or restore a previous version if you have a backup.  
  
 To review additional error message information that accompanies the **rsServerConfiguration** error, review the report server trace log files, which are located at \\Microsoft SQL Server\\MSRS12.\<instancename \>\\Reporting Services\\LogFiles. For more information, see [Reporting Services Log Files and Sources](../../Topics\TopicNameNotContainA/Reporting-Services-Log-Files-and-Sources.md).  
  
## Internal\-Only  
  
## See Also  
 [Reporting Services Configuration Files](../../Topics\TopicNameNotContainA/Reporting-Services-Configuration-Files.md)   
 [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](../Topic/Modify%20a%20Reporting%20Services%20Configuration%20File%20\(RSreportserver.config\).md)  
  
  