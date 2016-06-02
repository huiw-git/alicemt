---
title: ListInstalledSharePointVersions Method (WMI)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8f0a5e9f-23f1-41e5-9a90-dfec19ef1df7
---
# ListInstalledSharePointVersions Method (WMI)
  Returns a set of tokens that represent the versions of Microsoft [!INCLUDE[winSPServ](../../Token\Other/winSPServ_md.md)], [!INCLUDE[offSPServ](../../Token\Other/offSPServ_md.md)], [!INCLUDE[SPF2010](../../Token\Other/SPF2010_md.md)], or [!INCLUDE[SPS2010](../../Token\Other/SPS2010_md.md)] that are installed on the same computer as the report server.  
  
## Syntax  
  
```vb#  
Public Sub ListInstalledSharePointVersions(ByRef VersionTokens() _  
    As String, ByRef Length As Int32, ByRef HRESULT As Int32)  
```  
  
```c#  
public void ListReportServersInDatabase (out string[] VersionTokens,   
    out Int32 Length, out Int32 HRESULT);  
```  
  
## Parameters  
 *VersionTokens\[\]*  
 \[out\] An array that contains the tokens that represent the version of a SharePoint product or technology that is compatible with the installed report server.  
  
 *Length*  
 \[out\] The length of the version tokens array.  
  
 *HRESULT*  
 \[out\] Value indicating whether the call succeeded or failed.  
  
## Return Value  
 Returns an *HRESULT* indicating success or failure of the method call. A value of 0 indicates that the method call was successful. A non\-zero value indicates that an error has occurred.  
  
## Remarks  
 Each token that is returned represents a version of [!INCLUDE[winSPServ](../../Token\Other/winSPServ_md.md)] or [!INCLUDE[SPF2010](../../Token\Other/SPF2010_md.md)] that is compatible with the currently installed report server. If a particular version of SharePoint is compatible with previous SharePoint versions, tokens for each compatible SharePoint version are returned.  
  
 The following is a table of the SharePoint tokens that are returned.  
  
|**Version Tokens**|**Description**|  
|------------------------|---------------------|  
|WSS\_V2\_Compatible|A [!INCLUDE[winSPServ](../../Token\Other/winSPServ_md.md)], [!INCLUDE[winSPServ](../../Token\Other/winSPServ_md.md)], [!INCLUDE[offSPServ](../../Token\Other/offSPServ_md.md)], [!INCLUDE[SPF2010](../../Token\Other/SPF2010_md.md)], or [!INCLUDE[SPS2010](../../Token\Other/SPS2010_md.md)] installation is installed that is compatible with [!INCLUDE[winSPServ](../../Token\Other/winSPServ_md.md)] 2.0.|  
|WSS\_V3\_Compatible|A [!INCLUDE[winSPServ](../../Token\Other/winSPServ_md.md)], [!INCLUDE[winSPServ](../../Token\Other/winSPServ_md.md)], [!INCLUDE[offSPServ](../../Token\Other/offSPServ_md.md)], [!INCLUDE[SPF2010](../../Token\Other/SPF2010_md.md)], or [!INCLUDE[SPS2010](../../Token\Other/SPS2010_md.md)] installation is installed that is compatible with [!INCLUDE[winSPServ](../../Token\Other/winSPServ_md.md)] 3.0.|  
|WSS\_V4\_Compatible|A [!INCLUDE[SPF2010](../../Token\Other/SPF2010_md.md)] or [!INCLUDE[SPS2010](../../Token\Other/SPS2010_md.md)] installation is installed that is compatible with Office 14.|  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  