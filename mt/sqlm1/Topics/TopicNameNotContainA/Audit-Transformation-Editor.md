---
title: Audit Transformation Editor
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 32786a34-5870-4fde-83c7-ec74d62404b8
---
# Audit Transformation Editor
  The Audit transformation enables the data flow in a package to include data about the environment in which the package runs. For example, the name of the package, computer, and operator can be added to the data flow. [!INCLUDE[ssISnoversion](../../Token\Other/ssISnoversion_md.md)] includes system variables that provide this information.  
  
 To learn more about the Audit transformation, see [Audit Transformation](../../Topics\TopicNameNotContainA/Audit-Transformation.md).  
  
## Options  
 **Output column name**  
 Provide the name for a new output column that will contain the audit information.  
  
 **Audit type**  
 Select an available system variable to supply the audit information.  
  
|Value|Description|  
|-----------|-----------------|  
|**Execution instance GUID**|Insert the GUID that uniquely identifies the execution instance of the package.|  
|**Package ID**|Insert the GUID that uniquely identifies the package.|  
|**Package name**|Insert the package name.|  
|**Version ID**|Insert the GUID that uniquely identifies the version of the package.|  
|**Execution start time**|Insert the time at which package execution started.|  
|**Machine name**|Insert the name of the computer on which the package was launched.|  
|**User name**|Insert the login name of the user who launched the package.|  
|**Task name**|Insert the name of the Data Flow task with which the Audit transformation is associated.|  
|**Task ID**|Insert the GUID that uniquely identifies the Data Flow task with which the Audit transformation is associated.|  
  
## See Also  
 [Integration Services Error and Message Reference](../../Topics\TopicNameNotContainA/Integration-Services-Error-and-Message-Reference.md)  
  
  