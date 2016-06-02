---
title: Assembly Properties Dialog Box (Analysis Services - Multidimensional Data)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da1174d6-d82b-4337-ac19-7368dbd95a84
---
# Assembly Properties Dialog Box (Analysis Services - Multidimensional Data)
  Use the **Assembly Properties** dialog box in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] to set the properties of an assembly reference in an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database. You can display the **Assembly Properties** dialog box by right\-clicking an assembly in **Object Explorer** and selecting **Properties**.  
  
## Options  
  
|Term|Definition|  
|----------|----------------|  
|**Name**|Type to change the name of the assembly reference.<br /><br /> **Note:** Changing this value does not change the name of the assembly referred to by the assembly reference, but instead changes the name used the by the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance or database when referring to the assembly reference.|  
|**ID**|Displays the identifier of the assembly referred to by the assembly reference.|  
|**Description**|Type to change the description of the assembly reference.|  
|**Create Timestamp**|Displays the date and time the assembly reference was created.|  
|**Last Schema Update**|Displays the date and time the metadata for the assembly reference was last updated.|  
|**Type**|Displays the type of the assembly reference. The following values are displayed:<br /><br /> **.NET Assembly** The assembly reference refers to a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] .NET Framework assembly.<br /><br /> **COM DLL** The assembly reference refers to a COM library.|  
|**Source**|Displays the source of the assembly reference. This property typically contains the full path and file name of the assembly referred to by the assembly reference.|  
|**Permission Set**|Select the permission set used to determine access to the assembly reference. For more information about the available values for this property, see [PermissionSet](assetId:///P:Microsoft.AnalysisServices.ClrAssembly.PermissionSet).|  
|**Impersonation Info**|Select the impersonation information to use when accessing the assembly reference. For more information about the available values for this property, see [ImpersonationInfo Element &#40;ASSL&#41;](../Topic/ImpersonationInfo%20Element%20\(ASSL\).md)|  
  
## See Also  
 [Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](../Topic/Analysis%20Services%20Designers%20and%20Dialog%20Boxes%20\(Multidimensional%20Data\).md)   
 [Multidimensional Model Assemblies Management](../../Topics\TopicNameNotContainA/Multidimensional-Model-Assemblies-Management.md)  
  
  