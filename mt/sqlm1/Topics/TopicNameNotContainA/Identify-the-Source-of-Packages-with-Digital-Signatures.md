---
title: Identify the Source of Packages with Digital Signatures
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a433fbef-1853-4740-9d5e-8a32bc4ffbb2
---
# Identify the Source of Packages with Digital Signatures
  An [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] package can be signed with a digital certificate to identify its source. After a package has been signed with a digital certificate, you can have [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] check the digital signature before loading the package. To have [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] check the signature, you set an option in either [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] or in the **dtexec** utility \(dtexec.exe\), or set an optional registry value.  
  
## Signing a Package with a Digital Certificate  
 Before you can sign a package with a digital certificate, you first have to obtain or create the certificate. After you have the certificate, you can then use this certificate to sign the package. For more information about how to obtain a certificate and sign a package with that certificate, see [Sign a Package by Using a Digital Certificate](../../Topics\TopicNameContainA/Sign-a-Package-by-Using-a-Digital-Certificate.md).  
  
## Setting an Option to Check the Package Signature  
 Both [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] and the **dtexec** utility have an option that configures [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] to check the digital signature of a signed package. Whether you use [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] or the **dtexec** utility depends on whether you want to check all packages or just specific ones:  
  
-   To check the digital signature of all packages before loading the packages at design time, set the **Check digital signature when loading a package** option in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. This option is a global setting for all packages in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)]. For more information, see [General Page](../../Topics\TopicNameNotContainA/General-Page.md).  
  
-   To check the digital signature of an individual package, specify the **\/VerifyS\[igned\]** option when you use the **dtexec** utility to run the package. For more information, see [dtexec Utility](../../Topics\TopicNameNotContainA/dtexec-Utility.md).  
  
## Setting a Registry Value to Check the Package Signature  
 [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] also supports an optional registry value, **BlockedSignatureStates**, that you can use to manage an organization's policy for loading signed and unsigned packages. The registry value can prevent packages from loading if the packages are unsigned, or have invalid or untrusted signatures. For more information about how to set this registry value, see [Implement a Signing Policy by Setting a Registry Value](../../Topics\TopicNameContainA/Implement-a-Signing-Policy-by-Setting-a-Registry-Value.md).  
  
> [!NOTE]  
>  The optional **BlockedSignatureStates** registry value can specify a setting that is more restrictive than the digital signature option set in [!INCLUDE[ssBIDevStudioFull](../../Token\Other/ssBIDevStudioFull_md.md)] or at the **dtexec** command line. In this situation, the more restrictive registry setting overrides the other settings.  
  
## See Also  
 [Integration Services &#40;SSIS&#41; Packages](../Topic/Integration%20Services%20\(SSIS\)%20Packages.md)   
 [Security Overview &#40;Integration Services&#41;](../Topic/Security%20Overview%20\(Integration%20Services\).md)  
  
  