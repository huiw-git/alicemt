---
title: "IsSharePointIntegrated Property (WMI)"
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
ms.assetid: c548fed8-5e04-4faf-8b10-b37c86178056
caps.latest.revision: 12
caps.handback.revision: 0
manager: mblythe
---
# IsSharePointIntegrated Property (WMI)
Specifies whether the report server is in SharePoint integrated mode. Beginning in [!INCLUDE[ssSQL11](../../Topics/TopicNameContainA/tokens/ssSQL11_md.md)], this property always returns **False** because in SharePoint mode, [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] instances are SharePoint shared services and are not controlled by WMI providers.  
  
## Syntax  
  
```vb#  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```c#  
public Boolean IsSharePointIntegrated;  
```  
  
## Property Values  
 A **Boolean** object that indicates whether the report server is in SharePoint integrated mode.  
  
## Example Code  
 [MSReportServer_ConfigurationSetting Class](../../Topics/TopicNameNotContainA/MSReportServer_ConfigurationSetting-Class.md)  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Topics/TopicNameNotContainA/tokens/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics/TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)