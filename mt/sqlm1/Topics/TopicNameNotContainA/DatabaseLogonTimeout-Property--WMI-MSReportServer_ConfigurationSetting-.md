---
title: DatabaseLogonTimeout Property (WMI MSReportServer_ConfigurationSetting)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
apiname: 
  - DatabaseLogonTimeout Property
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: 4a65162c-33de-485e-8fd3-2bd6bff8bf8d
---
# DatabaseLogonTimeout Property (WMI MSReportServer_ConfigurationSetting)
  Specifies the number of seconds to wait before an attempt to log on to the report server database fails. A value of **0** indicates an infinite wait time. Read only.  
  
## Syntax  
  
```vb#  
Public Dim DatabaseLogonTimeout As Int32  
```  
  
```c#  
public Int32 DatabaseLogonTimeout;  
```  
  
## Property Values  
 A 32\-bit signed integer object that represents the number of seconds.  
  
## Example Code  
 [MSReportServer_ConfigurationSetting Class](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Class.md)  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  