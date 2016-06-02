---
title: SetExtendedProtectionSettings Method (WMI MSReportServer_ConfigurationSetting)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2d8e7232-42f4-41b6-98eb-c856f6c85d8c
---
# SetExtendedProtectionSettings Method (WMI MSReportServer_ConfigurationSetting)
  The SetExtendedProtectionSettings method is used to set the RSWindowsExtendedProtectionLevel and the RSWindowsExtendedProtectionScenario properties in the [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] configuration file RSReportServer.config.  
  
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
  
 To set the ExtendedProtectionLevel, the user must be a member of the BUILTIN\\Administrators group on the report server.  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [RSWindowsExtendedProtectionScenario Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](../Topic/RSWindowsExtendedProtectionScenario%20Property%20\(WMI%20MSReportServer_ConfigurationSetting\).md)   
 [RSWindowsExtendedProtectionLevel Property &#40;WMI MSReportServer_ConfigurationSetting&#41;](../Topic/RSWindowsExtendedProtectionLevel%20Property%20\(WMI%20MSReportServer_ConfigurationSetting\).md)   
 [Extended Protection for Authentication with Reporting Services](../../Topics\TopicNameNotContainA/Extended-Protection-for-Authentication-with-Reporting-Services.md)   
 [RsReportServer.config Configuration File](../../Topics\TopicNameNotContainA/RsReportServer.config-Configuration-File.md)  
  
  