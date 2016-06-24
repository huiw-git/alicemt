---
title: General Page
H1: na
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d695690a-923b-4036-945e-7621e8651deb
---
# General Page
  Use the **General** page of the **Integration Services Designers** page in the **Options** dialog box to specify the options for loading, displaying, and upgrading packages.  
  
 To open the **General** page, in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/includes/ssBIDevStudioFull_md.md)], on the **Tools** menu, click **Options**, expand **Business Intelligence Designers**, and select **Integration Services Designers**.  
  
## Options  
 **Check digital signature when loading a package**  
 Select to have [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/includes/ssISnoversion_md.md)] check the digital signature when loading a package. [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/includes/ssISnoversion_md.md)] will only check whether the digital signature is present, is valid, and is from a trusted source. [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/includes/ssISnoversion_md.md)] will not check whether the package has been changed since the package was signed.  
  
 If you set the **BlockedSignatureStates** registry value, this registry value overrides the **Check digital signature when loading a package** option. For more information, see [Implement a Signing Policy by Setting a Registry Value](../../Topics/TopicNameContainA/Implement-a-Signing-Policy-by-Setting-a-Registry-Value.md).  
  
 For more information about digital certificates and packages, see [Identify the Source of Packages with Digital Signatures](../../Topics/TopicNameNotContainA/Identify-the-Source-of-Packages-with-Digital-Signatures.md).  
  
 **Show warning if package is unsigned**  
 Select to display a warning when loading a package that is not signed.  
  
 **Show precedence constraint labels**  
 Select which label—Success, Failure, or Completion—to display on precedence constraints when viewing packages in [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/includes/ssBIDevStudioFull_md.md)].  
  
 **Scripting language**  
 Select the default scripting language for new Script tasks and Script components.  
  
 **Update connection strings to use new provider names**  
 When opening or upgrading [!INCLUDE[ssISversion2005](../../Topics/TopicNameNotContainA/includes/ssISversion2005_md.md)] packages, update connection strings to use the names for the following providers, for the current release of [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)][!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/includes/ssISnoversion_md.md)]:  
  
-   [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/includes/ssASnoversion_md.md)] OLE DB provider  
  
-   [!INCLUDE[ssNoVersion](../../Topics/TopicNameContainA/includes/ssNoVersion_md.md)] Native Client  
  
 The [!INCLUDE[ssIS](../../Topics/TopicNameContainA/includes/ssIS_md.md)] Package Upgrade Wizard updates only connection strings that are stored in connection managers. The wizard does not update connection strings that are constructed dynamically by using the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/includes/ssISnoversion_md.md)] expression language, or by using code in a Script task.  
  
 **Create new package ID**  
 When upgrading [!INCLUDE[ssISversion2005](../../Topics/TopicNameNotContainA/includes/ssISversion2005_md.md)] packages, create new package IDs for the upgraded versions of the packages.  
  
## See Also  
 [Security Overview &#40;Integration Services&#41;](../../Topics/TopicNameNotContainA/Security-Overview--Integration-Services-.md)   
 [Extending Packages with Scripting](../Topic/Extending%20Packages%20with%20Scripting.md)  
  
  