---
title: "Update and retire applications with System Center Configuration Manager"
ms.custom: na
ms.date: 2016-05-26
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 68ac8a07-8e54-4a3c-91e3-e50dc1cabf5d
caps.latest.revision: 9
author: barlanmsft
---
# Update and retire applications with System Center Configuration Manager
After a time, you will likely want to make changes to an application, uninstall it, or replace an already deployed application with a new application. [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] includes the following capabilities to help you with this:  
  
-   **Revise applications** - When you make changes to an application or deployment type, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] maintains a history of these changes. You can revert the application to a previous revision at any time. You can also view its properties, restore a previous revision of an application, or delete an old revision.  
  
     For more information, see [Application revisions](../System Center Configuration Manager/How-to-revise-and-supersede-applications-in-System-Center-Configuration-Manager.md#BKMK_Rev).  
  
-   **Supersede applications** - Lets you upgrade or replace existing applications by using a supersedence relationship. When you supersede an application, you can specify a new deployment type to replace the deployment type of the superseded application and also configure whether to upgrade or uninstall the superseded application before the superseding application is installed.  
  
     For more information, see [Application supersedence](../System Center Configuration Manager/How-to-revise-and-supersede-applications-in-System-Center-Configuration-Manager.md#BKMK_Super).  
  
-   **Uninstall applications** - [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] makes uninstalling an application easy. This can be accomplished silently, without any intervention from the end user.  
  
     For more information, see [How to uninstall applications with System Center Configuration Manager](../System Center Configuration Manager/How-to-uninstall-applications-with-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Deploy and manage applications with System Center Configuration Manager](../System Center Configuration Manager/Deploy-and-manage-applications-with-System-Center-Configuration-Manager.md)