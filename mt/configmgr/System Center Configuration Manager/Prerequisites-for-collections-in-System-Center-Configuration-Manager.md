---
title: "Prerequisites for collections in System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: a53e4cf1-518a-4210-9c16-022c4261d2fe
caps.latest.revision: 7
caps.handback.revision: 0
author: barlanmsft
---
# Prerequisites for collections in System Center Configuration Manager
Collections in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] contain only dependencies within the product.  
  
## [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] dependencies  
  
|Dependency|More information|  
|----------------|----------------------|  
|Reporting services point|The reporting services point site system role must be installed before you can run reports for collections. For more information, see [Reporting in System Center Configuration Manager](../System Center Configuration Manager/Reporting-in-System-Center-Configuration-Manager.md).|  
|Specific security permissions must have been granted to manage collections|You must have the following security permissions to manage compliance settings:<br /><br /> - To create and manage collections: **Create**, **Delete**, **Modify**, **Modify Folder**, **Move Object**, **Read** and **Read Resource** for the **Collection** Object.<br /><br /> - To manage collection settings: **Modify Collection Setting** for the **Collection** Object.<br /><br /> The **Modify Folder** permission is required for all collection folders, including the root folder.|  
  
## See Also  
 [Planning for collections in System Center Configuration Manager](../System Center Configuration Manager/Planning-for-collections-in-System-Center-Configuration-Manager.md)