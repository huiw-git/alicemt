---
title: "Copy Project Items"
ms.custom: na
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: na
ms.suite: na
ms.technology: 
  - integration-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1606c54d-20f9-49f3-a4ef-caad83a772aa
caps.latest.revision: 16
manager: jhubbard
---
# Copy Project Items
This topic describes how to copy objects within an [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] project or between [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] projects. You can also copy objects between the other types of [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)] projects, [!INCLUDE[ssRSnoversion](../../Topics/TopicNameContainA/tokens/ssRSnoversion_md.md)] and [!INCLUDE[ssASnoversion](../../Topics/TopicNameContainA/tokens/ssASnoversion_md.md)]. To copy between projects, the project must be part of the same [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)] solution. For more information, see [Integration Services (SSIS) Projects](../../Topics/TopicNameNotContainA/Integration-Services--SSIS--Projects.md).  
  
### To copy project level items  
  
1.  In [!INCLUDE[ssBIDevStudioFull](../../Topics/TopicNameContainA/tokens/ssBIDevStudioFull_md.md)], open the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] project or solution that you want to work with.  
  
2.  Expand the project and item folder to copy from.  
  
3.  Right-click the item and click **Copy**.  
  
4.  Right-click the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] project to copy to and click **Paste**.  
  
     The items are automatically copied to the correct folder. If you copy items to the [!INCLUDE[ssISnoversion](../../Topics/TopicNameContainA/tokens/ssISnoversion_md.md)] project that are not packages, the items are copied to the **Miscellaneous** folder.  
  
## See Also  
 [Integration Services (SSIS) Packages](../../Topics/TopicNameNotContainA/Integration-Services--SSIS--Packages.md)   
 [Copy Package Objects](../../Topics/TopicNameNotContainA/Copy-Package-Objects.md)