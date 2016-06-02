---
title: DeleteEncryptedInformation Method (WMI MSReportServer_ConfigurationSetting)
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
  - DeleteEncryptedInformation (WMI MSReportServer_ConfigurationSetting Class)
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: c14ed187-bdd9-4304-88e3-72072f03c21b
---
# DeleteEncryptedInformation Method (WMI MSReportServer_ConfigurationSetting)
  Deletes the encrypted information from the report server database.  
  
## Syntax  
  
```vb#  
Public Sub DeleteEncryptedInformation(ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```c#  
public void DeleteEncryptedInformation(out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## Parameters  
 *HRESULT*  
 \[out\] Value indicating whether the call succeeded or failed.  
  
 *ExtendedErrors\[\]*  
 \[out\] A string array containing additional errors returned by the call.  
  
## Return Value  
 Returns an *HRESULT* indicating success or failure of the method call. A value of 0 indicates that the method call was successful. A non\-zero value indicates that an error has occurred.  
  
## Remarks  
 When this method is invoked, the following data is deleted:  
  
-   Data source information that is encrypted, including user name and password.  
  
-   Subscription data that is encrypted using the delivery extension interfaces.  
  
-   All the information from the keys table in the report server database.  
  
 After this method is invoked, the user must initialize each computer that uses the report server database.  
  
 Calling the DeleteEncryptedInformation method does not affect the report server configuration file.  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  