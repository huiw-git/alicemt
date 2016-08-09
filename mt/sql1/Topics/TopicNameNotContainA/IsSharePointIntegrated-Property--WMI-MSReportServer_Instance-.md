---
title: "IsSharePointIntegrated Property (WMI MSReportServer_Instance)"
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
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
caps.latest.revision: 14
caps.handback.revision: 0
manager: mblythe
---
# IsSharePointIntegrated Property (WMI MSReportServer_Instance)
Specifies whether the report server is in SharePoint integrated mode. Beginning in [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)], this property always returns **False** because in SharePoint mode, [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] instances are SharePoint shared services and are not controlled by WMI providers.  
  
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
 **Namespace:** [!INCLUDE[ssRSWMInmspc](../../Topics/TopicNameNotContainA/tokens/ssRSWMInmspc_md.md)]  
  
## See Also  
 [MSReportServer_Instance Members](../../Topics/TopicNameNotContainA/MSReportServer_Instance-Members.md)   
 [MSReportServer_ConfigurationSetting Class](../../Topics/TopicNameNotContainA/MSReportServer_ConfigurationSetting-Class.md)