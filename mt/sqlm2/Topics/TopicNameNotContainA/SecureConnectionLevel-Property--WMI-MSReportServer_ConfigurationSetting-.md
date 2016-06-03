---
title: SecureConnectionLevel Property (WMI MSReportServer_ConfigurationSetting)
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
  - SecureConnectionLevel
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: fd5549e7-b874-41e2-866e-2f58caf6f733
---
# SecureConnectionLevel Property (WMI MSReportServer_ConfigurationSetting)
  Returns the secure connection level specified in the RSReportServer.config file. Read\-only.  
  
## Syntax  
  
```vb#  
Public Dim SecureConnectionLevel As Integer  
```  
  
```c#  
public Integer SecureConnectionLevel;  
```  
  
## Property Values  
 An **Integer** value that represents the secure connection level. The return values indicate that the SSL is either configured or not. A value of greater than or equal to 1 indicates that SSL is turned on. A value of 0 indicates that SSL is turned off.  
  
## Example Code  
 [MSReportServer\_ConfigurationSetting Class](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Class.md)  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  