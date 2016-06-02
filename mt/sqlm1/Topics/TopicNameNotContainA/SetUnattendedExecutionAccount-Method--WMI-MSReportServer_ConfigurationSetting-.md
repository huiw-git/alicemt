---
title: SetUnattendedExecutionAccount Method (WMI MSReportServer_ConfigurationSetting)
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
  - SetUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: 1ba6be6f-b05c-4ea0-af98-cd0780290b70
---
# SetUnattendedExecutionAccount Method (WMI MSReportServer_ConfigurationSetting)
  Specifies the account used to execute reports unattended.  
  
## Syntax  
  
```vb#  
Public Sub SetUnattendedExecutionAccount(UserName as String, _  
    Password as String, ByRef HRESULT as Int32)  
```  
  
```c#  
public void SetUnattendedExecutionAccount (string UserName,   
    string Password, out Int32 HRESULT);  
```  
  
## Parameters  
 *UserName*  
 A Windows account to be used for unattended executions.  
  
 *Password*  
 The password for the specified account.  
  
 *HRESULT*  
 \[out\] Value indicating whether the call succeeded or failed.  
  
## Return Value  
 Returns an *HRESULT* indicating success or failure of the method call. A value of 0 indicates that the method call was successful. A non\-zero value indicates that an error has occurred.  
  
## Remarks  
 The SetUnattendedExecutionAccount method does not verify whether the report server can log in as the specified user.  
  
 It is not possible to use the SetUnattendedExecutionAccount method to run unattended executions in the context of the report server Windows service.  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  