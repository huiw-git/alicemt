---
title: "DatabaseLogonType Property (WMI MSReportServer_ConfigurationSetting)"
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
  - DatabaseLogonType
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: 6b592582-4c35-4029-ab86-982fff47d8d6
caps.latest.revision: 25
caps.handback.revision: 0
manager: mblythe
---
# DatabaseLogonType Property (WMI MSReportServer_ConfigurationSetting)
Specifies whether the report server uses a [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] Windows service account, a Windows user account, or a [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login to access the report server database. Read-only.  
  
## Syntax  
  
```vb#  
Public Dim DatabaseLogonType As Integer  
```  
  
```c#  
public int DatabaseLogonType;  
```  
  
## Property Values  
 An **integer** object that represents the login type.  
  
## Example Code  
 [MSReportServer_ConfigurationSetting Class](../../Topics/TopicNameNotContainA/MSReportServer_ConfigurationSetting-Class.md)  
  
## Remarks  
 Values are:  
  
-   0 for Windows login  
  
-   1 for [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login  
  
-   2 to log in as a service  
  
 If you specify 0 (Windows), you must set the value in the [DatabaseLogonAccount](../../Topics/TopicNameNotContainA/DatabaseLogonAccount-Property--WMI-MSReportServer_ConfigurationSetting-.md) property to a corresponding a valid Windows user account.  
  
 If you specify 1 (SQL Server), make sure the value of the [DatabaseLogonAccount](../../Topics/TopicNameNotContainA/DatabaseLogonAccount-Property--WMI-MSReportServer_ConfigurationSetting-.md) corresponds to a valid [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/tokens/ssNoVersion_md.md)] login.  
  
 If you specify 2 (Windows service), the report server uses an [!INCLUDE[vstecasp](../../Topics/TopicNameContainA/tokens/vstecasp_md.md)] account and the Windows service account to access the report server database. The **DatabaseLogonAccount** property is ignored.  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Topics/TopicNameNotContainA/tokens/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics/TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)