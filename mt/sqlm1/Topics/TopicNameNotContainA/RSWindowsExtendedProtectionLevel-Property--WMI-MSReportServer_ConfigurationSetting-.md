---
title: RSWindowsExtendedProtectionLevel Property (WMI MSReportServer_ConfigurationSetting)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 162ffe86-69c3-49d2-b9ed-49d097c05551
---
# RSWindowsExtendedProtectionLevel Property (WMI MSReportServer_ConfigurationSetting)
  Returns a string value that indicates the level of protection the report server is configured to support. This property is read\-only.  
  
## Syntax  
  
```vb#  
Public Dim RSWindowsExtendedProtectionLevel As String  
```  
  
```c#  
public string RSWindowsExtendedProtectionLevel;  
```  
  
## Remarks  
 Returns a string value that indicates the level of protection the report server is configured to support. If the report server that the WMI provider is connected to does not support extended protection, “” \(empty string\) is returned. The following list shows valid values:  
  
 `“Off” | “Allow” | “Require”`  
  
## Example Code  
 [MSReportServer_ConfigurationSetting Class](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Class.md)  
  
## See Also  
 [RSWindowsExtendedProtectionScenario Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](../Topic/RSWindowsExtendedProtectionScenario%20Property%20\(WMI%20MSReportServer_ConfigurationSetting\).md)   
 [SetExtendedProtectionSettings Method &#40;WMI MSReportServer_ConfigurationSetting&#41;](../Topic/SetExtendedProtectionSettings%20Method%20\(WMI%20MSReportServer_ConfigurationSetting\).md)   
 [Extended Protection for Authentication with Reporting Services](../../Topics\TopicNameNotContainA/Extended-Protection-for-Authentication-with-Reporting-Services.md)   
 [RsReportServer.config Configuration File](../../Topics\TopicNameNotContainA/RsReportServer.config-Configuration-File.md)  
  
  