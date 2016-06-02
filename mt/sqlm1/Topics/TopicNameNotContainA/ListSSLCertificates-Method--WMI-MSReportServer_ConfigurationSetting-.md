---
title: ListSSLCertificates Method (WMI MSReportServer_ConfigurationSetting)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - reporting-services-sharepoint
  - reporting-services-native
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 88cd0936-b202-4ab8-90f2-d9c3f66d37f4
---
# ListSSLCertificates Method (WMI MSReportServer_ConfigurationSetting)
  Returns a list of certificates on the report server computer.  
  
## Syntax  
  
```vb#  
Public Sub CreateSSLCertificateBinding (ByRef CertificateHash() as String, _  
    ByRef CertName() as String, ByRef HostName() as String, ByRef Length as Int32, _   
    ByRef HRESULT as Int32)  
```  
  
```c#  
public void ListSSLCertificates(out string[] CertificateHash,   
    out string[] CertName, out string[] Hostname, out Int32 length,   
    out Int32 HRESULT);  
```  
  
## Parameters  
 *CertificateHash\[\]*  
 \[out\] The certificate hashes.  
  
 *CertName\[\]*  
 \[out\] Names of the certificate.  
  
 *HostName\[\]*  
 \[out\] The host names for the certificates.  
  
 *Length*  
 \[out\] Represents the length of the *CertificateHash*, *CertName* and *HostName* arrays.  
  
 *HRESULT*  
 \[out\] Value indicating whether the call succeeded or failed.  
  
## Return Value  
 Returns an *HRESULT* indicating success or failure of the method call. A value of 0 indicates that the method call was successful; an error code indicates the call was not successful.  
  
## Remarks  
  
## Requirements  
 **Namespace:** [!INCLUDE[ssRSWMInmspcA](../../Token\Other/ssRSWMInmspcA_md.md)]  
  
## See Also  
 [MSReportServer_ConfigurationSetting Members](../../Topics\TopicNameNotContainA/MSReportServer_ConfigurationSetting-Members.md)  
  
  