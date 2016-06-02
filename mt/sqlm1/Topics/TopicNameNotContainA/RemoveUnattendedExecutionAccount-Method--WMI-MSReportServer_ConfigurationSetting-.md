---
title: RemoveUnattendedExecutionAccount Method (WMI MSReportServer_ConfigurationSetting)
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
  - RemoveUnattendedExecutionAccount (WMI MSReportServer_ConfigurationSetting Class)
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: 77e371c1-7c26-44f9-9119-7c8dc838db32
---
# RemoveUnattendedExecutionAccount Method (WMI MSReportServer_ConfigurationSetting)
  Deletes the unattended execution account entry from the report server configuration file.  
  
## Syntax  
  
```vb#  
Public Sub RemoveUnattendedExecutionAccount(ByRef HRESULT as Int32)  
```  
  
```c#  
public void RemoveUnattendedExecutionAccount (out Int32 HRESULT);  
```  
  
## Parameters  
 *HRESULT*  
 \[out\] Value indicating whether the call succeeded or failed.  
  
## Return Value  
 Returns an *HRESULT* indicating success or failure of the method call. A value of 0 indicates that the method call was successful. A non\-zero value indicates that an error has occurred.  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  