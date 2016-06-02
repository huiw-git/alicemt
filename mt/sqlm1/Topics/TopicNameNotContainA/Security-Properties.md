---
title: Security Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2fc7fe10-0cbb-49ac-aa8c-8ec3f7a7705f
---
# Security Properties
  [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] supports the security server properties listed in the following table. For more information about additional server properties and how to set them, see [Server Properties in Analysis Services](../../Topics\TopicNameNotContainA/Server-Properties-in-Analysis-Services.md).  
  
 **Applies to:** Multidimensional and Tabular server mode  
  
## Properties  
 **RequireClientAuthentication**  
 A Boolean property that indicates whether client authentication is required.  
  
 The default value for this property is True, which indicates that client authentication is required.  
  
 **SecurityPackageList**  
 A string property that contains a comma\-separated list of SSPI packages used by server for client authentication.  
  
 **DisableClientImpersonation**  
 A Boolean property that indicates whether client impersonation \(for example, from stored procedures\) is disabled.  
  
 The default value for this property is False, which indicates that client impersonation is enabled.  
  
 **BuiltinAdminsAreServerAdmins**  
 A Boolean property that indicates whether members of the local machine administrators group are [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] administrators.  
  
 **ServiceAccountIsServerAdmin**  
 A Boolean property that indicates whether the service account is a server administrator.  
  
 The default value for this property is True, which indicates that the service account is a server administrator.  
  
 **ErrorMessageMode**  
 An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] support.  
  
 **DataProtection\\ RequiredProtectionLevel**  
 A signed 32\-bit integer property that defines the required protection level for all client requests. This property has one of the values listed in the following table.  
  
|Value|Description|  
|-----------|-----------------|  
|*0*|None, clear text allowed.|  
|*1*|\(Default\) Encryption required, no clear\-text logging.|  
|*2*|Clear\-text requests allowed but only with signatures \(weaker protection than encryption\).|  
  
 **AdministrativeDataProtection\\ RequiredProtectionLevel**  
 An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] support.  
  
## See Also  
 [Server Properties in Analysis Services](../../Topics\TopicNameNotContainA/Server-Properties-in-Analysis-Services.md)   
 [Determine the Server Mode of an Analysis Services Instance](../../Topics\TopicNameNotContainA/Determine-the-Server-Mode-of-an-Analysis-Services-Instance.md)  
  
  