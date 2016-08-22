---
title: "Create task sequence media with System Center Configuration Manager"
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
ms.assetid: 90498b4b-6a9b-43cd-b465-1d6c9a52df1c
caps.latest.revision: 8
caps.handback.revision: 0
---
# Create task sequence media with System Center Configuration Manager
You can use media to capture an operating system image from a reference computer or to deploy an operating system to a destination computer in your [!INCLUDE[cm6long](../System Center Configuration Manager/itokens/cm6long_md.md)] environment. The media that you create can be a CD, DVD set, or a USB flash drive.  
  
 Media is used mostly to deploy operating systems on destination computers that do not have a network connection or that have a low bandwidth connection to your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] site. However, deployment media is also used to start an operating system deployment outside of an existing Windows operating system. This second use of deployment media is important for times when there is no operating system on the destination computer, the operating system is in a non-operable state, or the administrative user wants to repartition the hard disk on the destination computer.  
  
 Deployment media includes bootable media, stand-alone media, and prestaged media. The content of the deployment media varies, depending on what type of media that you use. For example, stand-alone media contains the task sequence that deploys the operating system while other types of media retrieve task sequences from the management point.  
  
> [!IMPORTANT]  
>  To create task sequence media, you must be an administrator on the computer from which you run  the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] console. If you are not an administrator, you will be prompted for administrator  credentials  when you start the Create Task Sequence Media wizard.  
  
##  <a name="BKMK_PlanCaptureMedia"></a> Capture media for operating system images  
 Capture media allows you to capture an operating system image from a reference computer. Capture media contains the boot image that starts the reference computer and the task sequence that captures the operating system image. For information about how to create capture media, see [Create capture media with System Center Configuration Manager](../System Center Configuration Manager/Create-capture-media-with-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_PlanBootableMedia"></a> Bootable media operating system deployments  
 Bootable media contains only the boot image, optional [prestart commands](http://technet.microsoft.com/library/mt629385\(TechNet.10\).aspx) and their required files, and [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] binaries. When the destination computer starts, it connects to the network and retrieves the task sequence, the operating system image, and any other required content from the network. Because the task sequence is not on the media, you can change the task sequence or content without having to recreate the media.  
  
> [!IMPORTANT]  
>  The packages on bootable media are not encrypted. The administrative user must take the appropriate security measures, such as adding a password to the media, to ensure that the package contents are secured from unauthorized users.  
  
 For information about how to create bootable media, [Create bootable media with System Center Configuration Manager](../System Center Configuration Manager/Create-bootable-media-with-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_PlanPrestagedMedia"></a> Prestaged media operating system deployments  
 Prestaged media allows you to prestage bootable media and an operating system image to a hard disk prior to the provisioning process. The prestaged media is a Windows Imaging Format (WIM) file that can be installed on a bare-metal computer by the manufacturer or at an enterprise staging center that is not connected to the [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] environment.  
  
 Prestaged media contains the boot image used to start the destination computer and the operating system image that is applied to the destination computer. You can also specify applications, packages, and driver packages to include as part of the prestaged media. The task sequence that deploys the operating system is not included in the media. When you deploy a task sequence that uses prestaged media, the client checks the local task sequence cache for valid content first, and if the content cannot be found or has been revised, the client downloads the content from the distribution point.  
  
 Prestaged media is applied to the hard drive of a new computer before the computer is sent to the end user. When the computer starts for the first time after the prestaged media has been applied, the computer starts Windows PE and connects to a management point to locate the task sequence that completes the operating system deployment process.  
  
> [!IMPORTANT]  
>  The packages on prestaged media are not encrypted. The administrative user must take the appropriate security measures, such as adding a password to the media, to ensure that the package contents are secured from unauthorized users.  
  
 For information about how to create prestaged media, see [Create prestaged media with System Center Configuration Manager](../System Center Configuration Manager/Create-prestaged-media-with-System-Center-Configuration-Manager.md).  
  
##  <a name="BKMK_PlanStandaloneMedia"></a> Stand-alone media operating system deployments  
 Stand-alone media contains everything that is required to deploy the operating system. This includes the task sequence and any other required content. Because everything that is required to deploy the operating system is stored on the stand-alone media, the disk space required for stand-alone media is significantly larger than the disk space required for other types of media.  
  
 For information about how to create stand-alone media, see [Create stand-alone media with System Center Configuration Manager](../System Center Configuration Manager/Create-stand-alone-media-with-System-Center-Configuration-Manager.md).  
  
## Media considerations when using site systems configured for HTTPS  
 When your management point and distribution points are configured to use HTTPS communication, you must create boot media and prestaged media at a primary site, not the central administration site. Also, consider the following to help you determine whether to configure the media as dynamic or site-based:  
  
-   To configure the media as dynamic media, all primary sites must have the root CA of the site from which you created the media. You can import the root CA to all primary sites in your hierarchy.  
  
-   When primary sites in your [!INCLUDE[cmshort](../System Center Configuration Manager/itokens/cmshort_md.md)] hierarchy use different root CAs, you must use site-based media at each site.  
  
## See Also  
 [Manage task sequences to automate tasks in System Center Configuration Manager](../System Center Configuration Manager/Manage-task-sequences-to-automate-tasks-in-System-Center-Configuration-Manager.md)