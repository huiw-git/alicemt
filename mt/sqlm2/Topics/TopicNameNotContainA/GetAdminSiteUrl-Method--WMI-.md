---
title: GetAdminSiteUrl Method (WMI)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fbc5bf3c-120c-4aec-a4f2-f5391bd415f6
---
# GetAdminSiteUrl Method (WMI)
  Gets the absolute URL for the Central Administration Web site for the Microsoft [!INCLUDE[winSPServ](../../Token\Other/winSPServ_md.md)], [!INCLUDE[offSPServ](../../Token\Other/offSPServ_md.md)], [!INCLUDE[SPF2010](../../Token\Other/SPF2010_md.md)], or [!INCLUDE[SPS2010](../../Token\Other/SPS2010_md.md)] farm that the report server is integrated with.  
  
## Syntax  
  
```vb#  
Public Sub GetAdminSiteUrl(ByRef AdminSiteUrl as String, _  
ByRef HRESULT as Int32)  
```  
  
```c#  
public void GetAdminSiteUrl(out string AdminSiteUrl, out Int32 HRESULT);  
```  
  
## Parameters  
 *AdminSiteUrl*  
 \[out\] A string that contains the absolute URL for the Central Administration Web site for the SharePoint farm that the report server is integrated with.  
  
 *HRESULT*  
 \[out\] Value indicating whether the call succeeded or failed.  
  
## Return Value  
 Returns an *HRESULT* indicating success or failure of the method call. A value of 0 indicates that the method call was successful. A non\-zero value indicates that an error has occurred.  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Methods](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Methods.md)  
  
  