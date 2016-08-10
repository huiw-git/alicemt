---
title: "ListInstalledSharePointVersions Method (WMI)"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8f0a5e9f-23f1-41e5-9a90-dfec19ef1df7
caps.latest.revision: 14
caps.handback.revision: 0
manager: mblythe
---
# ListInstalledSharePointVersions Method (WMI)
Returns a set of tokens that represent the versions of Microsoft [!INCLUDE[winSPServ](../../Topics/TopicNameContainA/tokens/winSPServ_md.md)], [!INCLUDE[offSPServ](../../Topics/TopicNameContainA/tokens/offSPServ_md.md)], [!INCLUDE[SPF2010](../../Topics/TopicNameContainA/tokens/SPF2010_md.md)], or [!INCLUDE[SPS2010](../../Topics/TopicNameContainA/tokens/SPS2010_md.md)] that are installed on the same computer as the report server.  
  
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
 *VersionTokens[]*  
 [out] An array that contains the tokens that represent the version of a SharePoint product or technology that is compatible with the installed report server.  
  
 *Length*  
 [out] The length of the version tokens array.  
  
 *HRESULT*  
 [out] Value indicating whether the call succeeded or failed.  
  
## Return Value  
 Returns an *HRESULT* indicating success or failure of the method call. A value of 0 indicates that the method call was successful. A non-zero value indicates that an error has occurred.  
  
## Remarks  
 Each token that is returned represents a version of [!INCLUDE[winSPServ](../../Topics/TopicNameContainA/tokens/winSPServ_md.md)] or [!INCLUDE[SPF2010](../../Topics/TopicNameContainA/tokens/SPF2010_md.md)] that is compatible with the currently installed report server. If a particular version of SharePoint is compatible with previous SharePoint versions, tokens for each compatible SharePoint version are returned.  
  
 The following is a table of the SharePoint tokens that are returned.  
  
|**Version Tokens**|**Description**|  
|------------------------|---------------------|  
|WSS_V2_Compatible|A [!INCLUDE[winSPServ](../../Topics/TopicNameContainA/tokens/winSPServ_md.md)], [!INCLUDE[winSPServ](../../Topics/TopicNameContainA/tokens/winSPServ_md.md)], [!INCLUDE[offSPServ](../../Topics/TopicNameContainA/tokens/offSPServ_md.md)], [!INCLUDE[SPF2010](../../Topics/TopicNameContainA/tokens/SPF2010_md.md)], or [!INCLUDE[SPS2010](../../Topics/TopicNameContainA/tokens/SPS2010_md.md)] installation is installed that is compatible with [!INCLUDE[winSPServ](../../Topics/TopicNameContainA/tokens/winSPServ_md.md)] 2.0.|  
|WSS_V3_Compatible|A [!INCLUDE[winSPServ](../../Topics/TopicNameContainA/tokens/winSPServ_md.md)], [!INCLUDE[winSPServ](../../Topics/TopicNameContainA/tokens/winSPServ_md.md)], [!INCLUDE[offSPServ](../../Topics/TopicNameContainA/tokens/offSPServ_md.md)], [!INCLUDE[SPF2010](../../Topics/TopicNameContainA/tokens/SPF2010_md.md)], or [!INCLUDE[SPS2010](../../Topics/TopicNameContainA/tokens/SPS2010_md.md)] installation is installed that is compatible with [!INCLUDE[winSPServ](../../Topics/TopicNameContainA/tokens/winSPServ_md.md)] 3.0.|  
|WSS_V4_Compatible|A [!INCLUDE[SPF2010](../../Topics/TopicNameContainA/tokens/SPF2010_md.md)] or [!INCLUDE[SPS2010](../../Topics/TopicNameContainA/tokens/SPS2010_md.md)] installation is installed that is compatible with Office 14.|  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Topics/TopicNameNotContainA/tokens/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics/TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)