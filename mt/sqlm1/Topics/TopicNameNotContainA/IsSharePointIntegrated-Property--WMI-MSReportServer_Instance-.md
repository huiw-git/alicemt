---
title: IsSharePointIntegrated Property (WMI MSReportServer_Instance)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
---
# IsSharePointIntegrated Property (WMI MSReportServer_Instance)
  Specifies whether the report server is in SharePoint integrated mode. Beginning in [!INCLUDE[ssSQL11](../../Token\Other/ssSQL11_md.md)], this property always returns **False** because in SharePoint mode, [!INCLUDE[ssRSnoversion](../../Token\Other/ssRSnoversion_md.md)] instances are SharePoint shared services and are not controlled by WMI providers.  
  
## Syntax  
  
```vb#  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```c#  
public Boolean IsSharePointIntegrated;  
```  
  
## Property Values  
 A **Boolean** value that indicates whether the report server is in SharePoint integrated mode.  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspc](../../Token\Other/ssRSWMInmspc_md.md)]  
  
## See Also  
 [MSReportServer_Instance Members](../../Topics\TopicNameNotContainA/MSReportServer_Instance-Members.md)   
 [MSReportServer_ConfigurationSetting Class](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Class.md)  
  
  