---
title: BackupEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)
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
  - BackupEncryptionKey Method (WMI MSReportServer_ConfigurationSetting Class)
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: da1d5dae-2517-448e-96fb-5379c93222ea
---
# BackupEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)
  Backs up the encryption key for the specified report server instance. The encryption key is stored encrypted with a password.  
  
## Syntax  
  
```vb#  
Public Sub BackupEncryptionKey(Password as String, _  
    ByRef KeyFile() as Integer, ByRef Length as Int32, _  
    ByRef HRESULT as Int32, ByRef ExtendedErrors() as String)  
  
```  
  
```c#  
public void BackupEncryptionKey(string Password, out Byte[] KeyFile,   
    out Int32 Length, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## Parameters  
 *Password*  
 A string used to encrypt the encryption key before it is returned.  
  
 *KeyFile\[\]*  
 \[out\] An array containing the encrypted encryption key.  
  
 *Length*  
 \[out\] The length of the array returned by the method.  
  
 *HRESULT*  
 \[out\] Value indicating whether the call succeeded or failed.  
  
 *ExtendedErrors\[\]*  
 \[out\] A string array containing additional errors returned by the call.  
  
## Return Value  
 Returns an *HRESULT* indicating success or failure of the method call. A value of 0 indicates that the method call was successful. A non\-zero value indicates that an error has occurred.  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  