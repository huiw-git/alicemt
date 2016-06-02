---
title: UnattendedExecutionAccount Property (WMI MSReportServer_ConfigurationSetting)
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
  - UnattendedExecutionAccount
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: ab5203ba-c01e-4020-8619-ee290cf9da07
---
# UnattendedExecutionAccount Property (WMI MSReportServer_ConfigurationSetting)
  Returns the user account that the report server impersonates when running reports unattended. Read\-only.  
  
## Syntax  
  
```vb#  
Public Dim UnattendedExecutionAccount As String  
```  
  
```c#  
public string UnattendedExecutionAccount;  
```  
  
## Property Values  
 A **String** object that represents the account name.  
  
## Example Code  
 [MSReportServer\_ConfigurationSetting Class](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Class.md)  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  