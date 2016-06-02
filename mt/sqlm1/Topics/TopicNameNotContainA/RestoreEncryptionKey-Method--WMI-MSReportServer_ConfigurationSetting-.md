---
title: RestoreEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)
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
  - RestoreEncryptionKey (WMI MSReportServer_ConfigurationSetting Class)
apilocation: 
  - reportingservices.mof
apitype: MOFDef
ms.assetid: 37e949f5-15af-4858-848a-f482ee94fcd9
---
# RestoreEncryptionKey Method (WMI MSReportServer_ConfigurationSetting)
  Reapplies the specified encryption key to the report server database.  
  
## Syntax  
  
```vb#  
Public Sub RestoreEncryptionKey(ByRef KeyFile() As Integer, _  
    ByRef Length As Int32, ByVal Password As String, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```c#  
public void RestoreEncryptionKey(out Byte[] KeyFile, out Int32 Length,   
            string Password, out Int32 HRESULT, out string[] ExtendedErrors);  
```  
  
## Parameters  
 *KeyFile\[\]*  
 \[out\] An array containing the encrypted encryption key.  
  
 *Length*  
 \[out\] The length of the array returned by the method.  
  
 *Password*  
 A string used to encrypt the encryption key.  
  
 *HRESULT*  
 \[out\] Value indicating whether the call succeeded or failed.  
  
 *ExtendedErrors\[\]*  
 \[out\] A string array containing additional errors returned by the call.  
  
## Return Value  
 Returns an *HRESULT* indicating success or failure of the method call. A value of 0 indicates that the method call was successful. A non\-zero value indicates that an error has occurred.  
  
## Remarks  
 If an entry already exists for the report server in the report server database, it is deleted. The new entry is then created using the specified encryption key and the report server’s public key.  
  
 The method is most effective when called after the [DeleteEncryptionKey](../Topic/DeleteEncryptionKey%20Method%20\(WMI%20MSReportServer_ConfigurationSetting\).md) method, which clears the list of encryption keys.  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  