---
title: "Migrate Scripts to VSTA"
ms.custom: na
ms.date: 06/29/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - setup-install
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
caps.latest.revision: 44
manager: mblythe
robots: noindex,nofollow
---
# Migrate Scripts to VSTA
When you upgrade [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)] packages to [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)], [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] migrates the scripts in any Script tasks or Script components to [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[vsprvs](../../Topics/TopicNameContainA/tokens/vsprvs_md.md)] Tools for Applications (VSTA). VSTA is the scripting environment that [!INCLUDE[ssCurrent](../../Topics/TopicNameContainA/tokens/ssCurrent_md.md)] uses. In [!INCLUDE[ssVersion2005](../../Topics/TopicNameContainA/tokens/ssVersion2005_md.md)], the scripting environment for [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] is [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[vsprvs](../../Topics/TopicNameContainA/tokens/vsprvs_md.md)] for Applications (VSA).  
  
 If the scripts in either the Script tasks or Script components reference interfaces, you might have to modify those references before you upgrade the package. Otherwise, the package will not be upgraded or the scripts will not be validated, depending on the upgrade method that you use. To modify these references, replace references to IDTS*xxx*90 interfaces with references to the corresponding IDTS*xxx*100 interfaces.  
  
 For more information about how to migrate scripts and upgrade packages, see [Upgrade Integration Services Packages](../../Topics/TopicNameNotContainA/Upgrade-Integration-Services-Packages.md).  
  
## Understanding Migration Failures  
 When you migrate the scripts, the migration can fail because of one of the following reasons:  
  
-   The entry point for the VSA script was renamed.  
  
     The entry point specifies the method in the **ScriptMain** class in the VSTA project that the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] runtime calls as the entry point into the Script task code. The **ScriptMain** class is the default class that the script templates generate.  
  
-   There is no entry point or there are multiple entry points in the VSA script.  
  
-   Assembly references could not be added.  
  
-   The **ScriptMain** class was modified to inherit from other classes in addition to the **ScriptObjectModelSSIS** class. [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[dnprdnshort](../../Topics/TopicNameContainA/tokens/dnprdnshort_md.md)] does not support multiple inheritance.  
  
 You cannot convert a VSA script that uses [!INCLUDE[vbprvblong](../../Topics/TopicNameNotContainA/tokens/vbprvblong_md.md)] to a VSTA script that uses [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[csharp_orcas_long](../../Topics/TopicNameNotContainA/tokens/csharp_orcas_long_md.md)]. However, you can create a new VSTA script that uses [!INCLUDE[msCoName](../../Topics/TopicNameContainA/tokens/msCoName_md.md)] [!INCLUDE[csharp_orcas_long](../../Topics/TopicNameNotContainA/tokens/csharp_orcas_long_md.md)]. For more information, see [Coding and Debugging the Script Task](assetId:///687c262f-fcab-42e8-92ae-e956f3d92d69) and [Coding and Debugging the Script Component](assetId:///c3913c15-66aa-4b61-89b5-68488fa5f0a4).  
  
## See Also  
 [Extending Packages with Scripting](assetId:///67fe18ef-f3aa-41d4-9b9d-5defd4618c4b)