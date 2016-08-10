---
title: "UnattendedExecutionAccount Property (WMI MSReportServer_ConfigurationSetting)"
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
apiname: 
  - UnattendedExecutionAccount
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: ab5203ba-c01e-4020-8619-ee290cf9da07
caps.latest.revision: 18
caps.handback.revision: 0
manager: mblythe
---
# UnattendedExecutionAccount Property (WMI MSReportServer_ConfigurationSetting)
Returns the user account that the report server impersonates when running reports unattended. Read-only.  
  
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
 [MSReportServer_ConfigurationSetting Class](../../Topics/TopicNameNotContainA/MSReportServer_ConfigurationSetting-Class.md)  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Topics/TopicNameNotContainA/tokens/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics/TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)