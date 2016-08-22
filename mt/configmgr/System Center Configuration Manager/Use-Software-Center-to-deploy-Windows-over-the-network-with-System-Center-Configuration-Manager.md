---
title: "Use Software Center to deploy Windows over the network with System Center Configuration Manager"
ms.custom: na
ms.date: 2015-12-08
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 919e3636-53fe-4119-ad14-2d03702b391b
caps.latest.revision: 5
---
# Use Software Center to deploy Windows over the network with System Center Configuration Manager
The task sequence to install an operating system in [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] can be made available in  Software Center. You can deploy an  operating system to Software Center  in the following operating system deployment scenarios:  
  
-   [Refresh an existing computer with a new version of Windows using System Center Configuration Manager](../System Center Configuration Manager/Refresh-an-existing-computer-with-a-new-version-of-Windows-using-System-Center-Configuration-Manager.md)  
  
-   [Upgrade Windows to the latest version with System Center Configuration Manager](../System Center Configuration Manager/Upgrade-Windows-to-the-latest-version-with-System-Center-Configuration-Manager.md)  
  
 Complete the steps in one of the operating system deployment scenarios and then use the following sections to prepare for deployments that are available in Software Center.  
  
## Configure deployment settings  
 When you want the operating system deployment to be available in the Software Center, you must configure the deployment to make the operating system available to [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] clients. You can configure this on the **Deployment Settings** page of the Deploy Software Wizard or the **Deployment Settings** tab in the properties for the deployment.  For the **Make available to the following** setting, configure either **Only Configuration Manager Clients** or **Configuration Manager clients, media and PXE**. After the operating system is deployed, it will be displayed in Software Center for members of the target collection.  
  
##  <a name="BKMK_Deploy"></a> Deploy the task sequence to computers  
 Deploy the operating system to a target collection. For more information, see [Deploy a task sequence](../System Center Configuration Manager/Manage-task-sequences-to-automate-tasks-in-System-Center-Configuration-Manager.md#BKMK_DeployTS). When you deploy operating systems for Software Center, you can configure whether the deployment is required or available.  
  
-   **Required deployment**: Required deployments will make the operating system available in Software Center, but it will be automatically started at the configured assignment schedule.  
  
-   **Available deployment**: The operating system will be available in the Software Center and the user can install it on demand.  
  
## See Also  
 [Methods to deploy enterprise operating systems using System Center Configuration Manager](../System Center Configuration Manager/Methods-to-deploy-enterprise-operating-systems-using-System-Center-Configuration-Manager.md)