---
title: Register Database Assembly Dialog Box (Analysis Services - Multidimensional Data)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0c07cc87-fc94-456f-b878-7b23e39772b9
---
# Register Database Assembly Dialog Box (Analysis Services - Multidimensional Data)
  Use the **Register Server Assembly** dialog box in [!INCLUDE[ssManStudioFull](../../Token\Other/ssManStudioFull_md.md)] to set the properties of an assembly reference in an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] database. You can display the **Register Server Assembly** dialog box by right\-clicking the Assemblies folder of an [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance or database in **Object Explorer** and selecting **New assembly**.  
  
## Options  
  
|Term|Definition|  
|----------|----------------|  
|**Type**|Select the type of the assembly reference. The following values are available:<br /><br /> **.NET Assembly**:<br />                      The assembly reference refers to a [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] .NET Framework assembly.<br /><br /> **COM DLL**:<br />                      The assembly reference refers to a COM library.<br /><br /> **\*\* Security Note \*\*** COM assemblies might pose a security risk. Due to this risk and other considerations, COM assemblies were deprecated in [!INCLUDE[ssASversion10](../../Token\Other/ssASversion10_md.md)]. COM assemblies might not be supported in future releases.|  
|**File name**|Type the full path and file name of the .NET assembly or COM library.|  
|**...**|Click to display the **Open** dialog box and select the full path and file name of the .NET assembly or COM library.|  
|**Assembly name**|Type to set the name of the assembly reference.<br /><br /> Note: Changing this value does not change the name of the assembly referred to by the assembly reference, but instead changes the name used the by the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] instance or database when referring to the assembly reference.|  
|**Include debug information**|Select this option to include debug information, if available, for the .NET assembly or COM library.|  
|**Create Timestamp**|Displays the date and time the assembly reference was created.|  
|**Last Schema Update**|Displays the date and time the metadata for the assembly reference was last updated.|  
|**Source**|Displays the source of the assembly reference. This property typically contains the full path and file name of the assembly referred to by the assembly reference.|  
|**Safe**|Select this option to use this permission set for the assembly reference. If this option is selected, the assembly is allowed only internal computation and local data access. Code executed by an assembly with this option cannot access external system resources such as files, the network, environment variables, or the registry.<br /><br /> **\*\* Security Note \*\*** This option is the recommended permission setting for assemblies that perform computation and data management tasks without accessing resources outside [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. This option represents the most restrictive permission set.|  
|**External access**|Select this option to use this permission set for the assembly reference. If this option is selected, the assembly is allowed only internal computation and local data access. Code executed by an assembly with this permission set has the ability to access external system resources such as files, networks, environmental variables, and the registry.<br /><br /> **\*\* Security Note \*\*** This option is recommended for assemblies that access resources outside [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. Assemblies using this option, by default, execute using the security credentials of the service account. It is possible for code within this assembly to explicitly impersonate the caller’s [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] Windows Authentication security context. Because the default is to execute as the service account, permission to execute assemblies with this option should only be given to roles trusted to run as the service account. This option represents a less restrictive permission set than **Safe**, but more restrictive than **Unrestricted**.|  
|**Unrestricted**|Select this option to use this permission set for the assembly reference. If this option is selected, the assembly has unrestricted access to resources, both inside and outside. Code executing from within an assembly with this option can call unmanaged code.<br /><br /> **\*\* Security Note \*\*** This option is not recommended unless the assembly requires unrestricted access. From a security perspective, this option is identical to **External access**. However, assemblies using the **External access** option provide various reliability and robustness protections that are not included in assemblies using this option. Specifying this option allows the code in the assembly to perform illegal operations against the process space and hence can potentially compromise the robustness and scalability of [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. This option represents the least restrictive permission set, and should be used with caution.|  
|**Use a specific user name and password**|Select this option to have the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] object use the security credentials of a specified user account.|  
|**User name**|Type the domain and name of the user account to be used by the selected [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] object. The domain and name of the user account uses the following format:<br /><br /> *\<Domain name\>* **\\** *\<User account name\>*<br /><br /> Note: This option is enabled only if **Use a specific name and password** is selected.|  
|**Password**|Type the domain and name of the user account to be used by the selected [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] object.|  
|**Use the service account**|Select this option to have the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] object use the security credentials associated with the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] service that manages the object.|  
|**Use the credentials of the current user**|Select this option to have the [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] object use the security credentials of the current user.|  
|**Default**|Select this option to use the default user account for [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)]. Selecting this option is equivalent to selecting the **Use the credentials of the current user** option.|  
|**Description**|Type to set the description of the assembly reference.|  
  
## See Also  
 [Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](../Topic/Analysis%20Services%20Designers%20and%20Dialog%20Boxes%20\(Multidimensional%20Data\).md)   
 [Multidimensional Model Assemblies Management](../../Topics\TopicNameNotContainA/Multidimensional-Model-Assemblies-Management.md)  
  
  