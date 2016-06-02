---
title: Lock Manager Properties
ms.custom: na
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - analysis-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 15fe9ead-825b-4ac3-9191-7a07caa2861b
---
# Lock Manager Properties
  [!INCLUDE[ssASnoversion](../../Token\Other/ssASnoversion_md.md)] supports the lock manager server properties listed in the following table. For more information about additional server properties and how to set them, see [Server Properties in Analysis Services](../../Topics\TopicNameNotContainA/Server-Properties-in-Analysis-Services.md).  
  
 **Applies to:** Multidimensional and Tabular server mode  
  
## Properties  
 **DefaultLockTimeoutMS**  
 A signed 32\-bit integer property that defines default lock timeout in milliseconds for internal lock requests.  
  
 The default value for this property is \-1, which indicates there is no timeout for internal lock requests.  
  
 **LockWaitGranularityMS**  
 An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] support.  
  
 **DeadlockDetectionGranularityMS**  
 An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../Token\Other/msCoName_md.md)] support.  
  
## See Also  
 [Server Properties in Analysis Services](../../Topics\TopicNameNotContainA/Server-Properties-in-Analysis-Services.md)   
 [Determine the Server Mode of an Analysis Services Instance](../../Topics\TopicNameNotContainA/Determine-the-Server-Mode-of-an-Analysis-Services-Instance.md)  
  
  