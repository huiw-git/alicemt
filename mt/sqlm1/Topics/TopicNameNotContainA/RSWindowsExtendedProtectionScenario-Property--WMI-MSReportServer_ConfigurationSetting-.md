---
title: RSWindowsExtendedProtectionScenario Property (WMI MSReportServer_ConfigurationSetting)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5ac7ab80-9adf-4f65-abfa-fedf53b082b5
---
# RSWindowsExtendedProtectionScenario Property (WMI MSReportServer_ConfigurationSetting)
  Returns a string value that indicates the extended protection scenario the report server is configured to allow.  
  
## Syntax  
  
```vb#  
Public Dim RSWindowsExtendedProtectionScenario As String  
```  
  
```c#  
public string RSWindowsExtendedProtectionScenario;  
```  
  
## Remarks  
 Returns a string value that indicates the extended protection scenario the report server is configured to allow. If the report server that the WMI provider is connected to does not support extended protection, “” \(empty string\) is returned.  
  
 The following list shows valid values:  
  
 `”Any | Proxy | Direct”`  
  
## Example Code  
 [MSReportServer_ConfigurationSetting Class](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Class.md)  
  
## See Also  
 [RSWindowsExtendedProtectionLevel Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](../Topic/RSWindowsExtendedProtectionLevel%20Property%20\(WMI%20MSReportServer_ConfigurationSetting\).md)   
 [SetExtendedProtectionSettings Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../Topic/SetExtendedProtectionSettings%20Method%20\(WMI%20MSReportServer_ConfigurationSetting\).md)   
 [Extended Protection for Authentication with Reporting Services](../../Topics\TopicNameNotContainA/Extended-Protection-for-Authentication-with-Reporting-Services.md)   
 [RsReportServer.config Configuration File](../../Topics\TopicNameNotContainA/RsReportServer.config-Configuration-File.md)  
  
  