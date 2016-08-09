---
title: "SetExtendedProtectionSettings Method (WMI MSReportServer_ConfigurationSetting)"
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
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
caps.latest.revision: 8
caps.handback.revision: 0
manager: mblythe
---
# SetExtendedProtectionSettings Method (WMI MSReportServer_ConfigurationSetting)
The SetExtendedProtectionSettings method is used to set the RSWindowsExtendedProtectionLevel and the RSWindowsExtendedProtectionScenario properties in the [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] configuration file RSReportServer.config.  
  
## Syntax  
  
```vb#  
Public Sub SetExtendedProtectionSettings( _  
        ByVal ExtendedProtectionLevel As String, _  
        ByVal ExtendedProtectionScenario As String, _  
        ByRef Warnings() As String, _  
        ByRef Length As Int32, _  
        ByRef HRESULT As Int32)  
```  
  
```c#  
public void SetExtendedProtectionSettings(  
            string ExtendedProtectionLevel,  
            string ExtendedProtectionScenario,  
            out string[] Warnings,  
            out Int32 Length,  
            out Int32 HRESULT);  
```  
  
## Parameters  
 *ExtendedProtectionLevel*  
 Sets the RSWindowsExtendedProtectionLevel in the RSRreportserver.config file. The required value is not case sensitive.  
  
 The following list shows valid values:  
  
 `”Off | Allow | Require”`  
  
 *ExtendedProtectionScenario*  
 Sets the RSWindowsExtendedProtectionScenario in the RSReportserver.config file. The required value is not case sensitive.  
  
 The following list shows valid values:  
  
 `”Any” | “Proxy” | “Direct”`  
  
## Remarks  
 The RSWindowsExtendedProtectionLevel and the RSWindowsExtendedProtectionScenario properties apply when the AuthenticationTypes in the RSReportServer.config file include RSWindowNTLM, RSWindowsNegotiate, or RSWindowsKerberos. Setting these properties affects how users and client software authenticate with a report server. It is recommended that you read the documentation for extended protection before setting ExtendedProtectionLevel to either **Allow** or **Require**.  
  
 To set the ExtendedProtectionLevel, the user must be a member of the BUILTIN\Administrators group on the report server.  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Topics/TopicNameNotContainA/tokens/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [RSWindowsExtendedProtectionScenario Property (WMI MSReportServer_ConfigurationSetting)](../../Topics/TopicNameNotContainA/RSWindowsExtendedProtectionScenario-Property--WMI-MSReportServer_ConfigurationSetting-.md)   
 [RSWindowsExtendedProtectionLevel Property (WMI MSReportServer_ConfigurationSetting)](../../Topics/TopicNameNotContainA/RSWindowsExtendedProtectionLevel-Property--WMI-MSReportServer_ConfigurationSetting-.md)   
 [Extended Protection for Authentication with Reporting Services](../../Topics/TopicNameNotContainA/Extended-Protection-for-Authentication-with-Reporting-Services.md)   
 [RsReportServer.config Configuration File](../../Topics/TopicNameNotContainA/RsReportServer.config-Configuration-File.md)