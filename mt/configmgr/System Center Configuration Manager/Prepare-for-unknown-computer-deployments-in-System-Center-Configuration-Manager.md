---
title: "Prepare for unknown computer deployments in System Center Configuration Manager"
ms.custom: na
ms.date: 2016-07-27
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: 
  - configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
applies_to: 
  - System Center Configuration Manager (current branch)
ms.assetid: 9e447e34-0943-49ed-b6ba-3efebf3566c1
caps.latest.revision: 10
caps.handback.revision: 0
---
# Prepare for unknown computer deployments in System Center Configuration Manager
Use the information in this topic to deploy operating systems to unknown computers in your [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] environment. An unknown computer is a computer that is not managed by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]. This means that there is no record of these computers in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database. Unknown computers include the following:  
  
-   A computer where the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client is not installed  
  
-   A computer that is not imported into [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]  
  
-   A computer that is not been discovered by [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)]  
  
 You can deploy operating systems to unknown computers with the following deployment methods:  
  
-   [Use PXE to deploy Windows over the network with System Center Configuration Manager](../System Center Configuration Manager/Use-PXE-to-deploy-Windows-over-the-network-with-System-Center-Configuration-Manager.md)  
  
-   [Use bootable media to deploy an operating system](http://technet.microsoft.com/library/mt627921\(TechNet.10\).aspx)  
  
-   [Use prestaged media to deploy an operating system](http://technet.microsoft.com/library/mt627922\(TechNet.10\).aspx)  
  
## Unknown computer deployment workflow  
 The following is the basic workflow to deploy an operating system to an unknown computer:  
  
-   Select an unknown computer object to use in the deployment. You can deploy the operating system to one of the unknown computer objects in the **All Unknown Computers** collection or you can add the objects in the **All Unknown Computer** collection to another collection. [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] provides two unknown computer objects in the **All Unknown Computers** collection. One object is for x86 computers and the other object is for x64 computers.  
  
    > [!NOTE]  
    >  The **x86 Unknown Computer** object is for computers that are only x86 capable. The **x64 Unknown Computer** object is for computers that are x86 and x64 capable. In other words, these objects describe the architecture of the destination computer. They do not describe the operating system that you want to deploy to the destination computer.  
  
-   Configure a PXE-enabled distribution point or create media to support unknown computer deployments.  
  
-   Deploy the task sequence to install the  operating system.  
  
## Unknown Computer Installation Process  
 When a computer is first started from PXE or from media, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] checks to see if a record for that computer exists in the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] database. If there is a record, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] then checks to see if there are any task sequences deployed to the record. If there is not a record, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] checks to see if there are any task sequences deployed to an unknown computer object. In either case, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] then performs one of the following actions:  
  
-   If there is an available task sequence, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] prompts the user to run the task sequence.  
  
-   If there is a required task sequence, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] automatically runs the task sequence.  
  
-   If a task sequence is not deployed for the record, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] generates an error that there is no deployed task sequence for the destination computer.  
  
 When an unknown computer is started, [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] recognizes the computer as an unprovisioned computer rather than an unknown computer. This means that the computer can now receive the task sequences that were deployed to the unknown computer object. The deployed task sequence then installs an operating system image that must include the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client.  
  
 After the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client is installed, a record for the computer is created and the computer is listed in the appropriate [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] collection. If the computer fails to install the operating system image or the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] client, an “Unknown” record for the computer is created and the computer appears in the **All Systems** collection.  
  
> [!NOTE]  
>  During the installation of the operating system image, the task sequence can retrieve collection variables but not computer variables from this computer.  
  
##  <a name="BKMK_EnablingUnknown"></a> Enabling Unknown Computer Support  
 Use the following to enable unknown computer support when you deploy an operating system by using PXE, bootable media, and prestaged media.  
  
-   **PXE**  
  
     Select the **Enable unknown computer support** check box on the **PXE** tab for a distribution point that is enabled for PXE. For more information, see [Configuring distribution points to accept PXE requests](../System Center Configuration Manager/Prepare-site-system-roles-for-operating-system-deployments-with-System-Center-Configuration-Manager.md#BKMK_PXEDistributionPoint).  
  
-   **Bootable media**  
  
     Select the **Enable unknown computer support** check box on the **Security** page of the Create Task Sequence Media Wizard. For more information, see [Configuring distribution points to accept PXE requests](../System Center Configuration Manager/Prepare-site-system-roles-for-operating-system-deployments-with-System-Center-Configuration-Manager.md#BKMK_PXEDistributionPoint) and [Use PXE to deploy Windows over the network with System Center Configuration Manager](../System Center Configuration Manager/Use-PXE-to-deploy-Windows-over-the-network-with-System-Center-Configuration-Manager.md).  
  
-   **Prestaged media**  
  
     Select the **Enable unknown computer support** check box on the **Security** page of the Create Task Sequence Media Wizard. For more information, see [Create prestaged media with System Center Configuration Manager](../System Center Configuration Manager/Create-prestaged-media-with-System-Center-Configuration-Manager.md).  
  
## See Also  
 [Prepare for operating system deployment in System Center Configuration Manager](../System Center Configuration Manager/Prepare-for-operating-system-deployment-in-System-Center-Configuration-Manager.md)