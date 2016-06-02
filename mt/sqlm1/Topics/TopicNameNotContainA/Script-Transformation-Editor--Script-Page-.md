---
title: Script Transformation Editor (Script Page)
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
---
# Script Transformation Editor (Script Page)
  Use the **Script** tab of the **Script Transformation Editor** dialog box to specify a script and related properties.  
  
 To learn more about the Script component, see [Script Component](../../Topics\TopicNameNotContainA/Script-Component.md) and [Configuring the Script Component in the Script Component Editor](../Topic/Configuring%20the%20Script%20Component%20in%20the%20Script%20Component%20Editor.md). To learn about programming the Script component, see [Extending the Data Flow with the Script Component](../Topic/Extending%20the%20Data%20Flow%20with%20the%20Script%20Component.md).  
  
## Options  
 **Properties**  
 View and modify the properties of the Script transformation. Many of the properties displayed are read\-only. You can modify the following properties:  
  
|Value|Description|  
|-----------|-----------------|  
|**Description**|Describe the script transformation in terms of its purpose.|  
|**LocaleID**|Specify the locale to provide region\-specific information for ordering, and for date and time conversion.|  
|**Name**|Type a descriptive name for the component.|  
|**ValidateExternalMetadata**|Indicate whether the Script transformation validates column metadata against external data sources at design time. A value of **false** delays validation until the time of execution.|  
|**ReadOnlyVariables**|Type a comma\-separated list of variables for read\-only access by the Script transformation.<br /><br /> Note: Variable names are case\-sensitive.|  
|**ReadWriteVariables**|Type a comma\-separated list of variables for read\/write access by the Script transformation.<br /><br /> Note: Variable names are case\-sensitive.|  
|**ScriptLanguage**|Select the script language to be used by the Script component.<br /><br /> To set the default script language for Script components and Script tasks, use the **Scripting language** option on the **General** page of the **Options** dialog box. For more information, see [General Page](../../Topics\TopicNameNotContainA/General-Page.md).|  
|**UserComponentTypeName**|Specifies the [ScriptComponentHost](assetId:///T:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost) class and the **Microsoft.SqlServer.TxScript** assembly that support the [!INCLUDE[ssNoVersion](../../Token\Other/ssNoVersion_md.md)] infrastructure.|  
  
 **Edit Script**  
 Use [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] [!INCLUDE[vsprvs](../../Token\Other/vsprvs_md.md)] Tools for Applications \(VSTA\) to create or modify a script.  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)   
 [Select Script Component Type](../../Topics\TopicNameNotContainA/Select-Script-Component-Type.md)   
 [Script Transformation Editor &#40;Input Columns Page&#41;](../Topic/Script%20Transformation%20Editor%20\(Input%20Columns%20Page\).md)   
 [Script Transformation Editor &#40;Inputs and Outputs Page&#41;](../Topic/Script%20Transformation%20Editor%20\(Inputs%20and%20Outputs%20Page\).md)   
 [Script Transformation Editor &#40;Connection Managers Page&#41;](../Topic/Script%20Transformation%20Editor%20\(Connection%20Managers%20Page\).md)   
 [Additional Script Component Examples](../Topic/Additional%20Script%20Component%20Examples.md)  
  
  