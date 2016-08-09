---
title: "RSWindowsExtendedProtectionLevel Property (WMI MSReportServer_ConfigurationSetting)"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 162ffe86-69c3-49d2-b9ed-49d097c05551
caps.latest.revision: 7
manager: mblythe
---
# RSWindowsExtendedProtectionLevel Property (WMI MSReportServer_ConfigurationSetting)
Returns a string value that indicates the level of protection the report server is configured to support. This property is read-only.  
  
## Syntax  
  
```vb#  
Public Dim RSWindowsExtendedProtectionLevel As String  
```  
  
```c#  
public string RSWindowsExtendedProtectionLevel;  
```  
  
## Remarks  
 Returns a string value that indicates the level of protection the report server is configured to support. If the report server that the WMI provider is connected to does not support extended protection, “” (empty string) is returned. The following list shows valid values:  
  
 `“Off” | “Allow” | “Require”`  
  
## Example Code  
 [MSReportServer_ConfigurationSetting Class](../../Topics/TopicNameNotContainA/MSReportServer_ConfigurationSetting-Class.md)  
  
## See Also  
 [RSWindowsExtendedProtectionScenario Property (WMI MSReportServer_ConfigurationSetting)](../../Topics/TopicNameNotContainA/RSWindowsExtendedProtectionScenario-Property--WMI-MSReportServer_ConfigurationSetting-.md)   
 [SetExtendedProtectionSettings Method (WMI MSReportServer_ConfigurationSetting)](../../Topics/TopicNameNotContainA/SetExtendedProtectionSettings-Method--WMI-MSReportServer_ConfigurationSetting-.md)   
 [Extended Protection for Authentication with Reporting Services](../../Topics/TopicNameNotContainA/Extended-Protection-for-Authentication-with-Reporting-Services.md)   
 [RsReportServer.config Configuration File](../../Topics/TopicNameNotContainA/RsReportServer.config-Configuration-File.md)