---
title: InitializeReportServer Method (WMI MSReportServer_ConfigurationSetting)
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
  - InitializeReportServer (WMI MSReportServer_ConfigurationSetting Class)
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: 0304acc2-1fd7-437b-94d9-1c1073dd3ca4
---
# InitializeReportServer Method (WMI MSReportServer_ConfigurationSetting)
  Initializes the specified report service instance.  
  
## Syntax  
  
```vb#  
Public Sub InitializeReportServer(ByVal InstallationID As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```c#  
public void InitializeReportServer(string InstallationID,   
    out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## Parameters  
 *InstallationID*  
 A string used to encrypt the encryption key before it is returned.  
  
 *HRESULT*  
 \[out\] Value indicating whether the call succeeded or failed.  
  
 *ExtendedErrors\[\]*  
 \[out\] A string array containing additional errors returned by the call.  
  
## Return Value  
 Returns an *HRESULT* indicating success or failure of the method call. A value of 0 indicates that the method call was successful. A non\-zero value indicates that an error has occurred.  
  
## Remarks  
 When this method is called, the encryption key that accesses the report server database secure information is encrypted using the public key of the report server identified by *InstallationID*.  
  
 The specified report server’s public key must have previously been written into the report server database.  
  
 The *InitializeReportServer* method must be called against a report server that already has access to the secure information so that it can decrypt the encryption key. The resulting encrypted encryption key is then stored in the report server database.  
  
 If the report server’s [IsInitialized](../Topic/IsInitialized%20Property%20\(WMI%20MSReportServer_ConfigurationSetting\).md) property is set to **true** when the InitializeReportServer method is called, the method returns success without trying to encrypt the encryption key.  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  